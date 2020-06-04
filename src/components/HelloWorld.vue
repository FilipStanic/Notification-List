<template>
  <div class="hello">
    <ul>
      <li v-bind:class="{'seen':notification.seen}" v-for="(notification, index) in notifications" v-bind:key="index">
        <div class="">
          <span v-on:click="markAsSeen(index)" class="circle"></span>
          <span>{{ notification.title }}</span>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      notifications: [
        {
          title: "Elon Musk sent you a message",
          seen: false,
          timestamp: 1591106509
        },
        {
          title: "Mark Zuckerburg sent you a message",
          seen: false,
          timestamp: 1591106409
        },
        {
          title: "Milivoje would like to tag you in a photo",
          seen: false,
          timestamp: 1591106329
        },
        {
          title: "Radivoje liked your comment",
          seen: false,
          timestamp: 1591106209
        },
        {
          title: "FBI wants to know your location",
          seen: false,
          timestamp: 1591106100
        }
      ]
    }
  },
  methods: {
    markAsSeen: function(index) {
      this.notifications[index].seen = true;
    },
    sortNotifications: function() {
      this.notifications.sort(function(a,b) {
        return a.timestamp - b.timestamp
      })
    }
  },
  beforeMount() {
    this.sortNotifications()
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  ul {
    list-style: none;
  }

  li {
    max-width: 500px;
    text-align: left;
    margin: 0 auto;
    background: rgb(14, 110, 106);
    line-height: 50px;
    color: white;
  }

  li.seen {
    background: lightsteelblue;
  }



  span {
    vertical-align: middle;
  }

  .circle {
    height: 20px;
    width: 20px;
    border-radius: 50%;
    background: rgb(196, 34, 34);
    display: inline-block;
    margin: 0 10px;
  }

  li.seen .circle {
    background: rgb(25, 189, 25);
  }


</style>
