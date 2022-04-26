<template>
  <h1 class="app-title">Ticket Booking APP</h1>
  <div class="ticket-app">
      <div v-if="confirmed">
          <h3>Ticket Confirmed</h3>
          <p>Passanger Name: {{ name }}</p>
          <p>Passanger Mobile: {{ mobile }}</p>
          <table>
              <thead>
                  <tr>
                      <th>Seat</th>
                      <th>Price</th>
                  </tr>
              </thead>
              <tbody>
                  <tr v-for="seat in selectedSeat" :key="seat.name">
                      <td>{{ seat.name }}</td>
                      <td>{{ seat.price }}</td>
                  </tr>
                  <tr>
                      <td>Total Price</td>
                      <td>{{ totalCost }}</td>
                  </tr>
              </tbody>
          </table>
          <button @click="resetData">Book Agagin</button>
      </div>
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
        <div v-if="selectedSeat.length === 0">
            No Selected Seats
        </div>
        <div class="ticket-app-right" v-else>
            <div class="cart">
                <strong>Selected Seat</strong>
                <table class="selected-seats" border="1">
                    <thead>
                        <tr>
                            <th>seat</th>
                            <th>price</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="seat in selectedSeat" :key="seat.name">
                            <td>{{ seat.name }}</td>
                            <td>{{ seat.price }}</td>
                        </tr>
                        <tr v-if="appliedCoupon !== null">
                            <td>Discount</td>
                            <td>{{ appliedCoupon.discount }}</td>
                        </tr>
                        <tr>
                            <td>Total Cost</td>
                            <td>{{ totalCost }}</td>
                        </tr>
                    </tbody>
                </table>
                <p v-if="appliedCoupon === null">
                    have a coupon?
                    <input type="text" v-model="couponCode" placeholder="10 digit coupon code">
                </p>
                <p v-else>
                    Applied Coupon {{ appliedCoupon.code }}
                </p>
                <div>
                    <input type="text" v-model="name">
                    <input type="text" v-model="mobile">
                </div>
                <button @click="confirm">Confirm</button>
            </div>
        </div>

      </div>
  </div>
</template>

<script>
export default {
    name: "Part19",
    data(){
        return {
            name:"",
            mobile: "",
            confirmed: false,
            appliedCoupon: null,
            couponCode: "",
            coupons:[
                {
                    code: "100TakaOff",
                    discount: 100
                },
                {
                    code: "200TakaOff",
                    discount: 200
                }
            ],
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
        selectedSeat(){
            let st = this.seats.filter(item => item.type === 'selected');
            return st
        },
        totalCost(){
            let tc = 0;
            this.selectedSeat.forEach((seat)=>{
                tc += seat.price
            });
            if (this.appliedCoupon !== null){
                tc -= this.appliedCoupon.discount
            }
            return tc;
        }
    },
    watch:{
        couponCode(newValue){
            if (newValue.length === 10){
                let searchCoupon = this.coupons.filter((item) => item.code === newValue)
                if (searchCoupon.length === 1){
                    this.appliedCoupon = searchCoupon[0]
                    this.couponCode=''
                }else{
                    alert("coupon not valid")
                }
            }
        }
    },
    methods: {
        handleSeat(i){
            let seatClicked = this.seats[i]
            if(seatClicked.type === "sold" || seatClicked.type === "booked"){
                alert("You are not allowed for selecting this seat");
                return ;
            }
            if(this.selectedSeat.length > 2){
                alert("You can not select more than 3 seat");
                return ;
            }
            seatClicked.type = seatClicked.type === "selected" ? "available":"selected"
            console.log(seatClicked)
        },
        confirm(){
            if(!this.name || !this.mobile){
                alert("Mobile or Name is missing")
            }
            this.confirmed = true;
        },
        resetData(){
            this.confirmed=false;
            this.name='';
            this.mobile='';
            this.appliedCoupon = null;
            
            this.seats.forEach((seat)=>{
                if (seat.type === 'selected'){
                    seat.type = 'sold'
                }
            })
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
.cart{
    border:1px solid gray;
    padding: 5px;
}
</style>