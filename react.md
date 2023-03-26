# **React**

## **Component**

---

+ ### **Form 1**

Este es un formulario clásico con su archivo css para los estilos.

Para actualizar el formulario usamos useState.
En react los formularios tienen la propiedad de *onSubmit* y *onReset* a las cuales les mandamos por referencia las funciones tanto para enviar como para resetear el formulario.


```javascript
  javascript

  import React, { useState } from 'react'
  import './register.css'

  const FormRegister = () => {

    const [name, setName] = useState('')
    const [email, setEmail] = useState('')
    const [password, setPassword] = useState('')
    const [repeatPasword, setRepeatPasword] = useState('')

    const onSubmit = (event) => {
      event.preventDefault()
      console.log({
        name,
        email,
        password,
        repeatPasword
      })
    }

    const onReset = () => {
      setName('')
      setEmail('')
      setPassword('')
      setRepeatPasword('')

    }

    return (
      <>
        <div className="register__container">
          <h2 className="register__title">Registro</h2>
          <form className="register__form" onSubmit={onSubmit} onReset={onReset}>
            <input
              required
              type="text"
              value={name}
              placeholder="Nombre"
              onChange={(event) => setName(event.target.value)}
            />
            <input
              required
              type="email"
              value={email}
              placeholder="Mail"
              onChange={(event) => setEmail(event.target.value)}
            />
            <input
              required
              type="password"
              value={password}
              placeholder="Contraseña"
              onChange={(event) => setPassword(event.target.value)}
            />
            <input
              required
              type="password"
              value={repeatPasword}
              placeholder="Repetir contraseña"
              onChange={(event) => setRepeatPasword(event.target.value)}
            />
            <button className="register__button" type='submit'>Registrarse</button>
            <button className="register__button"type='reset'>Limpiar</button>
          </form>
        </div>

      </>
    )
  }

  export default FormRegister

```

```css
  CSS

  .register__container{
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 50px 0;
    color: var(--text-color);
  }

  .register__form{
    width: 250px;
    display: flex;
    flex-direction: column;
  }

  .register__form input{
    margin: 15px 0;
    color: #222;
  }

  input{
    height: 35px;
    padding: 10px;
  }

  .register__title{
    color: var(--text-color);
    text-align: center;
    font-size: 2rem;
    margin-top: 20px;
  }

  .register__button{
    background-color: var(--background-color-button);
    height: 35px;
    margin: 10px;
    border-radius: 10px;
  }

```

---

+ ### **Form 2**

Otra forma de hacer lo mismo es separar el form de los botones , en este caso podriamos tener dos componetes por separado *form* *button*.
Para hacerlo agregamos un *id* al formulario y este de lo pasamos como valor de la propiedad *form* de los botones.
En este ejenplo tambien agregamos una validación para las claves.

```javascript
  javascript

  import React, { useState } from 'react'
  import './register.css'

  const FormRegister = () => {

    const [name, setName] = useState('')
    const [email, setEmail] = useState('')
    const [password, setPassword] = useState('')
    const [repeatPasword, setRepeatPasword] = useState('')

    const onSubmit = (event) => {
      event.preventDefault()
      console.log(password !== repeatPasword)
      if (password !== repeatPasword){
        console.log('Las claves no son iguales')
      }
      console.log({
        name,
        email,
        password,
        repeatPasword
      })
    }

    const onReset = () => {
      setName('')
      setEmail('')
      setPassword('')
      setRepeatPasword('')

    }

    return (
      <>
        <div className="register__container">

          <h2 className="register__title">Registro</h2>

          <form
            className="register__form"
            onSubmit={onSubmit}
            onReset={onReset}
            id='registerForm'
          >
            <input
              required
              type="text"
              value={name}
              placeholder="Nombre"
              onChange={(event) => setName(event.target.value)}
            />
            <input
              required
              type="email"
              value={email}
              placeholder="Mail"
              onChange={(event) => setEmail(event.target.value)}
            />
            <input
              required
              type="password"
              value={password}
              placeholder="Contraseña"
              onChange={(event) => setPassword(event.target.value)}
            />
            <input
              required
              type="password"
              value={repeatPasword}
              placeholder="Repetir contraseña"
              onChange={(event) => setRepeatPasword(event.target.value)}
            />
          </form>

          <button
            className="register__button"
            type='submit'
            form='registerForm'
          >Registrarse</button>
          <button
            className="register__button"
            type='reset'
            form='registerForm'
          >Limpiar</button>

        </div>

      </>
    )
  }

  export default FormRegister

```

---

+ ### **Form 3**

Ahora vamos a refactorizar lo que venimos haciendo hasta ahora.

Vamos a usar un solo state, al cual le vamos a pasar como valor inicial un objeto con todas los valores de *value* vacios.

A la función de callback de *setRegisterData* la ponemos entre parentesis porque lo que nos devulve es un objeto. Con el spread operator lo que hacemos es iterar el estado previo y le agregamos el estado alctual. Tambien usamos el spread operator para resetear el formulario.

```javascript
  javascript

  import React, { useState } from 'react'
  import './register.css'

  const FormRegister = () => {

    const [registerData, setRegisterData] = useState({
      name: '',
      email: '',
      password: '',
      repeatPasword: ''
    })

    const { name, email, password, repeatPasword } = registerData

      const onReset = () => {
        setRegisterData((prevState) => ({
          ...prevState,
          name: '',
          email: '',
          password: '',
          repeatPasword: ''
  
        }))
      }
    
    const onSubmit = (event) => {
      event.preventDefault()
      if (password !== repeatPasword) {
        console.log('Las claves no son iguales')
        return
      }
      console.log('Registro exitoso')
      onReset()
    }

    const onChange = (event) => {
      setRegisterData((prevState) => ({
        ...prevState,
        [event.target.name]: event.target.value,
      }))
    }

    return (
      <>
        <div className='register__container'>

          <h2 className='register__title'>Registro</h2>

          <form
            className='register__form'
            onSubmit={onSubmit}
            onReset={onReset}
            id='registerForm'
          >
            <input
              required
              type='text'
              value={name}
              placeholder='Nombre'
              name='name'
              onChange={onChange}
            />
            <input
              required
              type='email'
              value={email}
              placeholder='Mail'
              name='email'
              onChange={onChange}
            />
            <input
              required
              type='password'
              value={password}
              placeholder='Contraseña'
              name='password'
              onChange={onChange}
            />
            <input
              required
              type='password'
              value={repeatPasword}
              placeholder='Repetir contraseña'
              name='repeatPasword'
              onChange={onChange}
            />
          </form>

          <button
            className='register__button'
            type='submit'
            form='registerForm'
          >Registrarse</button>
          <button
            className='register__button'
            type='reset'
            form='registerForm'
          >Limpiar</button>

        </div>

      </>
    )
  }

  export default FormRegister

```
