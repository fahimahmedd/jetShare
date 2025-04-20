<script setup>
import { reactive } from 'vue';

const seats = reactive([
  { id: 1, class: 'seat-1', selected: false, booked: false },
  { id: 2, class: 'seat-2', selected: false, booked: false },
  { id: 3, class: 'seat-3', selected: false, booked: true },
  { id: 4, class: 'seat-4', selected: false, booked: false },
  { id: 5, class: 'seat-5', selected: false, booked: true },
  { id: 6, class: 'seat-6', selected: false, booked: false },
  { id: 7, class: 'seat-7', selected: false, booked: false },
]);

const toggleSeat = (id) => {
  const seat = seats.find((s) => s.id === id);
  if (seat && !seat.booked) {
    seat.selected = !seat.selected;
  }
};
</script>

<template>
  <div class="seat-container d-none d-sm-flex">
    <v-btn
      v-for="seat in seats"
      :key="seat.id"
      :class="[seat.class, { selected: seat.selected, booked: seat.booked }]"
      class="seat-item"
      :disabled="seat.booked"
      @click="toggleSeat(seat.id)"
      density="compact"
      variant="tonal"
    >
    <span v-if="seat.booked" class="booked-text text-caption text-white font-weight-medium">BOKAD</span>
    </v-btn>
  </div>

  <div class="seat-mobile-container d-block d-sm-none">
    <v-btn
      v-for="seat in seats"
      :key="seat.id"
      :class="[seat.class, { selected: seat.selected, booked: seat.booked }]"
      class="seat-item"
      :disabled="seat.booked"
      @click="toggleSeat(seat.id)"
      density="compact"
      variant="tonal"
    >
    <span v-if="seat.booked" class="booked-text text-caption text-white font-weight-medium">BOKAD</span>
    </v-btn>
  </div>



  <div class="seat-overview mt-16">
     <div class="d-flex align-center ga-2">
        <span class="seat-shape booked-seat"></span>
        <span>Booked Seat</span>
     </div>
     <div class="d-flex align-center ga-2">
        <span class="seat-shape choosen-seat"></span>
        <span>Choosen Seat</span>
     </div>
  </div>
  <div class="seat-footer d-flex justify-space-between mt-16">
    <div class="d-flex ga-4 align-center">
       <div><v-img src="/public/images/seat/seat.png" height="22" width="22"></v-img></div> <span>Seating <strong>3L</strong> </span>
    </div>
    <v-btn size="x-large" density="comfortable" variant="tonal"  min-width="260" rounded>1/2</v-btn>
  </div>
</template>

<style scoped>
.seat-container {
  height: 180px;
  width: 100%;
  background-image: url('/images/seat/plane-plate.png');
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;
  position: relative;
  z-index: 1;
}

.seat-mobile-container{
  height: 600px;
  width: 100%;
  background-image: url('/images/seat/m-plan-plate.png');
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;
  position: relative;
  z-index: 1;
}
.seat-item {
  height: 40px !important;
  width: 50px;
  min-width: auto !important;
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;
  position: absolute;
}

/* Seat positioning and background */
.seat-1 { background-image: url(/public/images/seat/seat-1.png); top: 25px; left: 235px; }
.seat-2 { background-image: url(/public/images/seat/seat-2.png); top: 25px; left: 340px; }
.seat-3 { background-image: url(/public/images/seat/seat-3.png); top: 25px; left: 465px; }
.seat-4 { background-image: url(/public/images/seat/seat-4.png); top: 25px; right: 325px; }
.seat-5 { background-image: url(/public/images/seat/seat-5.png); bottom: 27px; left: 340px; }
.seat-6 { background-image: url(/public/images/seat/seat-6.png); bottom: 27px; left: 460px; }
.seat-7 { background-image: url(/public/images/seat/seat-7.png); bottom: 27px; right: 320px; }


.selected {
  background-color: #3db641f6 !important; 
  color: white;
}

/* Booked seat style */
.booked {
  background-color: #eeeeeea8; 
  pointer-events: none;
  opacity: .8;
}
.booked .booked-text{
  position: relative;
  z-index: 111;
}
.seat-overview{
  display: flex;
  align-items: center;
  gap: 60px;
}
.seat-shape{
  height: 20px;
  width: 25px;
  border-top-left-radius: 10px;
  border-top-right-radius: 5px;
  border-bottom-left-radius: 6px;
  border-bottom-right-radius: 2px;
}
.booked-seat{
  background-color: #b9b9b9;
}
.choosen-seat{
  background-color:#358b38fd ;
}


.seat-mobile-container{

}

@media (max-width: 991px){

 .seat-1 {  top: 25px; left: 235px; }
.seat-2 {  top: 25px; left: 340px; }
.seat-3 {  top: 25px; left: 465px; }
.seat-4 {  top: 25px; right: 325px; }
.seat-5 {  bottom: 27px; left: 340px; }
.seat-6 {  bottom: 27px; left: 460px; }
.seat-7 {  bottom: 27px; right: 320px; }

}
</style>
