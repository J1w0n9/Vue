<template>
  <main class="content">
     <div class="product-card">
          <img :src="room.image" class="room-image" />
          <h4 @click="send">{{ room.title }}</h4>
          <p>{{ room.content }}</p>
          <p>{{ room.price }}원</p>
      </div>
    </main>
</template>

<script>
export default {
  name: 'Card',    
  props:{
    room : Object,
  },
  methods : {
    send(){
      this.$emit('openModal', this.room.id);
    }
  }
}
</script>