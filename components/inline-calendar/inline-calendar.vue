<template>
  <div class="m-calendar" ref="calendar">
    <div class="m-toolbar">
      <div class="m-year-selector">
        <a class="m-prev-btn" @click="changeYear('prev')"></a>
        <span>{{showDate.year}} {{yearName}}</span>
        <a class="m-next-btn" @click="changeYear('next')"></a>
      </div>
      <div class="m-month-selector">
        <a class="m-prev-btn" @click="changeMonth('prev')"></a>
        <span>{{monthNames[showDate.month-1]}}</span>
        <a class="m-next-btn" @click="changeMonth('next')"></a>
      </div>
    </div>
    <div class="m-week-header">
      <div
        class="m-week-day"
        v-for="item in weekNames"
        :key="item"
      >
        {{item}}
      </div>
    </div>
    <div
      class="m-months-container"
      @touchstart="touchstart"
      @touchmove="touchmove"
      @touchend="touchend"
    >
      <div
        class="m-months-wrapper"
        :style="{'transform': `translate3d(${-translateX*100}%, 0, 0)`}"
      >
        <div
          class="m-months"
          v-for="(month,monthIndex) in fullDate"
          :key="monthIndex"
          :style="{
            transform: `translate3d(${(monthIndex-1+translateX + (isTouching ? touch.x : 0))*100}%, 0, 0)`,
            transitionDuration: isTouching ? '0s' : '.3s',
          }"
        >
          <div
            class="m-row"
            v-for="(week,weekIndex) in month"
            :key="weekIndex"
          >
            <div
              class="m-day"
              v-for="(day,dayIndex) in week"
              :key="dayIndex"
              @click="onDayClick(day)"
            >
              <span
                :class="{
                  'm-day-num':true,
                  'm-grey': day.isGrey,
                  'm-today': day.isToday,
                  'm-disable': day.isDisable,
                  'm-select': day.isSelect,
                  'm-during': day.isDuring
                }"
              >
                {{day.value}}
              </span>
              <!-- <slot name="day" :date="day" /> -->
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import './inlineCalendar.less';
import dayjs from './dayjs';
let touchStartPosition;
let touchEndPosition;
let timeStamp;

