// type Hire = { company: number, candidate: number }
// wheat1(companies: number[][], candidates: number[][]): Hire[]
// chaff1(companies: number[][], candidates: number[][]): Hire[]

//generateInput(n: number): number[][]
function generateInput(n){
  function randomInt(min, max) {
    return Math.floor(Math.random() * (max - min)) + min;
  }
  let arr = [];
  for(let i = 0; i < n; ++i){
    arr.push(i);
  }
  for(let i = 0; i < n; ++i){
    arr[i] = [];
  }
  for(let i = 0; i < n; ++i){
    for(let j = 0; j < n; ++j){
      let input = randomInt(0, n);
      while(arr[i].includes(input) && arr[i].length !== n){
        input = randomInt(0, n);
      }
      arr[i].push(input);
    }
  }
  return arr;
}

// oracle(f: (companies: number[][], candidates: number[][]) => Hire[]): void
function oracle(f){
  let numTests = 20; // Change this to some reasonably large value
  for (let i = 0; i < numTests; ++i) {
    let n = 6; // Change this to some reasonable size
    let companies = generateInput(n);
    let candidates = generateInput(n);
    let hires = f(companies, candidates);
   test('Hires length is correct', function() {
     assert(companies.length === hires.length);
   });
 // Write your tests here
    test('hires-company correct type', function(){
      let testVal = true;
      for(let i = 0; i < hires.length; ++i){
        if(typeof hires[i].company !== 'number'){
          testVal = false;
        }
      }
      assert(testVal);
    });
    test('hires-candidate correct type', function(){
      let testVal = true;
      for(let i = 0; i < hires.length; ++i){
        if(typeof hires[i].candidate !== 'number'){
          testVal = false;
        }
      }
      assert(testVal);
    });
    test('within elements bound-company', function(){
      let testVal = true;
      for(let i = 0; i < hires.length; ++i){
        if(hires[i].company > hires.length - 1 || hires[i].company < 0){
          testVal = false;
        }
      }
      assert(testVal);
    });
    test('within elements bound-candidate', function(){
      let testVal = true;
      for(let i = 0; i < hires.length; ++i){
        if(hires[i].candidate > hires.length - 1 || hires[i].candidate < 0){
          testVal = false;
        }
      }
      assert(testVal);
    });
    test('match stability', function(){
      let candsList = hires.map(x => x.candidate);
      let compsList = hires.map(x => compsList);
      let stabilityArr = hires.map(function(x){
      let stability = true;
      let stabililityComp = companies[x.company].indexOf(x.candidate);   
      let stabilityCand = candidates[x.candidate].indexOf(x.company);
        for(let k = 0; k < companies.length; ++k){
          let compareComps = companies[x.company].indexOf(k);
          let compareCands = candidates[k].indexOf(x.company);
            if (compareComps < stabililityComp && compareCands < stabilityCand ){
            if (compareCands < candidates[k].indexOf(hires[candsList.indexOf(k)].company)){
                stability = false;
            }
          } 
        } 
          assert(stability);
      })
 
    });

 }
} 

oracle(wheat1);
oracle(chaff1);

//candidates to companies are one to one..no company takes 2
//unique numbers (ratings)
//check every match stable
//console.log(generateInput(4));


// type Offer = { from: number, to: number, fromCo: boolean }
// type Run = { trace: Offer[], out: Hire[] }

//runOracle(f: (companies: number[][], candidates: number[][]) => Run): void
function runOracle(f){
  let numTests = 20; 
  for (let i = 0; i < numTests; ++i) {
    let n = 6; 
    let companies = generateInput(n);
    let candidates = generateInput(n);
    let run = f(companies, candidates);
    let companyOffers = [];
    let candidateOffers = [];
    for(let i = 0; i < run.trace.length; ++i){
      if(run.trace[i].fromCo){
        companyOffers.push([run.trace[i].from,run.trace[i].to]);
      }
      else{
        candidateOffers.push([run.trace[i].from,run.trace[i].to]);
        }
      }
      
    test('next preferred ', function() {
      let offers = [];
      for(let i= 0; i < n; ++i){
        offers.push([i]);
      }
      for(let i = 0; i < companyOffers.length; ++i){
        offers[companyOffers[i][0]].push(companyOffers[i][1]);
      }

      for(let i= 0; i< n; ++i){
        offers[i].shift();
      }

      for(let i = 0; i < offers.length; ++i){
        let compStr = companies[i].toString();
        let offerStr = offers[i].toString();
        assert(compStr.includes(offerStr));
      }
    });

  

     test('proposals unrepeated', function(){
        let companyOfferStr = companyOffers.map(x => x.toString());
        let candOfferStr = candidateOffers.map(x => x.toString());
        let filteredCompany = [n];
        filteredCompany = companyOfferStr.filter(x => !filteredCompany.includes(x));
        assert(filteredCompany.length === companyOfferStr.length);
        let filteredCandidate = [n];
        filteredCandidate = candOfferStr.filter(x => !filteredCandidate.includes(x));

        assert(filteredCandidate.length === candOfferStr.length);
    }); 
    
 

    //test('Any unmatched party that receives a proposal accepts unconditionally', function(){


    

  }
}

const oracleLib = require('oracle');
runOracle(oracleLib.traceWheat1);
runOracle(oracleLib.traceChaff1);
