# Day 2: Components & API Basics

Pre-requisite:
1. Create a folder in Desktop or any location
2. Go to Visual Studio, open the folder
3. Make virtual environment (to install packages) and activate it
- Go to Visual Studio Code
- Open the Terminal ( CTRL + SHIFT + ` )

- 
Run:
```bash
python -m venv venv
```
```bash
# To activate
venv\Scripts\activate
```

---
## Let's Start!

### 1. Create a Django Project, name it as `backend`

Syntax:
```bash
django-admin startproject <project_name>
```
**Run:**
```bash
django-admin startproject backend
```

![image](https://github.com/user-attachments/assets/3c4de6c6-428d-4b02-a1ea-9ebb06d1cce9)


![image](https://github.com/user-attachments/assets/6310d97a-f2cf-47f9-9b37-7896bb1cd61a)


## 2. Install Django and Django REST Framework
```bash
pip install django djangorestframework
```


## 3. Create an app named `contact` 
```bash
django-admin startapp contact


```


## 4. Add to INSTALLED_APPS:
```python
'rest_framework',
'contact',  # your app
```


## 4. Modify `models.py` of the `contact` app
```python
# contact/models.py
from django.db import models

class ContactMessage(models.Model):
    name = models.CharField(max_length=100)
    email = models.EmailField()
    message = models.TextField()

```

Then, run the following code:
```python
python manage.py makemigrations
```


```python
python manage.py migrate
```




## 5. Create a file named `serializers.py` of the `contact` app

```python
# contact/views.py
# contact/serializers.py
from rest_framework import serializers
from .models import ContactMessage

class ContactMessageSerializer(serializers.ModelSerializer):
    class Meta:
        model = ContactMessage
        fields = '__all__'

```


## 6. Modify `views.py` of the `contact` app

```python
# contact/views.py
from rest_framework import generics
from .models import ContactMessage
from .serializers import ContactMessageSerializer

class ContactMessageCreate(generics.CreateAPIView):
    queryset = ContactMessage.objects.all()
    serializer_class = ContactMessageSerializer

```


## 7. Create a file named `urls.py` of the `contact` app
```python
# contact/urls.py
from django.urls import path
from .views import ContactMessageCreate

urlpatterns = [
    path('contact/', ContactMessageCreate.as_view(), name='contact-create'),
]

```


## 8. Include it in `backend/urls.py`
```python
from django.urls import path, include

urlpatterns = [
    path('api/', include('contact.urls')),
]
```




---

### 2. Create a React Project, name it as `frontend`

**1. Setting Up a React Project with Vite**


Run the following command:

```bash
npm create vite@latest frontend --template react
```

![image](https://github.com/user-attachments/assets/ee75cca2-db8d-4056-8156-2b1602ab8442)


Run the following command:
```bash
cd frontend
```

![image](https://github.com/user-attachments/assets/971aa1a4-ec27-43be-8c00-51237f3254f8)



Run the following command:
```bash
npm install
```

![image](https://github.com/user-attachments/assets/58db8292-ab3b-45c3-bb96-4ca92938cb39)
<p align="center">The image shows that we have successfully installed react</p>


**Visit `http://localhost:5173` to see the project running.**


Run the following command:
```bash
npm run dev
```



---
**2. Install Tailwind CSS**
```bash
npm install -D tailwindcss @tailwindcss/vite
```


```bash
# Configure Vite to Use Tailwind CSS:
Edit `vite.config.ts` (or vite.config.js if using JavaScript) file and add the Tailwind CSS plugin:
// vite.config.ts
import { defineConfig } from 'vite'
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [tailwindcss()],
})

# Import Tailwind CSS in CSS File:
/* src/style.css */
@import 'tailwindcss';
```

**3. Create `components` folder inside `src`**



**4. Create a file named `Navbar.js` inside `components`**
```javascript
// components/Navbar.js
import React from "react";

const Navbar = () => (
  <nav>
    <h1>RivanCyber</h1>
    <ul>
      <li>Home</li>
      <li>About</li>
      <li>Services</li>
      <li>Courses</li>
      <li>Reviews</li>
      <li>Contact</li>
    </ul>
  </nav>
);

export default Navbar;
```


Then use it in `App.js`:
```javascript
import React from 'react';
import Navbar from './components/Navbar';

function App() {
  return (
    <>
      <Navbar />
      {/* other components */}
    </>
  );
}

export default App;
```



**5. Create a file named `ContactForm.js` inside `components`**
```javascript
// components/ContactForm.js
import { useState } from 'react';
import axios from 'axios';

function ContactForm() {
  const [form, setForm] = useState({ name: '', email: '', message: '' });

  const handleSubmit = async (e) => {
    e.preventDefault();
    await axios.post('http://localhost:8000/api/contact/', form);
    alert('Message sent!');
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" placeholder="Your Name" value={form.name} onChange={e => setForm({...form, name: e.target.value})} />
      <input type="email" placeholder="email@company.com" value={form.email} onChange={e => setForm({...form, email: e.target.value})} />
      <textarea placeholder="Tell us more..." value={form.message} onChange={e => setForm({...form, message: e.target.value})}></textarea>
      <button type="submit">Let's get started</button>
    </form>
  );
}

export default ContactForm;
```


