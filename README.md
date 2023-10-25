Live Demo:
# [Kantinenbuchungen App](https://sarah-rz.github.io/kantinenbuchungen-app/)

## HOW I CREATED THIS APP:

1. First, I started my code by creating the template of the app with HTML. And created the pages.
<br><br>
2. Then I styled and responsived the app, using Bootstrap and CSS.
<br><br>
3. I have created a local json file where the data is stored.
<br><br>
4. Now its time to fetch the data with an ajax request from the JSON file:
<br>
* First I create a new xmlhttp-request object.

   > - ``` let http = new XMLHttpRequest(); ```

    - The variable http holds now all methods and properties of the object. 

* Next I prepare the request with the open() method.

    > - ``` http.open('get', 'data.json', true); ```

    - The first argument sets the http method.
    - In the second argument we pass the file where our data lives.
    - And last the keyword true, sets the request to be async.

* Next I will send the request.

   > - ``` http.send(); ```

* Now I have to check the response. I will check the onload eventlistener.
    - Inside the function I need to check the readystate and status properties.
    - If we have a successful response, I have to parse the JSON data
    - By running the JSON parse method, a regular JavaScript Object is returned. I can now manipulate it just like any other JavaScript Object.

   ``` 
    http.onload = function() {
        if(this.readyState == 4 && this.status == 200){
            let data = JSON.parse(this.responseText);
        }    
   } 
   
   ``` 
<br>

5. Now it's time to render items from JSON using forEach() method (buttons on the left side)   

    ``` 
    data.forEach( (food) => {
        foodsEl.innerHTML += `
        <button type="button" class="btn food" onclick= "addToOrder(${food.id})">${food.name}</button>
        `;
        })
    ```    
<br>

6. Next, I tried activating buttons (on the left side) in such a way that when the button is clicked, the item's information (name, number of items, price) is displayed on the right side of the app

    - first, using this function to render the items: 
        
        > - ``` function renderOrderedItems() ```

    - second, using this function to display the items: 
        
        > - ``` function addToOrder(id) ```

    - last, we should call this function to see selected items on the screen:
        
        > - ``` updateOrder() ```    

<br>

7. After that I tried to write a function that every time the button (food on the left side) is clicked, the number of ordered food on the right side of the app is increased by one using: 

    > - ``` function changeNumberOfFoods(action, id) ```

<br>

8. It's now time to calculate the total prices of the selected items, using:

    > - ``` function renderSumPrice() ```

<br>

9. With a button that displays a pop-up window asking "Wollen Sie wirklich, dass dieser Bestellung aufgegeben wird?", if "Ja", we go to the next page (e.g.to the payment gateway), if "Nine", we stay on the page and continue, using: 

   > - ``` function openPopup() ```
    > - ``` function closePopup() ```

<br>

10. I have also created a delete button to clear all selected food on the screen, change the total price to zero, and refresh the page for new orders, using:

    > - ``` del = () => {} ```

<br>

11. Now I want when I am in certain page, the navbar link of this page is active (remains glowing). For that I wrote these methods:
    - ACTIVE NAVBAR Section (script.js)
    



        

