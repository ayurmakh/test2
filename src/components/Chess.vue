<template>
  <div class="wrapper">
    <label>{{ label }} </label>
    <input type="text" v-model="cell"><br>
    <button @click="ways">{{ btnName }}</button>
  </div>  
</template>

<script>
export default {
  data() {
    return {
        label: 'Исходное положение',
        btnName: 'Ок',
        cell: ''
      };
  },
  name: 'Chess',
  methods: {
    ways() {     
      var chars = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H'];
      var res = '';
			var x = chars.indexOf(this.cell[0]);
			var y = parseInt(this.cell[1]);
			for (let i = 1; i < 9; i++) 
				for (let j = 0; j < chars.length; j++) 
					if (
							((j == x - 2) && ((i == y - 1) || (i == y + 1))) ||
							((j == x - 1) && ((i == y - 2) || (i == y + 2))) ||
							((j == x + 1) && ((i == y - 2) || (i == y + 2))) ||
							((j == x + 2) && ((i == y - 1) || (i == y + 1)))
						)	
						res = res + chars[j] + i + ' ';
			alert(res);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .wrapper {
    margin: 0 auto;
    width: 350px;
    height: 70px;
    border: 1px solid grey;
    padding: 10px;
    text-align: center;

    label {
      font-weight: 900;
    }

    * {
      margin-top: 10px;
    }
  }
</style>