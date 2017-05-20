# psa2reaforms
## 3. Template-driven vs. Reactive Forms
### 2 Form Building Blocks
value changed - pristine dirty  
validity - valid errors  
visited - touched untouched  

### 3 Form Directives


## 5. Validation
### 2 Setting Built-in Validation Rules
```
this.customerForm = this.fb.group({
  firstName:['',
    [Validators.required,Validators.minLength(3)]
  ],
  sendCatelog: true
})
```
### 3. Adjusting Validation Rules at Runtime
```
setNotification(notifyVia:string): void{
  const phoneControl = this.customerForm.get('phone');
  if(notifyVia === 'text'){
    phoneControl.setValidators(Validators.required);
  } else{
    phoneControl.clearValidators();
  }
  phoneControl.updateValueAndValidity();
}
```

### 4 Custom Validators
```
function myCus(c:AbstractControl):{[key:string]:boolean}|null{
  if(){
  }
}
```

#### 03:10
actual:
```
import {FormGroup,FormBuilder,Validators,AbstractControl} from'@angular/forms';
function ratingRange(c:AbstractControl):{[key:string]:boolean}|null{
  if(c.value!=undefined && (isNaN(c.value)|| c.value<1||c.value>5)){
    return {'range':true}
  };
  return null;
}
```

```
ngOnInit():void{
  this.customerForm = this.fb.group({
    rating:['',ratingRange]
  })
}
```

html
```
<span class="" *ngIf="(customerForm.get('rating').touched || sustomerFrom.get('rating').dirty)&& customerForm.get('rating').errors">
```



## 9. Create, Read, Update, and Delete (CRUD) Using HTTP
### 4 Faking a Backend Server
```
npm install angular-in-memory-web-api --save
```
in package.json
```
'angular-in-memory-web-api':'npm:angular-in-memory-web-api/bundles/in-memory-web-api.umd.js'
```
