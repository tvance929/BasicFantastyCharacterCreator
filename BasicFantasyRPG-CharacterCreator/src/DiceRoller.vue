<template>
    <div>
        <b-container fluid class="onepercent" id="diceRoller">
            <b-row class="my-1">
                <b-col>
                    <b-button variant="warning" v-on:click="rollAbilityScores()">ROLL ABILITIES</b-button>
                </b-col>
                <b-col>
                    <b-button variant="info" v-on:click="standardArrayScores()">STANDARD ARRAY</b-button>
                </b-col>
            </b-row>
            <b-row class="my-1">
                <b-col>
                    <b-container fluid class="onepercent" id="diceRoller">
                        <b-row class="my-1">
                            <b-col class="border dieRoll cols-lg" draggable="true" v-on:dragstart="setDragInfo($event)" v-bind:data-value="randomrolls.one">
                                <span>{{randomrolls.one}}</span>
                            </b-col>
                            <b-col class="border dieRoll" draggable="true" v-on:dragstart="setDragInfo($event)" v-bind:data-value="randomrolls.two">
                                <span>{{randomrolls.two}}</span>
                            </b-col>
                            <b-col class="border dieRoll" draggable="true" v-on:dragstart="setDragInfo($event)" v-bind:data-value="randomrolls.three">
                                <span>{{randomrolls.three}}</span>
                            </b-col>
                        </b-row>
                        <b-row class="my-1">
                            <b-col class="border dieRoll" draggable="true" v-on:dragstart="setDragInfo($event)" v-bind:data-value="randomrolls.four">
                                <span>{{randomrolls.four}}</span>
                            </b-col>
                            <b-col class="border dieRoll" draggable="true" v-on:dragstart="setDragInfo($event)" v-bind:data-value="randomrolls.five">
                                <span>{{randomrolls.five}}</span>
                            </b-col>
                            <b-col class="border dieRoll" draggable="true" v-on:dragstart="setDragInfo($event)" v-bind:data-value="randomrolls.six">
                                <span>{{randomrolls.six}}</span>
                            </b-col>
                        </b-row>
                    </b-container>
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>
<script>
    export default {
        name: "diceRoller",
        data() {
            return {
                randomrolls: {
                    one: 0,
                    two: 0,
                    three: 0,
                    four: 0,
                    five: 0,
                    six: 0
                },
                draggingValue: 0
            };
        },
        methods: {
            rollAbilityScores: function () {
                this.randomrolls.one = this.rollDie(6, 3);
                this.randomrolls.two = this.rollDie(6, 3);
                this.randomrolls.three = this.rollDie(6, 3);
                this.randomrolls.four = this.rollDie(6, 3);
                this.randomrolls.five = this.rollDie(6, 3);
                this.randomrolls.six = this.rollDie(6, 3);
            },
            standardArrayScores: function () {
                this.randomrolls.one = 15;
                this.randomrolls.two = 14;
                this.randomrolls.three = 13;
                this.randomrolls.four = 12;
                this.randomrolls.five = 10;
                this.randomrolls.six = 8;
            },
            rollDie: function (dieSides, numberOfRolls) {
                var total = 0;
                for (var i = 0; i < numberOfRolls; i++) {
                    total += Math.floor(Math.random() * dieSides + 1);
                }
                return total;
            },
            setDragInfo: function (event) {
                window.console.log(event);
                window.console.log(event.target.dataset.value);
                event.dataTransfer.setData("text/plain", event.target.dataset.value);
                //this.draggingValue = event.target.dataset.value;

                //ev.dataTransfer.setData("text", ev.target.id);
            }
        }
    };
</script>