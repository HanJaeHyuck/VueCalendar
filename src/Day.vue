<template>
  <div class="day" @click="openPopup">
    <div class="date">
      <span class="number">{{day.date.getDate()}}</span>
      <span class="month">({{day.date.getMonth() + 1}}월)</span>
    </div>
    <div class="list">
      <div
        class="item"
        v-for="(todo, idx) in day.list"
        @click.stop="openEditPopup(idx)"
      >{{todo.name}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "day",
  props: ["day"],
  data() {
    return {};
  },
  methods: {
    openPopup() {
      this.$emit("open");
    },
    openEditPopup(idx) {
      this.$emit("edit", event, idx, this.day.idx);
    }
  }
};
</script>

<style scoped>


::-webkit-scrollbar-track
{
	-webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
	background-color: #F5F5F5;
	border-radius: 10px;
}

::-webkit-scrollbar
{
	width: 10px;
	background-color: #F5F5F5;
}
::-webkit-scrollbar-thumb
{
	border-radius: 10px;
	background-image: -webkit-gradient(linear,
        left bottom,
        left top,
        color-stop(0.44, rgb(122,153,217)),
        color-stop(0.72, rgb(73,125,189)),
        color-stop(0.86, rgb(28,58,148)));
}
.day:first-child {
  color: red;
}

.day:last-child {
    color: blue;
}

.day {
  width: 100%;
  height: 145px;
  display: flex;
  justify-content: flex-start;
  flex-direction: column;
  box-shadow: 2px 2px 1px 1px #607d8b;
}

.list {
  overflow-y: auto;
}

.date {
  padding: 8px;
}

.number {
  font-size: 25px;
  font-weight: bold;
}

.month {
  font-size: 15px;
  color: #555;
}

.item {
  background-color: #3af;
  color: #fff;
  border-radius: 0.25rem;
  padding: 0.2rem 0.25rem;
  margin: 4px;
}
</style>