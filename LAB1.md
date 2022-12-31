# BASH
Lab 1

Using sed utility
1. Display the lines that contain the word “lp” in /etc/passwd file.

	>> sed -n '/lp/p' /etc/passwd
![Lab1-1](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-1.png)

2. Display /etc/passwd file except the third line.

	>> sed -n '3!p' /etc/passwd
![Lab1-2](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-2.png)

3. Display /etc/passwd file except the last line.

	>> sed -n '$!p' /etc/passwd
![Lab1-3](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-3.png)

4. Display /etc/passwd file except the lines that contain the word “lp”.

	>> sed '/lp/d' /etc/passwd
![Lab1-4](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-4.png)

5. Substitute all the words that contain “lp” with “mylp” in /etc/passwd file.

	>> sed 's/lp/mylp/' /etc/passwd 	#prints entire files
	>> sed -n 's/lp/mylp/p' /etc/passwd 	#prints only changed lines
![Lab1-5.1](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-5.1.png)
![Lab1-5.2](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-5.2.png)

Using awk utility
6. Print full name (comment) of all users in the system.

	>> awk -F : '{print $5}' /etc/passwd
![Lab1-6](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-6.png)

7. Print login, full name (comment) and home directory of all users.( Print each line preceded by a line number)

	>> awk -F : '{print $1,$5,$6}' /etc/passwd
![Lab1-7](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-7.png)

8. Print login, uid and full name (comment) of those uid is greater than 500

	>> awk -F : '{if ($3>500) print $1,$3,$5}' /etc/passwd
![Lab1-8](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-8.png)

9. Print login, uid and full name (comment) of those uid is exactly 500

	>> awk -F : '{if ($3==500) print $1,$3,$5}' /etc/passwd
![Lab1-9](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-9.png)

10. Print line from 5 to 15 from /etc/passwd

	>> awk -F : '{if (NR>=5 && NR<=15) print $0}' /etc/passwd
![Lab1-10](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-10.png)

11. Change lp to mylp

	>> awk -F: '{sub(/lp/,/mylp/$0); print $0}' /etc/passwd
		????????????????????????????????????????????????????

12. Print all information about greatest uid.

	>> awk -F: 'BEGIN{max=0} {if ($3>max) {max=$3; line=$0}} END{print line}' /etc/passwd
![Lab1-12](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-12.png)

13. Get the sum of all accounts id’s.

	>> awk -F: 'BEGIN{sum=0} {sum=sum+$3} END{print sum}' /etc/passwd
![Lab1-1](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-1.png)

Bonus
1. Get the sum of accounts id’s that has the same group.

	>> awk -F: '{a[$4]+=$3} END{for(i in a) print i":",a[i]}' /etc/passwd
![LLab1-bonus-1](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-bonus-1.png)

2. Make the following report:
User-Group Report
--------------------------
Group1 Name:
User1
User2
Group2 Name:
User3
User4

	>> 

awk -F: '{a[$4]=a[$4]"\n"$1} END{for(i in a) print i":",a[i]}' /etc/passwd	#prints group numbers, how to change to names

![LLab1-bonus-2.1](https://github.com/ragia-abdallah/BASH-Labs/blob/main/BASH/Lab1-bonus-2.1.png)





