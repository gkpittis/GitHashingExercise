# GitHashingExercise

This project is the solution to question 1 of the 4th laboratory exercise for the Operating Systems course (049).

## Description

I have generated a unique number based on the last 4 digits of my student ID.This number is `5068`.The `hash_script` is written in the Bash shell, taking this 4-digit number as input and outputting a hash of the input using the SHA-256 hashing algorithm. The resulting hash is then saved to `hash_output.txt`.
I can run the hash_script in the following ways :
``` 
1) bash hash_script <4-digit number>
2) sh hash_script <4-digit number>
3) chmod +x hash_script   and   ./hash_script <4-digit number>
```

## hash_script Code Comments

```bash

if [ "$#" -lt 1 ]; then             #Check if at least one argument is provided
echo "Usage: $0 <4-digit-number>"   #Ιf no input argument is given then an error message is printed and the program terminates
exit 1
fi

if [ "$#" -gt 1 ]; then                               #Check if there are additional arguments
echo "Error: Additional arguments are not allowed."   #If there are additional arguments then an error message is printed                                                       
exit 1                                                #and the program teminates
fi

intnum="$1"  #Store the first argument in the variable intnum

if ! echo "$intnum" | grep -E '^[0-9]{4}$' >/dev/null; then   #Check if the argument is a 4-digit number
  echo "Error: Argument must be a 4-digit number."            #If it is not a valid 4-digit then an error message is printed 
  exit 1                                                      #and the program teminates
fi

hash=$(echo -n "$intnum" | sha256sum)   # Calculate the SHA-256 hash of the input integer

echo "hash of $intnum is : $hash" > hash_output.txt   # Output the hash along with a message to hash_output.txt

echo "$hash"   # Print the hash to the console

echo "Usage: ./hash_script <4-digit-integer>"   # Print the usage message of hash_script
```

## Uploading to GitHub
Uploading the `hash_script`, `hash_output.txt` and `README.md` files to my remote `GitHashingExercise repository` on GitHub
