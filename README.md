# Formik

## import 
```javascript
import {  useFormik } from 'formik';
import * as Yup from 'yup';

```


## implimentation 

```javascript
   //The Initial Value The Input Will Havet
    const initialValues={
        cardNumber: '',
        cvc: '',
        nameOnCard: '',
        expiryMonth:'',
        expiryYear:''
    }
    
    //when you submit you will get all data
    const Get_AllData=(data)=>{
        console.log(data)
    }
    
    // formik function use function 
    const formik=useFormik({
        initialValues:{initialValues},
        onSubmit:Get_AllData,
        validationSchema

    })
    
    
    
   //Html File And Implimintation Section 
   
   <form onSubmit={formik.handleSubmit}>
         //{getFieldProps=====> onChange={formik.handleChange} value={formik.values.cardNumber} onBlur={formik.handleBlur} }
         <input name="cardNumber"    className="cardNumber" {... formik.getFieldProps('cardNumber')}/>
         {formik.errors.cardNumber &&formik.touched.cardNumber ? (<div className='error-section'>{formik.errors.cardNumber}</div>) : null}

         <input name="nameOnCard" type="text" placeholder="FULL NAME YOU HAVE"  className="cardName" {... formik.getFieldProps('nameOnCard')}/>
         {formik.errors.nameOnCard &&formik.touched.nameOnCard ? <div className='error-section'>{formik.errors.nameOnCard}</div> : null}
                    
   </form>
   
   
   //-----------------------------------------------------------------------usign combonants -----------------------------------------------------------------//
   ## import 
   
   ```javascript
     import { Formik, Form, Field,useFormik } from 'formik';
     import * as Yup from 'yup';
   ```
   
   //you schema style validation 
    const SignupSchema = Yup.object().shape({
     cardNumber: Yup.string()
        .label('Card number')
        .max(16)
        .required(),
      cvc: Yup.string()
        .label('CVC')
        .min(3)
        .max(4)
        .required(),
      nameOnCard: Yup.string()
        .label('Name on card')
        .required(),
      expiryMonth: Yup.string()
        .label('Expiry month')
        .min(2)
        .max(2)
        .required(),
      expiryYear: Yup.string()
        .label('Expiry year')
        .min(4)
        .max(4)
        .required(),
      });

    const initialValues={
        cardNumber: '',
        cvc: '',
        nameOnCard: '',
        expiryMonth:'',
        expiryYear:''
    }

    

    const Get_AllData=(data)=>{
        console.log(data)
    }



            <Formik
                initialValues={initialValues}
                validationSchema={SignupSchema}
                onSubmit={Get_AllData}
                >
                {({ errors, touched }) => (
                    <Form>
                          <Field name="cardNumber"  placeholder="1234 5678 9101 1213" type="number" className="cardNumber" />
                          {errors.cardNumber && touched.cardNumber ? (<div className='error-section'>{errors.cardNumber}</div>) : null}


                          <Field name="nameOnCard" type="text" placeholder="FULL NAME YOU HAVE"  className="cardName"/>
                          {errors.nameOnCard && touched.nameOnCard ? <div className='error-section'>{errors.nameOnCard}</div> : null}

                          <button type="submit" className='submit-buttom'>Submit paymant Information</button>
                    </Form>
                )}
            </Formik>




```
