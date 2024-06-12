# Task_07_FSD60WD-E_05-06-24
Task_07_FSD60WD-E_05-06-24-Array methods
 ARRAY METHODS

Q) Solving problems using array functions on rest countries data (https://restcountries.com/v3.1/all).
a) Get all the countries from Asia continent /region using Filter method
b) Get all the countries with a population of less than 2 lakhs using Filter method
c) Print the following details name, capital, flag, using forEach method
d) Print the total population of countries using reduce method
e) Print the country that uses US dollars as currency.

//a) Get all the countries from Asia continent /region using Filter function

var request=new XMLHttpRequest();
request.open('GET','https://restcountries.eu/rest/v2/all','true');
request.send();
request.onload=function (){
    var countryData=JSON.parse(this.response);
    const asia=countryData.filter((element)=>{
        if(element.region==='Asia'){
            return element.name;
        }
    })
    console.log(asia);}
    
//b) Get all the countries with population of less than 2 lacs using Filter function

var request=new XMLHttpRequest();
request.open('GET','https://restcountries.eu/rest/v2/all','true');
request.send();
request.onload=function (){
    var countryData=JSON.parse(this.response);
    const popu=countryData.filter((element)=>{
        return element.population<200000;
    })
    console.log(popu);}

//c) Print the following details name, capital, flag using forEach function.

var request=new XMLHttpRequest();
request.open('GET','https://restcountries.eu/rest/v2/all','true');
request.send();
request.onload=function (){
    var countryData=JSON.parse(this.response);
    countryData.forEach((element)=>{
        console.log(element.name,element.capital,element.flag);
    })}

//d) Print the total population of countries using reduce function 

var request=new XMLHttpRequest();
request.open('GET','https://restcountries.eu/rest/v2/all','true');
request.send();
request.onload=function (){
    var countryData=JSON.parse(this.response);
    const population=countryData.reduce((acc,element)=>{
        return acc+element.population;
    },0)
    console.log(population);}

//e) Print the country which use US Dollars as currency.

var request = new XMLHttpRequest();
request.open('Get', 'https://restcountries.eu/rest/v2/all', true)
request.send();
request.onload = function () {
        var data = JSON.parse(this.response);
        var cur=[];
        for(i=0;i<data.length;i++){
            if(data[i].currencies[0].code==="USD")
            {
                console.log("name:",data[i].name,"==>",data[i].currencies[0].code)
            }
        }
    }