export default {
  name: 'inlineCalendar',
  props: {
    defaultDate: {
      type: [Date, Number, Array, String, dayjs],
    },
    disabledDate: {
      type: Array,
      default() {
        return [];
      },
    },
    minDate: {
      type: [Date, Number, Array, String, dayjs],
    },
    maxDate: {
      type: [Date, Number, Array, String, dayjs],
    },
    mode: {
      type: String,
      default: 'single',
    },
    dayClick: {
      type: Function,
      default() {
        return function() {
          return true;
        };
      },
    },
    enableTouch: {
      type: Boolean,
      default: true,
    },
    monthNames: {
      type: Array,
      default() {
        return ['一月', '二月', '三月', '四月', '五月', '六月', '七月', '八月', '九月', '十月', '十一月', '十二月'];
      },
    },
    weekNames: {
      type: Array,
      default() {
        return ['周一', '周二', '周三', '周四', '周五', '周六', '周日'];
      },
    },
    yearName: {
      type: String,
      default: '年',
    },
    restrictCurrentMonth: {
      type: Boolean,
      default: false,
    },
  },
  watch: {
    mode() {
      this.init();
    },
  },
  data() {
    return {
      fullDate: [[], [], []],
      translateX: 0,
      showDate: {
        year: undefined,
        month: undefined,
      },
      dateNow: {
        year: dayjs().year(),
        month: dayjs().month() + 1,
        date: dayjs().date(),
      },
      selectDate: [],
      touch: {
        x: 0,
        y: 0,
      },
      isTouching: false,
    };
  },
  created() {
    this.init();
  },
  methods: {
    init(date) {
      this.selectDate = [];
      let { defaultDate, mode } = this;
      if (date) {
        defaultDate = date;
      }
      let dateToShow = dayjs().startOf('month');
      if (mode === 'single' && defaultDate) {
        this.selectDate = dayjs(defaultDate).startOf('day');
        dateToShow = this.selectDate.startOf('month');
      }
      if (mode === 'multiple' && Array.isArray(defaultDate)) {
        if (defaultDate.length > 0) {
          this.selectDate = defaultDate.map((item) => dayjs(item).startOf('day'));
        }
      }
      if (mode === 'during' && Array.isArray(defaultDate)) {
        if (defaultDate.length === 2) {
          const startDate = dayjs(defaultDate[0]).startOf('day');
          const endDate = dayjs(defaultDate[1]).startOf('day');
          if (startDate.isBefore(endDate) || startDate.isSame(endDate)) {
            this.selectDate = [startDate, endDate];
          }
        }
      }
      this.showDate = {
        year: dateToShow.year(),
        month: dateToShow.month() + 1,
      };
      this.getFullDate(this.showDate);
    },
    touchstart(event) {
      if (this.enableTouch) {
        touchStartPosition = event.touches[0].clientX;
        touchEndPosition = event.touches[0].clientY;
        timeStamp = event.timeStamp;
        this.touch = {
          x: 0,
          y: 0,
        };
        this.isTouching = true;
      }
    },
    touchmove(event) {
      if (this.enableTouch) {
        this.touch = {
          x: (event.touches[0].clientX - touchStartPosition) / this.$refs.calendar.offsetWidth,
          y: (event.touches[0].clientY - touchEndPosition) / this.$refs.calendar.offsetHeight,
        };
      }
    },
    touchend(event) {
      if (this.enableTouch) {
        this.isTouching = false;
        const during = dayjs(event.timeStamp).diff(timeStamp);
        if (Math.abs(this.touch.x) > Math.abs(this.touch.y) && Math.abs(this.touch.x * this.$refs.calendar.offsetWidth) > 20) {
          if (this.touch.x > 0) {
            this.changeMonth('prev');
          } else if (this.touch.x < 0) {
            this.changeMonth('next');
          }
        } else {
          this.touch = {
            x: 0,
            y: 0,
          };
        }
      }
    },
    // 触发change事件
    emitChange() {
      this.$emit('change', this.selectDate);
    },
    // 触发切换年月事件
    emitSwitch(showDate) {
      if (this.restrictCurrentMonth) {
        this.selectDate = [];
      }
      this.$emit('switch', showDate);
    },
    // 日期点击事件
    onDayClick(day) {
      if (!this.dayClick(day.dateTime)) {
        return;
      }
      switch (this.$props.mode) {
      case 'single':
        if (!day.isSelect && !day.isDisable) {
          this.selectDate = day.dateTime;
          this.getFullDate(this.showDate);
          this.emitChange();
        }
        break;
      case 'multiple':
        if (!day.isSelect && !day.isDisable) {
          this.selectDate.push(day.dateTime);
          this.getFullDate(this.showDate);
          this.emitChange();
        } else {
          if (this.selectDate.length > 1) {
            this.selectDate = this.selectDate.filter((item) => !item.isSame(day.dateTime));
            this.getFullDate(this.showDate);
            this.emitChange();
          }
        }
        break;
      case 'during':
        if (day.isDisable) return;
        if (this.restrictCurrentMonth && day.isGrey) return;
        if (this.selectDate.length === 0) {
          this.selectDate = [day.dateTime];
        } else if (this.selectDate.length === 1) {
          this.selectDate.push(day.dateTime);
          if (this.selectDate[1].isBefore(this.selectDate[0])) {
            this.selectDate.reverse();
          }
        } else if (this.selectDate.length === 2) {
          this.selectDate = [day.dateTime];
        }
        this.getFullDate(this.showDate);
        this.emitChange();
        break;
      }
    },
    // 切换年份
    changeYear(action) {
      const date = dayjs(`${this.showDate.year}-${this.showDate.month}`);
      let computedDate;
      switch (action) {
      case 'prev':
        this.translateX += 1;
        computedDate = date.subtract(1, 'year');
        break;
      case 'next':
        this.translateX -= 1;
        computedDate = date.add(1, 'year');
        break;
      }
      this.showDate = {
        year: computedDate.year(),
        month: computedDate.month() + 1,
      };
      this.emitSwitch(this.showDate);
      this.getFullDate(this.showDate);
    },
    // 切换月份
    changeMonth(action) {
      const date = dayjs(`${this.showDate.year}-${this.showDate.month}`);
      let computedDate;
      switch (action) {
      case 'prev':
        this.translateX += 1;
        computedDate = date.subtract(1, 'month');
        break;
      case 'next':
        this.translateX -= 1;
        computedDate = date.add(1, 'month');
        break;
      }
      this.showDate = {
        year: computedDate.year(),
        month: computedDate.month() + 1,
      };
      this.emitSwitch(this.showDate);
      this.getFullDate(this.showDate);
    },
    // 暴露出去的方法：切换已选的时间
    changeDate(date) {
      if (dayjs(date).isValid() || Array.isArray(date)) {
        this.init(date);
      } else {
        console.error('Type of parameter is invalid!');
      }
    },
    // 暴露出去的方法：切换当前显示的时间
    changeDateView(date = dayjs()) {
      const changeDate = dayjs(date);
      this.showDate = {
        year: changeDate.year(),
        month: changeDate.month() + 1,
      };
      this.getFullDate(this.showDate);
    },
    getFullDate() {
      const date = dayjs(`${this.showDate.year}-${this.showDate.month}`);
      const thisDate = this.getDate(date);
      const prevDate = this.getDate(date.subtract(1, 'month'));
      const nextDate = this.getDate(date.add(1, 'month'));
      this.fullDate = [
        prevDate.fullDate,
        thisDate.fullDate,
        nextDate.fullDate,
      ];
    },
    // 当前日期是否被选中
    isSelect(date) {
      let select = false;
      switch (this.$props.mode) {
      case 'single':
        if (this.selectDate && date.isSame(this.selectDate)) {
          select = true;
        }
        break;
      case 'multiple':
        if (this.selectDate.length > 0 && this.selectDate.some((item) => date.isSame(item))) {
          select = true;
        }
        break;
      }
      return select;
    },
    // 当前时间是否在selectDate之间
    isBetting(date) {
      if (this.mode === 'during') {
        const startDate = this.selectDate[0];
        const endDate = this.selectDate[1];
        if (this.selectDate.length === 1) {
          return date.isSame(startDate);
        } else if (this.selectDate.length === 2) {
          return (date.isAfter(startDate) && date.isBefore(endDate)) || date.isSame(startDate) || date.isSame(endDate);
        }
      }
      return false;
    },
    getIsDisable(dateTime) {
      let isDisable = false;
      const disabledDate = this.disabledDate.map((item) => dayjs(item).startOf('day'));
      if (this.minDate || this.maxDate) {
        if (this.minDate) {
          const minDate = dayjs(this.minDate).startOf('day');
          isDisable = dateTime.isBefore(minDate);
        }
        if (!isDisable && this.maxDate) {
          const maxDate = dayjs(this.maxDate).endOf('day');
          isDisable = dateTime.isAfter(maxDate);
        }
      } else if (disabledDate.length > 0) {
        if (this.mode !== 'during') {
          isDisable = disabledDate.some((item) => item.isSame(dateTime));
        }
      }
      return isDisable;
    },
    getDate(thisDate) {
      let date = [];
      const prevDate = thisDate.subtract(1, 'month');
      const nextDate = thisDate.add(1, 'month');
      const firstDayOfWeek = thisDate.day() || 7;
      const dayCountOfThisMonth = thisDate.daysInMonth();
      const dayCountOfPrevMonth = prevDate.daysInMonth();
      const prevIndexOfThisMonth = firstDayOfWeek - 1;
      const NextIndexOfThisMonth = firstDayOfWeek + dayCountOfThisMonth - 2;
      const disabledDate = this.disabledDate.map((item) => dayjs(item).startOf('day'));
      for (let i = 0; i < 7 * 6; i++) {
        // 上月
        if (i < prevIndexOfThisMonth) {
          const value = dayCountOfPrevMonth - (firstDayOfWeek - i - 2);
          const dateTime = prevDate.date(value);
          date[i] = {
            value,
            dateTime,
            isGrey: true,
            isToday: dateTime.isSame(dayjs().startOf('day')),
            isSelect: this.isSelect(dateTime),
            isDisable: this.getIsDisable(dateTime),
            isDuring: this.isBetting(dateTime),
          };
        }
        // 当月
        if (
          i >= prevIndexOfThisMonth &&
          i <= NextIndexOfThisMonth
        ) {
          const value = i - firstDayOfWeek + 2;
          const dateTime = thisDate.date(value);
          date[i] = {
            value,
            dateTime,
            isGrey: false,
            isToday: dateTime.isSame(dayjs().startOf('day')),
            isSelect: this.isSelect(dateTime),
            isDisable: this.getIsDisable(dateTime),
            isDuring: this.isBetting(dateTime),
          };
        }
        // 下月
        if (i > NextIndexOfThisMonth) {
          const value = i - firstDayOfWeek - dayCountOfThisMonth + 2;
          const dateTime = nextDate.date(value);
          date[i] = {
            value,
            dateTime,
            isGrey: true,
            isToday: dateTime.isSame(dayjs().startOf('day')),
            isSelect: this.isSelect(dateTime),
            isDisable: this.getIsDisable(dateTime),
            isDuring: this.isBetting(dateTime),
          };
        }
      }
      const fullDate = [];
      for (let i = 0; i < 6; i++) {
        fullDate.push(date.slice(i * 7, (i + 1) * 7));
      }
      return {
        fullDate,
      };
    },
  },
};
</script>
<style lang="less" scoped>
.m-calendar {
  background: #fff;
  .m-toolbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: #fff;
    height: 44px;
    font-size: 17px;
    .m-month-selector,
    .m-year-selector {
      display: flex;
      align-items: center;
      justify-content: space-between;
      width: 50%;
      padding: 0 20px;
      .m-prev-btn,
      .m-next-btn {
        cursor: pointer;
        width: 20px;
        height: 20px;
        background-size: 100% 100%;
        -webkit-tap-highlight-color: transparent;
      }
      .m-prev-btn {
        background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMgAAADICAYAAACtWK6eAAAKFUlEQVR4Xu2bQXJbRRBAeyIFvMOuEmuUEyTcIDkBPgIsqZginIDkBAkFVJZwA5wTwA0wJ8CsSZWdnYQlDyVjJyEVy/P/n+6Z3/Oypad7+nW/GtkWQfgHAQhcSyDABgIQuJ4AgrAdENhCAEFYDwggCDsAgX4EeEH6ceNUIwQQpJFB02Y/AgjSjxunGiGAII0Mmjb7EUCQftw41QgBBGlk0LTZjwCC9OPm/9TTk92d2+vPYpT9EOSeiMwvmz6OUY5CkMPF2eSFfLN36hkGgniebp/eNmJ8cP51PI+PQpDdbSlilNNwKzxb/HPrO6+iIEifJXJ6Zuf5yTyuV78ECZsXI/lflHi0PJs+8CgJgiSvge/A2z+e3Lt1vv71plfjOgqb12S5mtzxJgmC+N77pO6GynFVxONLgiBJK+Q3KJccrwnF+GTx1cePvRBDEC+T7NFHdjlExNtHLQTpsVgejmjI8ZpLkC8WD2c/e+CEIB6m2LEHVTk2r4jIi+XBbL/jtaoMR5Aqx6J3KW05Lm9+vDiY3dHrwi4zgtixLl7JSI6LPhcHMxe75aKJ4ps3ggtYyoEgI1gIrviGgLUcIvLX4mB29d2tUY+CF2TU47v58gXk4If0m8dCRA0ESshx0Te/5q1h/NxhG4FSckSRV8uzydzLd7L4iOXQs1JyXKDkqyYON8pRSyXliDH+sVxN73t5Pf77tMg/NwSKyiHyKkwm9xZf7h27AYogfkZZWo7zMLl/9nDvyA/R/zrhBXEwUeTQGyKC6LE1yYwcupgRRJevanbkUMXLRyx9vHoVkEOP7duZeUFsOGetghxZcW5NhiB2rLNUQo4sGJOTIEgyqvKByGE/AwSxZ96rInL0wjb4EIIMRqifADn0GV9XAUHKsU+qjBxJmNSCEEQN7fDEyDGc4dAMCDKUoNJ55FAC2zEtgnQEZhGOHBaU02ogSBonsyjkMEOdVAhBkjDZBCGHDecuVRCkCy3FWORQhDsgNYIMgJfrKHLkIpk/D4LkZ9opI3J0wmUejCDmyN8URI6C8BNLI0giqNxhyJGbqE4+BNHhujUrchSA3rMkgvQE1/cYcvQlV+YcghhyRw5D2JlKIUgmkDelQY6bCNX53xHEYC7IYQBZqQSCKIG9SoscyoCV0yOIImDkUIRrlBpBlEAjhxJY47QIogAcORSgFkqJIJnBI0dmoIXTIUjGASBHRpiVpEKQTINAjkwgK0uDIBkGghwZIFaaAkEGDgY5BgKs/DiCDBgQcgyAN5KjCNJzUMjRE9zIjiFIj4EhRw9oIz2CIB0HhxwdgY08HEE6DBA5OsByEoogiYNEjkRQzsIQJGGgyJEAyWkIgtwwWORwuvmJbSHIFlDIkbhFjsMQ5JrhIofjre/QGoK8BxZydNgg56EI8s6AkcP5xndsD0HeAoYcHbengXAEuRwycjSw7T1aRBARQY4em9PIkeYFQY5GNr1nm00Lghw9t6ahY80KghwNbfmAVpsUBDkGbExjR5sTBDka2/CB7TYlCHIM3JYGjzcjCHI0uN0ZWm5CEOTIsCmNpnAvCHI0utmZ2nYtCHJk2pKG07gVBDka3uqMrbsUBDkybkjjqdwJsvP8ZB5X699DkF3r2UaRV+dhcv/s4d6RdW3q6RDwJcjTk90Pb69+DRLu6eC6PityWBO3qedKkJ3v/34sIXxrg+5NFeSwJm5Xz48gm9djuv7T+qMVctgta4lKbgTZ+fHl5xLlJ0uIyGFJu0wtN4J8+MPLwyDymRVG5LAiXbaOG0F2fnj5p4jMLXAihwXlOmp4EiRaIEUOC8r11ECQjrOIUU7Pb00e8LeOjuBGGu5JkGMR+cRiDkhiQbmOGm4EMf8hnZekjg1WvoUbQYr8mhdJlNezfHo3gsjF10zWx0HkI0usfNyypG1fy48gIlLsqya8JPaba1TRlSAXr8h09VsI4a4Rv9dleEmsidvU8yXI5hXZfN19vT6y/qi1GReS2CytZRV3gmzgXfwPU3H9G5JYrpLPWi4FQRKfy1qiK7eCIEmJdfJX07UgSOJvYa07ci8IklivlK96TQiCJL6W1rKbZgRBEsu18lOrKUGQxM/iWnXSnCBIYrVaPuo0KQiS+Fheiy6aFQRJLNZr/DWaFgRJxr/A2h00LwiSaK/YuPMjyOX8+ILjuBdZ6/YI8hZZJNFas/HmRZB3Zock411mjZsjyHuoIonGqo0zJ4JcMzckGedC5741gmwhiiS51218+RDkhpkhyfiWOueNESSBJpIkQHIagiCJg0WSRFDOwhCkw0CRpAMsJ6EI0nGQSNIR2MjDEaTHAJGkB7SRHkGQnoNDkp7gRnYMQQYMDEkGwBvJUQQZOCgkGQiw8uMIkmFASJIBYqUpECTTYJAkE8jK0iBIxoEgSUaYlaRCkMyDQJLMQAunQxCFASCJAtRCKRFECTySKIE1TosgisCRRBGuUWoEUQaNJMqAldMjiDLgTXokMYCsVAJBlMC+mxZJjEBnLoMgmYFuS4ckhrAzlUKQTCBT0yBJKqk64hCkwByQpAD0niURpCe4oceQZChBm/MIYsP5vVWQpCD8xNIIkghKKwxJtMjmyYsgeTgOyoIkg/CpHkYQVbzpyZEknZVlJIJY0r6hFpJUNIzLqyBIZTNBkroGgiB1zePiNkhSz1AQpJ5Z/O8mSFLHYBCkjjnwd5JK54AglQ7m6lq8JGUHhCBl+SdVR5IkTCpBCKKCNX9SJMnPNCUjgqRQqiQGSewHgSD2zAdVRJJB+DofRpDOyMofQBK7GSCIHeuslZAkK85rkyGIDWeVKkiigvV/SRFEn7FqBSRRxSsIosvXJDuS6GFGED22ppmRRAc3guhwLZK1tCRhOvl08eXecZHmlYoiiBLYUmmLSiLxaHk2fSDf7J2W6j93XQTJTbSCfCUlkRifLL76+HEFGLJcAUGyYKwvSSlJYpTT5Wpyx8srgiD17Xa2G5WSRIJ8sXg4+zlbIwUTIUhB+BalS0gSRV4sD2b7Fv1p10AQbcIV5C8gyfHiYHangtYHXwFBBiMcRwJrSRYHMxe75aKJcaxo+VtaSoIg5efNDXoQMJLkr8XBbN7jetUd4QWpbiT6F9KWhB/S9WdIBWUCqpLwa17l6ZHehICGJFHk1fJsMucPhSYjpIg2geyS8FUT7ZGR35pALklijH8sV9P7Xl6PzRz4Id16GyutN1QSbx+trsaEIJUubIlr7Tw/mcfV6jCEcLdLfY8vB4J02YCWYp+e7O5MV49iCI+CyEfbWt+8GiHGZ4vV9Jmnj1Vv98wL0tLyd+l1I8oH6/0YZV9inF+9KpvXQkI4DkEOF/9MDr2KwQvSZVmIbZYAL0izo6fxFAIIkkKJmGYJIEizo6fxFAIIkkKJmGYJIEizo6fxFAIIkkKJmGYJIEizo6fxFAIIkkKJmGYJIEizo6fxFAIIkkKJmGYJ/As1XBIyICoY8QAAAABJRU5ErkJggg==);
      }
      .m-next-btn {
        background-image: url(data:image/png;base64,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);
      }
    }
  }
  .m-week-header {
    position: relative;
    display: flex;
    box-sizing: border-box;
    font-size: 11px;
    background: #fff;
    .m-week-day {
      flex: 1;
      text-align: center;
      line-height: 18px;
    }
  }
  .m-months-container {
    position: relative;
    box-sizing: border-box;
    height: 240px;
    overflow: hidden;
    .m-months-wrapper {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      .m-months {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        will-change: transform;
        .m-row {
          position: relative;
          display: flex;
          height: 40px;
          &::before {
            content: '';
            position: absolute;
            // background-color: #ccc;
            display: block;
            right: 0;
            bottom: 0;
            left: 0;
            height: 1px;
            width: 100%;
            transform-origin: 50% 0;
          }
          .m-day {
            position: relative;
            line-height: 40px;
            font-size: 14px;
            width: calc(100% / 7);
            text-align: center;
            cursor: pointer;
            -webkit-tap-highlight-color: transparent;
            .m-day-num {
              width: 30px;
              height: 30px;
              line-height: 30px;
              display: inline-block;
              border-radius: 100%;
            }
            .m-grey {
              color: #b8b8b8;
            }
            .m-today {
              background: #FFE4E1;
            }
            .m-disable {
              color: #b8b8b8;
              text-decoration: line-through;
            }
            .m-select {
              background: #FF6363;
              color: #fff;
            }
            .m-during{
              background: #FF6363;
              color: #fff;
              width: 100%;
              height: 100%;
              line-height: 40px;
              border-radius: initial;
            }
          }
        }
      }
    }
  }
}
</style>