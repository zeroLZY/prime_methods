```python
import math
nmax = 100
#input : normal number
#output: True  for prime
#		 False for non-prime
def is_prime(number):
	if number <=1 or type(number) == type(0.0):
		return False
	for i in range(2,int(math.sqrt(number))+1):
		if number%i == 0:
			return False
	return True

#input : nmax
#output: a list of prime in range of nmax
def generator_prime_list(nmax):
	prime_list = []
	for i in range(2,nmax+1):
		if is_prime(i):
			prime_list.append(i)

	return prime_list
print 'method  zero:',generator_prime_list(nmax)

#method inspired by geekpradd: https://github.com/geekpradd/Prime-Factorise/blob/master/primefactorize.py
factors       = lambda n: [x for x in range(1,n+1) if not n%x]
geek_is_prime = lambda n: len(factors(n)) == 2
prime_list    = lambda n: list(filter(geek_is_prime, range(2,n+1)))
print 'method   one:',prime_list(nmax)

#method two
def append_prime_list(n):
	prime_list = [2,3]
	if n <=1 or type(n) == type(0.0):
		return False
	elif n == 2: return [2]
	elif n == 3: return prime_list
	else:
		for number in range(4,n+1):
			for prime_number in prime_list:
				if number%prime_number == 0:
					break

	return prime_list
print 'method   two:','sorry, I didn\'t get right ans'

#Sieve of Eratosthenes method
def Sieve_prime(n):
	no_primes   = [j for i in range(2,int(math.sqrt(n))) for j in range(i*2,n,i)]
	primes_list = [x for x in range(2,n) if x not in no_primes]
	return primes_list
print 'method three:',Sieve_prime(nmax)
```
