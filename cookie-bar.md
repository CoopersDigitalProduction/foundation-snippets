# Cookie Bar

## Usando Foundation Callout

Com o *callout* aparecerá uma notificação no rodapé da página.

### HTML
```html
<div id="cookie-notice" class="callout" data-closable="fade-out" data-animate="fade-in">
  <div class="grid-container">
    <div class="grid-x grid-margin-x">
      <div class="cell medium-8">
        <h3>Nós utilizamos Cookies</h3>
        <p>Queremos melhorar sua experiência de navegação em nosso site.</p>
        <p>Ao continuar a utilizar este site, <strong>você concorda</strong> com o uso de cookies. Para mais informações, por favor veja nossa <a href="">Declaração de Privacidade</a>.</p>
      </div>
      <div class="cell medium-offset-2 medium-2">
        <button data-close class="cookie-button">
          <span class="close-text">Fechar</span>
          <svg class="close-icon" width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M1.51743 0.266929C1.1703 -0.0889762 0.607482 -0.0889762 0.26035 0.266929C-0.0867832 0.622833 -0.0867832 1.19987 0.26035 1.55577L6.74292 8.20216L0.654706 14.4442C0.307574 14.8001 0.307573 15.3772 0.654706 15.7331C1.00184 16.089 1.56465 16.089 1.91178 15.7331L8 9.49101L14.0882 15.7331C14.4353 16.089 14.9982 16.089 15.3453 15.7331C15.6924 15.3772 15.6924 14.8001 15.3453 14.4442L9.25708 8.20216L15.7397 1.55577C16.0868 1.19987 16.0868 0.622833 15.7397 0.266929C15.3925 -0.0889762 14.8297 -0.0889762 14.4826 0.266929L8 6.91332L1.51743 0.266929Z" fill="white"/>
          </svg>
        </button>
      </div>
    </div>
  </div>
</div>
```

### CSS
```css
// cookies banner
#cookie-notice {
  background-color: #06152B;
  width: 100%;
  font-family: $body-font-family;
  color: #FFF;
  padding: 46px 0px;
  filter: drop-shadow(0px -4px 6px rgba(0, 0, 0, 0.25));
  position: fixed;
  left: 0;
  bottom: 0;
  z-index: 9999;
  overflow: hidden;
  margin-bottom: 0px;

  h3 {
    text-transform: uppercase;
    font-size: 24px;
    line-height: 30px;
    font-weight: 500;
    margin-bottom: 30px;
    letter-spacing: 0.08em;
    @include breakpoint(small only) {
      font-size: 1.2em;
    }
  }

  p {
    text-transform: uppercase;
    font-size: 1em;
    line-height: 20px;
    letter-spacing: 0.08em;
    word-wrap: break-word;
    @include breakpoint(small only) {
      font-size: 0.8em;
    }
  }

  a {
    color: #FFF;
    text-decoration: underline;
  }

  button {
    color: #FFF;
    font-family: $body-font-family;
    font-size: 16px;
    text-transform: uppercase;
    width: 100%;

    @include breakpoint(small only) {
      width: unset;
    }
  
    .close-text {
      float: right;
      display: block;
      padding-right: 40px;
      @include breakpoint(small only) {
        float: none;
        display: inline-block;
        padding: 0px;
      }
    }

    .close-icon {
      float: right;
      margin-left: 50%;
      margin-top: -17px;
      display: block;
      @include breakpoint(small only) {
        float: none;
        display: inline-block;
        margin-top: 20px;
        margin-left: 20px;
      }
    }
  
  }

}
```

### JS
```js
const showNotice = localStorage.getItem('showNotice');

if(showNotice === 'false'){
  $('#cookie-notice').hide();
}

$('.cookie-button').on('click', function() {
  $('#cookie-notice').fadeOut('slow');
  localStorage.setItem('showNotice', 'false');
});
```

