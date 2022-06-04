# Modul 8

## Transition

Animationen macht Design schöner, kann aber Performance beeinflussen.

Transition - ist eine CSS Eigenschaft für einfache Übergänge.

_transition_
```css
transition: background-color 1s ease 0.5s, padding 1s ease-out 0s;

/*background-color - Zeigt was verändert wird*/
/*1s - Zeit für die Animation*/
/*ease - Szenarium der Animation*/
/*0.5s - Zeit verzögerung, wann beginnt die Animation*/
```

_transition-duration_`
```css
/*Zeit für Animationsdauer*/
transition-duration: 1s;
```

_transition-property_
```css
/*Properties, die Animiert werden*/
transition-property: background-color, box-shadow;
```

_transition-delay_
```css
/*Verzögerung der Animation*/
transition-delay: 1s;
```

_transition-timing-function: ease-in-out_
```css
/*Wie die Animation verläuft, bei mehreren properties kann man mehrere Funktionen angeben*/
transition-timing-function: ease-in-out;
```

|Funktion|Bedeutung|
|---|---|
|ease|Функция по умолчанию, переход начинается медленно, разгоняется быстро и замедляется в конце. Соответствует cubic-bezier(0.25,0.1,0.25,1).|
|linear|Переход происходит равномерно на протяжении всего времени, без колебаний в скорости. Соответствует cubic-bezier(0,0,1,1).|
|ease-in|Переход начинается медленно, а затем плавно ускоряется в конце. Соответствует cubic-bezier(0.42,0,1,1).|
|ease-out|Переход начинается быстро и плавно замедляется в конце. Соответствует cubic-bezier(0,0,0.58,1).|
|ease-in-out|Переход медленно начинается и медленно заканчивается. Соответствует cubic-bezier(0.42,0,0.58,1).|
|cubic-bezier(x1, y1, x2, y2)|Позволяет вручную установить значения от 0 до 1 для кривой ускорения. Подробнее о cubic-bezier.|
|initial|Устанавливает значение свойства в значение по умолчанию.|
|inherit|Наследует значение свойства от родительского элемента.|

![Animation](img/frpro_m8_u1_1_new.png)

## CSS animation & @keyframes

@keyframes - ermöglicht eine Animation sehr komplex zu gestalten. Hiermit kann man verschieden Werte der CSS-Props in den verschiedenen Punkten/Fasen der Animation anzugeben. 
```css
@keyframes myAnimation {
    from {
        text-shadow: 0 0 3px black;
    }
    50% {
        text-shadow: 0 0 30px black;
    }
    to {
        text-shadow: 0 0 3px black;
    }
}
```

_animation-name_ - 
```css
<div class="myAnimation"></div>

body {  
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin-top: 30px;
}
.myAnimation {
  background: lightblue;
  border-radius: 100%;
  width: 100px;
  height: 100px;
  animation: pulsing;
}
 
@keyframes pulsing {
  0% {
    transform: scale(0.5, 0.5)
  }
  50% {
    transform: scale(1.0, 1.0);
  }
  100% {
    transform: scale(0.5, 0.5);
  }
}
```

_animation-duration_ - Dauer der Animation
```css
body {  
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin-top: 30px;
}
.myAnimation {
  background: lightblue;
  border-radius: 100%;
  width: 100px;
  height: 100px;
  animation: pulsing 2s;
}
 
@keyframes pulsing {
  0% {
    transform: scale(0.5, 0.5)
  }
  50% {
    transform: scale(1.0, 1.0);
  }
  100% {
    transform: scale(0.5, 0.5);
  }
}
```

_animation-iteration-count_ - Anzahl der Wiederhollungen der Animatin
```css
body {  
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin-top: 30px;
}
.myAnimation {
  background: lightblue;
  border-radius: 100%;
  width: 100px;
  height: 100px;
  animation-iteration-count: infinite;
  animation-duration: 2s;
  animation-name: pulsing;
}
 
@keyframes pulsing {
  0% {
    transform: scale(0.5, 0.5)
  }
  50% {
    transform: scale(1.0, 1.0);
  }
  100% {
    transform: scale(0.5, 0.5);
  }
}

/*Kurzschreibweise*/
animation: pulsing 2s infinite;
```

_animation-play-state_ - Animationssteuerung _running_ und _paused_
```css
body {  
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin-top: 30px;
}
.myAnimation {
  background: lightblue;
  border-radius: 100%;
  width: 100px;
  height: 100px;
  animation-iteration-count: infinite;
  animation-duration: 2s;
  animation-name: pulsing;
}
.myAnimation:hover {
  animation-play-state: paused;
}
 
@keyframes pulsing {
  0% {
    transform: scale(0.5, 0.5)
  }
  50% {
    transform: scale(1.0, 1.0);
  }
  100% {
    transform: scale(0.5, 0.5);
  }
}
``` 

_animation-fill-mode_ - was passiert mit dem Objekt nach der Animation
|||
|---|---|
|__none__|Objekt kehrt wieder zum Ursprungszustand|
|forwards|Objekt bleibt in dem Zustand der Animation bei 100%|
|backwards|Zustand bis zur Animation|
|both|

