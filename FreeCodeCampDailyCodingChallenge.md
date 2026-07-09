
# Circular Prime (Jan 9 25)

Given an integer, determine if it is a circular prime.

A circular prime is an integer where all rotations of its digits are themselves prime.

For example, `197` is a circular prime because all rotations of its digits: `197`, `971`, and `719`, are prime numbers.

My answer:
```js
function isCircularPrime(n) {
  const arr = n.toString().split('')
  const rotated = arr
    .map((_, i) => {
    const rot = arr.slice(i)
      .concat(arr.slice(0, i))
    return +(rot.join(''))
    })

  
  for(let num of rotated){
    if(!isPrime(num)) return false
  }
  
  return true;
}

  
function isPrime(n){
  if(n <= 2) return false
  if(n%2===0) return false
  const limit = Math.floor(Math.sqrt(n))
  for(let i = 3; i<limit;i+2){
    if(n % i === 0) return false
  }

  return true
}

//num -> str -> arr
//loop arr.length times
//create new num
//run thru primeCheck helper function
//if not prime, return false
//end loop -> return true
```

# lowercase words (July 6, 2026)

Given a string, return only the words that are entirely lowercase, in their original order and with a space between each word.

## Tests:

- Waiting: 1. `getLowercaseWords("hello GOOD world")` should return `"hello world"`.
    
- Waiting: 2. `getLowercaseWords("these are all lowercase")` should return `"these are all lowercase"`.
    
- Waiting: 3. `getLowercaseWords("less is NoT more")` should return `"less is more"`.
    
- Waiting: 4. `getLowercaseWords("DonT eat pizza every OTHER day")` should return `"eat pizza every day"`.
    
- Waiting: 5. `getLowercaseWords("the Super quick AND snEaky brown fox Leapt anD jumped over aNd AROUND the lazy SloW dog")` should return `"the quick brown fox jumped over the lazy dog"`.

My answer:
```js
function getLowercaseWords(str) {
  return str.split(' ')
    .filter(word => word === word.toLowerCase())
    .join(' ');
}
```