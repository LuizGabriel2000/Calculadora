<template>
    <div class="fundo">
          <h1 class="Titulo">Calculadora</h1>
        <div class="calculator">
            <div class="display px-4">{{igual}} {{tipo}} {{display}}</div>
            <div @click="limpar()" class="numero ">C</div>
            <div @click="limparTudo()" class="numero ">CE</div>
            <div @click="conta('%')" class="numero ">%</div>
            <div @click="conta('/')"  class="numero">/</div>
            <div @click="numero('7')" class="numero">7</div>
            <div @click="numero('8')" class="numero">8</div>
            <div @click="numero('9')" class="numero">9</div>
            <div @click="conta('x')"  class="numero">x</div>
            <div @click="numero('4')" class="numero">4</div>
            <div @click="numero('5')" class="numero">5</div>
            <div @click="numero('6')" class="numero">6</div>
            <div @click="conta('-')" class="numero">-</div>
            <div @click="numero('1')" class="numero">1</div>
            <div @click="numero('2')" class="numero">2</div>
            <div @click="numero('3')" class="numero">3</div>
            <div @click="conta('+')" class="numero">+</div>
            <div @click="numero('0')" class="numero">0</div>
            <div @click="virgula()" class="numero">,</div>
            <div @click="result()" class="numero">=</div>
        </div>
     
    </div>
</template>

<script>
  export default {
    data() {
        return {
            display: '',
            igual: '',
            multi: '',
            menor: '',

            tipo: '',

            virgu: ","
            
            
        }
    },

    methods: {
        numero(num) {
            this.display += num
        },

        conta(tipo) {
            this.igual = this.display
            this.tipo = tipo
            this.display = ''
        },


        limpar() {
            this.display = ""
            this.igual = ""
            this.tipo = ""
        },

        limparTudo() {
            this.display = ""
            this.igual = ""
            this.tipo = ""
        },


         virgula() {
           this.display += ","
         },

        result() {    
            this.igual = this.igual.replace(',', '.')
            this.display = this.display.replace(',', '.')
            
            if (this.tipo == 'x')
                this.display = this.igual * this.display

            if (this.tipo == '-')
                this.display = this.igual - this.display

            
                
            if (this.tipo == '/')
                this.display = this.igual / this.display

                    
            if (this.tipo == '%')
                this.display = this.igual % this.display

                


           if (this.tipo == '+')
                this.display = (Number(this.igual) + Number(this.display))

            this.display = this.display.toString().replace('.', ',')
            this.igual = null
            this.tipo = null
        },

    },
}
</script>

<style>


.calculator {
position: fixed;
top: 15%;
left: 50%;
width: 520px;
height: 590px;
margin-top: -2em;
margin-left: -17em;
background-color: #70757a;
border-radius: 15px;
}

.display {
font-size: 35px;
color:azure;
position: absolute;
background-color: #3c404398;
width: 100%;
height: 60px;
text-align-last: end;
border-radius: 15px;

}

.numero {
color: beige;
width: 125px;
height: 100px;
display: inline-block;
font-size: 40px;
text-align: center;
margin-left: -10px;
padding-top: 60px;
cursor: pointer;
}

.Titulo {
    color: #242d2e;
    font-family: auto;
}

.fundo {
background-color: #70757aa4;
height: 100%;
}



</style>
