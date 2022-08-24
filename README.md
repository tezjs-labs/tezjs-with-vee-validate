#  tezJS with Vee-validate

- After making tezjs fresh project to add vee-validate  in your applicaion install it through below comand  

    ```
    npm install vee-validate 
    ```

 ### Let's take an example here to add vee-validate in tezjs project

 -  Here I added contact form under pages directory with contact.vue page
 ``` 
  pages/contact.vue
 ```

- And in that page under script tag import Form,Field and ErrorMessage component
from vue-validate
```
  import { Form, Field ,ErrorMessage } from 'vee-validate'; 
```

- Make one simple form with required **<Form>** **<Field>** and **<ErrorMessage>** tag

```
<Form class="w-full max-w-lg">
  <div class="flex flex-wrap -mx-3 mb-6">
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        First Name
      </label>
       <Field name="firstname" type="text" class="form-control appearance-none block w-full bg-gray-200 text-gray-700 border  rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white"  placeholder="Enter Your Firstname" :rules="nameValues"/>
       <ErrorMessage name="firstname" class="text-red-900"/>
     
    </div>

    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
       Last Name
      </label>
      <Field name="lastname" type="email" class="form-control appearance-none block w-full bg-gray-200 text-gray-700 border  rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white"  placeholder="Enter Your Email" :rules="nameValues"/>
       <ErrorMessage name="lastname" class="text-red-900"/>
    </div>
  </div>

  <div class="flex flex-wrap -mx-3 mb-6">
    <div class="w-full px-3">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-password">
        E-mail
      </label>
      <Field name="email" type="email" class="form-control appearance-none block w-full bg-gray-200 text-gray-700 border  rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white"  placeholder="Enter Your Email" :rules="validateEmail"/>
       <ErrorMessage name="email" class="text-red-900"/>
    </div>

  </div>
  <div class="flex flex-wrap -mx-3 mb-6">
    <div class="w-full px-3">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-password">
        Your Quesries
      </label>
      <Field name="queries" as="textarea"  class=" no-resize appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500 h-48 resize-none" id="message" :rules="nameValues"></Field>
     <ErrorMessage name="queries" class="text-red-900"/>
    </div>
  </div>
  <div class="md:flex md:items-center">
    <div class="md:w-1/6">
      <button class="shadow bg-teal-700 hover:bg-teal-600 focus:shadow-outline focus:outline-none text-white font-bold py-2 px-4 rounded" type="submit">
        Submit
      </button>
    </div>
    <div class="md:w-2/3"></div>
  </div>
</Form>

```

- Then add rules attribute  of the filed tag and add functions or rules to validate that filed

  ```
  methods: {
      onSubmit(values) {
         console.log(JSON.stringify(values, null, 2));
      },
      nameValues(value){
          if (!value || value=="" ||value==undefined) {

          return `This field is required`;
        }
        return true
      },
      validateEmail(value) {
         // if the field is empty
         if (!value || value=="" ||value==undefined) {
           return 'This field is required';
         }
         // if the field is not a valid email
         const regex = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
         if (!regex.test(value)) {
           return 'E-mail must be a valid email';
         }
         return true;
       },
       },
       head: {
       title: "contact-us",
  },
  ```

- In above code to validate for name here i made namevalues function and for email i made validateEmail function

- Make sure name in the **<ErrorMessage/>** Should be same as your related field name

- And yeah you almost done, now do required things with your submit button and then your validation will work!!