<template>
  <h1 class="app-title">Ticket Booking APP</h1>
  <div class="ticket-app">
      <div class="ticket-app-top">
          <div class="seat-states">
            <div class="seat-state" v-for="(value,key) in seatStates" :key="key">
                <div class="seat-state-color" :style="{backgroundColor:value.color}"></div>
                <div class="seat-state-text">{{ value.text }}</div>
            </div>
          </div>
      </div>
      <div class="ticket-app-bottom">
        <div class="tikcet-app-left">
              <div class="bus">
                  <div class="bus-top">
                      <div class="bus-door">Door</div>
                      <div class="bus-driver">Driver</div>
                  </div>
                  <div class="seats">
                      <div class="seat" :class="{
                          'seat-booked': seat.type === 'booked',
                          'seat-sold': seat.type === 'sold',
                          'seat-selected': seat.type === 'selected' 
                          }" 
                          v-for="(seat,i) in seats" :key="seat.name"
                          @click="handleSeat(i)"
                          >
                          {{ seat.name }}
                          </div>
                  </div>
              </div>
        </div>
        <div class="ticket-app-right"></div>

      </div>
  </div>
</template>

<script>
export default {
    name: "Part19",
    data(){
        return {
            seatStates:{
                sold:{
                    text: "Sold",
                    color: "#ff0000"
                },
                available:{
                    text: "Available",
                    color: "#fff"
                },
                booked:{
                    text: "Booked",
                    color: "gray"
                },
                selected: {
                    text: "Selected",
                    color: "#00ff00"
                }
            },
            seats:[
                {
                    name: "A1",
                    type: "booked",
                    price: 500,
                },
                {
                    name: "A2",
                    type: "available",
                    price: 500,
                },
                {
                    name: "A3",
                    type: "available",
                    price: 500,
                },
                {
                    name: "A4",
                    type: "sold",
                    price: 500,
                },
                {
                    name: "B1",
                    type: "booked",
                    price: 500,
                },
                {
                    name: "B2",
                    type: "available",
                    price: 500,
                },
                {
                    name: "B3",
                    type: "available",
                    price: 400,
                },
                {
                    name: "B4",
                    type: "sold",
                    price: 400,
                },
                {
                    name: "C1",
                    type: "booked",
                    price: 500,
                },
                {
                    name: "C2",
                    type: "available",
                    price: 500,
                },
                {
                    name: "C3",
                    type: "available",
                    price: 250,
                },
                {
                    name: "C4",
                    type: "sold",
                    price: 250,
                },
                {
                    name: "D1",
                    type: "booked",
                    price: 500,
                },
                {
                    name: "D2",
                    type: "available",
                    price: 500,
                },
                {
                    name: "D3",
                    type: "available",
                    price: 500,
                },
                {
                    name: "D4",
                    type: "sold",
                    price: 500,
                },
                {
                    name: "E1",
                    type: "booked",
                    price: 500,
                },
                {
                    name: "E2",
                    type: "available",
                    price: 500,
                },
                {
                    name: "E3",
                    type: "available",
                    price: 500,
                },
                {
                    name: "E4",
                    type: "sold",
                    price: 500,
                },
                {
                    name: "F1",
                    type: "booked",
                    price: 500,
                },
                {
                    name: "F2",
                    type: "available",
                    price: 500,
                },
                {
                    name: "F3",
                    type: "available",
                    price: 500,
                },
                {
                    name: "F4",
                    type: "sold",
                    price: 500,
                },
            ]
        }
    },
    computed: {

    },
    methods: {
        handleSeat(i){
            let seatClicked = this.seats[i]
            if(seatClicked.type === "sold" || seatClicked.type === "booked"){
                alert("You are not allowed for selecting this seat");
                return ;
            }
            seatClicked.type = seatClicked.type === "selected" ? "available":"selected"
            console.log(seatClicked)
        }
    }
}
</script>

<style scoped>
.app-title{
    text-align: center;
}
.ticket-app{
    width: 500px;
    max-width: 100%;
    min-height: 300px;
    margin: 22px auto;
    padding: 11px;
    position: relative;
    border-radius: 5px;
    box-shadow: 0 0 3px 2px #dedede;
}
.ticket-app-top{
    display: flex;
}
.ticket-app-bottom{
    display: flex;
    margin-bottom: 11px;
}
.ticket-app-left{
    width: 172px;
}
.ticket-app-right{
    flex: 1;
    padding-left: 22px;
}
.bus{
    border: 1px solid gray;
    padding: 5px;
}
.bus-top{
    display:flex;
    justify-content: space-between;
}
.bus-door{
    width: 66px;
    border: 1px solid gray;
    padding: 3px;
    display: flex;
    justify-content: center;
    align-items: center;
}
.bus-driver{
    width: 66px;
    border: 1px solid gray;
    padding: 3px;
    display: flex;
    justify-content: center;
    align-items: center;
}
.seat-states{
    display:flex;
    flex-wrap: wrap;
}
.seat-state{
    margin: 3px;
    min-height: 5px;
    min-width: 33px;
    margin-right: 22px;
    display: flex;
}
.seat-state-color{
    width: 28px;
    border: 1px solid gray;
}
.seat-state-text{
    display: flex;
    align-items: center;
    justify-content: center;
    line-height: 1.4;
    margin-left: 4px;
}
.seats{
    display: flex;
    flex-wrap: wrap;
    margin-top: 11px;
}
.seat{
    margin: 4px;
    border: 1px solid gray;
    padding: 3px;
    min-height: 11px;
    cursor: pointer;
    font-size: 15px;
    width: 28px;
}
.seat-sold{
    background-color: red;
    color: #fff;
}
.seat-booked{
    background-color: gray;
}
.seat-selected{
    background-color: #00ff00;
}
.seat:hover{
    font-weight: bold;
}
.seat:nth-child(4n -2){
    margin-right: 12px;
}
.seat:nth-child(4n -1){
    margin-left: 12px;
}
</style>