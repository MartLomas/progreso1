<script>
import iconArrowDown from "../assets/icon-arrow-down.svg";
import iconArrowUp from "../assets/icon-arrow-up.svg";
import iconCalendar from "../assets/icon-calendar.svg";
import iconPlanning from "../assets/icon-planning.svg";
import iconReminders from "../assets/icon-reminders.svg";
import iconTodo from "../assets/icon-todo.svg";

export default {
  data: function () {
    return {
      iconArrowDown,
      iconArrowUp,
      iconCalendar,
      iconPlanning,
      iconReminders,
      iconTodo,
      navItems: [
        { name: "Features", subItems: [
          { name: "To do list", icon: iconTodo },
          { name: "Calendar", icon: iconCalendar },
          { name: "Reminders", icon: iconReminders },
          { name: "Planing", icon: iconPlanning }
        ],
        toggleSubItem: false },
        { name: "Company", subItems: [
          { name: "History", icon: "" },
          { name: "Out Team", icon: "" },
          { name: "Blog", icon: "" }
        ],
        toggleSubItem: false },
        { name: "Careers", subItems: [], toggleSubItem: false },
        { name: "About", subItems: [], toggleSubItem: false },
      ]
    };
  },
  methods: {
    handleToggleSubItem (item) {
      if (!item.subItems.length) return;

      item.toggleSubItem = !item.toggleSubItem;
    }
  }
};
</script>

<template>
  <div class="navbar-content">
    <nav class="main-menu">
      <ul>
        <li :key="item.name" v-for="item in navItems">
          <span class="item-name" @click="this.handleToggleSubItem(item)" tabindex="0">
            {{ item.name }}
            <img v-if="item.subItems.length && !item.toggleSubItem" :src="iconArrowDown" alt="">
            <img v-else-if="item.subItems.length" :src="iconArrowUp" alt="">
          </span>

          <div v-if="item.toggleSubItem" class="sub-items-dropdown">
            <ul>
              <li class="sub-item-name" :key="subItem.name" v-for="subItem in item.subItems">
                <span tabindex="0">
                  <img v-if="subItem.icon" :src="subItem.icon" alt="">
                  {{ subItem.name }}
                </span>
              </li>
            </ul>
          </div>
        </li>
      </ul>
    </nav>

    <div class="sign-button-content">
      <button class="btn-sign-in">Login</button>
      <button class="btn-sign-out">Register</button>
    </div>
  </div>
</template>

<style>
.navbar-content {
  display: flex;
  flex-direction: column;
  padding: 0 20px;
  color: var(--medium-gray);
  font-size: .9rem;
}

.navbar-content li {
  min-height: 30px;
}

.main-menu ul {
  padding: 0;
}

.main-menu ul li span {
  cursor: pointer;
  user-select: none;
}

.main-menu ul li span:hover {
  color: var(--almost-black);
  font-weight: bold;
}

.navbar-content li {
  list-style: none;
}

.item-name img {
  margin: 0 15px;
}

.sub-items-dropdown {
  margin: 20px;
  transform-origin: left;
  animation: subMenuAnimation .3s ease;
}

.sub-items-dropdown .sub-item-name {
  min-height: 30px;
}

.sub-item-name img {
  height: 16px;
  width: 16px;
  margin: 0 7px 0 0;
}

.sign-button-content {
  display: flex;
  flex-direction: column;
}

.sign-button-content button {
  background: #fff;
  color: var(--medium-gray);
  border: none;
}

.sign-button-content button:hover {
  color: var(--almost-black);
  font-weight: bold;
}

.sign-button-content .btn-sign-out {
  border: solid 2px var(--medium-gray);
}

@keyframes subMenuAnimation {
  from {transform: scale(0);}
  to {transform: scale(1);}
}



@media (min-width: 1440px) {
  .navbar-content {
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    width: 90vw;
    height: 100px;
  }

  .main-menu ul {
    display: flex;
  }

  .main-menu ul li {
    display: flex;
    align-items: center;
    justify-content: center;
    min-width: 120px;
  }

  .item-name img {
    margin: 0 5px;
  }

  .sign-button-content {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    width: 300px;
  }

  .sub-items-dropdown {
    background: #ebe7e7;
    position: absolute;
    top: 50px;
    left: 0;
    margin: 0;
    padding: 20px;
    max-width: 200px;
    box-shadow: 0 0 20px #0000001a;
    border-radius: 10px;
  }
  .sub-items-dropdown ul {
    display: flex;
    flex-direction: column;
  }

  .sub-items-dropdown .sub-item-name span {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
}
</style>
