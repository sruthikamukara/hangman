# hangman
# my first hangman game
import random
import time
name=raw_input("ENTER YOUR NAME:-")
print "HELLO,",name,"lets start HANGMAN"
turns=10


words=["apple","strawberry","weed","brain","love","computer"]
correct_guesses=""
word=random.choice(words)
l=len(word)
temp=l
while temp!=0:
	correct_guesses+='_'
	temp-=1	
flag=0
count=0
i=0
while turns>0:
	time.sleep(1)
	guess=raw_input("enter the guess:-")
	turns-=1
	
	if guess in word: 
		if guess in correct_guesses:
			print "character already guessed"
		
		else:
			print "correct guess"
			i=word.count(guess)
			count+=i
			while i!=0:
			
				
				lis=list(correct_guesses)
				lw=list(word)
				pos=lw.index(guess)
				lw.remove(guess)
				lw.insert(pos,'_')
				lis.pop(pos)
				word=''.join(lw)
				lis.insert(pos,guess)
				correct_guesses=''.join(lis)
				i-=1
	else:
		print "wrong guess"

	if count==len(word):
		flag=1
		break
	print " chances left:-",turns
	print "correct guesses till now-->",correct_guesses

if flag==0:
	print "you LOST!!!!!"
else:
	print "you WON!!!!!!"
	
print "THE WORD WAS:",correct_guesses
