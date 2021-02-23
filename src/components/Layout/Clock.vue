<template>
  <div>
      <h1 class="clock" name="time" >{{name}}</h1>
  </div>
</template>

<script>
export default {   
    name: 'Clock',
    data() {
        return {
             name: '',
        }
    },
    methods: {
        getTime() {
            var time = new Date();
            var hour = time.getHours();
            var minutes = time.getMinutes();
            return {
                name: hour+minutes
            }
        }
        
    }
}
</script>

<style scoped>

.clock {
    background: #333;
    color: #fff;
    text-align: center;
    padding: 10px;
}

</style>