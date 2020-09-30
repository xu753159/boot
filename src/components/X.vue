<template>
  <div id="app">
    <div class="dynamic">
      <button
        class="dynamic-item"
        v-for="(item,index) in list"
        :key="index"
        v-on:[eventName]="handleClick(item.doSome,index)"
      >我的是动态元素--{{item.doSome}}</button>
    </div>
    <button @click="allClick">双点所有按钮失效</button>
  </div>
</template>
<script>
	export default {
	  name: "app",
	  data() {
	    return {
	      list: [
	        { doSome: "doSomg1" },
	        {  doSome: "doSomg2" },
	        { doSome: "doSomg3" },
	        { doSome: "doSomg4" },
	        {  doSome: "doSomg5" },
	        { doSome: "doSomg6" }
	      ],
	      eventName: "click",
	      newArrys: new Array(5),
	    };
	  },
	  mounted() {
	    var s = new Array(5);
	    console.log(this.newArrys);
	  },
	  methods: {
	    handleClick(i, inedx) {
	      let doSomes = i;
	      this[doSomes](inedx);
	    },
	    doSomg1(inedx) {
	      this.newArrys[inedx] = !this.newArrys[inedx];
	      if (this.newArrys[inedx]) {
	        console.log("doSomg1", this.newArrys[inedx]);
	      }
	    },
	    doSomg2(inedx) {
	      console.log("doSomg2");
	    },
	    doSomg3(inedx) {
	      console.log("doSomg3");
	    },
	    doSomg4(inedx) {
	      console.log("doSomg4");
	    },
	    doSomg5(inedx) {
	      console.log("doSomg5");
	    },
	    doSomg6(inedx) {
	      console.log("doSomg6");
	    },
	    allClick(){
	      this.eventName=='click'? this.eventName=null: this.eventName='click'
	    }
	  }
	};
</script>

