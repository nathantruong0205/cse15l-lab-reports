# StringServer Code
![image](https://github.com/nathantruong0205/cse15l-lab-reports/assets/108157832/638f9f52-9eef-4c89-97ab-b3d638f110cc)



# Usage
![image](https://github.com/nathantruong0205/cse15l-lab-reports/assets/108157832/f986c573-e28d-407b-b3dc-de2e74b5e8a8)

The two methods that are being called on would be `StringHandler` and `StringServer`.

The relevant argument of `StringServer` would be the port number which you would input when starting the web server.

The relevant argument/field of `StringHandler` would be the argument taken in by `handleRequest` which takes in a URL which is what is being read. 

`StringHandler` also has relevant fields which would be `totalString` and `counter`. `totalString` creates an empty string that we can eventually change and `counter` initializes as an integer of value 1, which will correspond to the first item on our list of strings. There is also the `string` value which stores the portion of the query after the "=" and `realString` which is just string but properly formatted. 

For this particular request, the value of `string` would become "Hello+good+friend" through the request of "/add-message?s=Hello good friend" which `realString` would then format to "Hello good friend". Then `totalString` would be changed to "1. Hello good friend" and eventually returned. This is a value that always changes with each request because it is related to the `counter` and `realString` values. `counter` value is also changed by imcrementing it by 1 for future requests. 

---

![image](https://github.com/nathantruong0205/cse15l-lab-reports/assets/108157832/a67bbbe5-769e-4cf2-abee-524de3acf053)

The two methods that are being called on would be `StringHandler` and `StringServer`.

The relevant argument of `StringServer` would be the port number which you would input when starting the web server.

The relevant argument/field of `StringHandler` would be the argument taken in by `handleRequest` which takes in a URL which is what is being read. 

`StringHandler` also has relevant fields which would be `totalString` and `counter`. `totalString` creates an empty string that we can eventually change and `counter` initializes as an integer of value 1, which will correspond to the first item on our list of strings. There is also the `string` value which stores the portion of the query after the "=" and `realString` which is just string but properly formatted.

For this particular request, the value of `string` would become "How+are+you+doing+today?" through the request of "/add-message?s=How are you doing today?" which `realString` would then format to "How are you doing today?". Then `totalString` would be changed to "2. How are you doing today?" and eventually returned. `counter` value is also changed by incrementing it by 1 for future requests but as you can see here it is now 2 instead of 1.



# Part 2

![image](https://github.com/nathantruong0205/cse15l-lab-reports/assets/108157832/2b6f7b5f-2ca9-4515-bbac-48088fd6be29)

![image](https://github.com/nathantruong0205/cse15l-lab-reports/assets/108157832/d7b43313-146f-453a-b822-f8a403e401d0)

![image](https://github.com/nathantruong0205/cse15l-lab-reports/assets/108157832/eb84e40f-f6ac-4bf4-a2be-9b8aaf0ca258)

![image](https://github.com/nathantruong0205/cse15l-lab-reports/assets/108157832/dfde2a25-c327-4e23-bb9a-e9d51ed3ef54)



# Part 3

Something interesting that I learned during week 2 and 3 was how we can start our own servers and store information on them as if they were websites. Activities during lab such as the SearchEngine and the lab activity of making a StringServer were very interesting for me because I had always wondered about the complexities of designing websites and such but now that I feel much more informed after getting hands on experience with it. 

