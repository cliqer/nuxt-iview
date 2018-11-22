<template lang="pug">
  div(style="margin: 200px;")
    steps(:current='current')
        step(title='Title1', content='Content1')
        step(title='Title2', content='Content2')
        step(title='Title3', content='Content3')
        step(title='Title4', content='Content4')
    
    Button(type="primary" @click="next") Next step

    Select(v-model="model1" style="width:200px" placeholder="Select")
        Option(v-for="item in cityList" :value="item.value" :key="item.value") {{ item.label }}</Option>

</template>
<script>
export default {
  asyncData() {
    return {
      current: 0,
      cityList: [
        {
          value: "New York",
          label: "New York"
        },
        {
          value: "London",
          label: "London"
        },
        {
          value: "Sydney",
          label: "Sydney"
        },
        {
          value: "Ottawa",
          label: "Ottawa"
        },
        {
          value: "Paris",
          label: "Paris"
        },
        {
          value: "Canberra",
          label: "Canberra"
        }
      ],
      model1: ""
    };
  },
  methods: {
    next() {
      if (this.current == 3) {
        this.current = 0;
      } else {
        this.current += 1;
      }
    }
  },
  mounted: () => {
    iView: {
      steps: {
        direction: "vertical";
      }
    }
  }
};
</script>
