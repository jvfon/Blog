# Pricing Cards Procedure

### Original html
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pricing</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;700;900&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="styles.css">
</head>

<body>
  <h1>pricing</h1>
  <p class="subhead">plans that work for everyone</p>

  <div class="plans">
    <div class="plan">
      <h2 class="plan__title">basic</h2>
      <p class="plan__price">
        $4.99<span>/month</span>
      </p>
      <p class="plan__description">Eleifend cursus volutpat risus convallis nam sed quam sollicitudin eget leo at erat
        cursus justo</p>
      <a href="#" class="plan__button">Join Now</a>
    </div>

    <div class="plan">
      <h2 class="plan__title">super</h2>
      <p class="plan__price">
        $19.99<span>/month</span>
      </p>
      <p class="plan__description">Eleifend cursus volutpat risus convallis nam sed quam sollicitudin eget leo at erat
        cursus justo</p>
      <a href="#" class="plan__button">Join Now</a>
    </div>
    <div class="plan">
      <h2 class="plan__title">Enterprise</h2>
      <p class="plan__price">
        $49.99<span>/month</span>
      </p>
      <p class="plan__description">Eleifend cursus volutpat risus convallis nam sed quam sollicitudin eget leo at erat
        cursus justo</p>
      <a href="#" class="plan__button">Join Now</a>
    </div>
  </div>
</body>

</html>
```

### Original CSS
```css
body {
  font-family: "Roboto", sans-serif;
  text-align: center;
}

h1 {
  font-size: 2.5rem;
  text-transform: uppercase;
  color: #00a1ab;
  font-weight: 900;
  margin-top: 3em;
  margin-bottom: 0;
}

.subhead {
  font-size: 1.3125rem;
  margin-top: 0;
}

.plans {
  display: flex;
  justify-content: center;
}

.plan {
  color: #fff;
  background: linear-gradient(-45deg, #00a1ab, #3741a0);
  width: 200px;
  padding: 2em;
  border-radius: 1em;
  margin: 0 0.5em;
}

.plan__title {
  text-transform: uppercase;
  margin: 0 0 1em;
}

.plan__price {
  font-size: 3rem;
  font-weight: 900;
  margin: 0;
}

.plan__price span {
  display: block;
  font-size: 1.5625rem;
  font-weight: 300;
}

.plan__description {
  margin: 2em 0;
  line-height: 1.5;
}

.plan__button {
  background: white;
  color: #4e4e4e;
  text-decoration: none;
  padding: 0.5em 0.75em;
  border-radius: 0.25em;
  text-transform: uppercase;
  font-weight: 700;
}
```  

### Goal
Change the HTML and CSS so the first and third pricing cards appear plain and the middle card is highlighted in blue.  

### Procedure
