# Dallin-G
<head>
    <meta charset="utf-8">
    <title>Well, you found a glitch.</title>
    <meta name="viewport" content="initial-scale=1, width=device-width">
    <link rel="stylesheet" type="text/css" href="https://cloud.webtype.com/css/3a8e55c6-b1f3-4659-99eb-125ae72bd084.css">
    <style>
      * {
        box-sizing: border-box;
      }

      html, body {
        margin: 0;
        padding: 0;
        font-family: "Benton Sans", Helvetica, Sans-serif;
        font-size: 16px;
        line-height: 160%;
        width: 100%;
        height: 100%;
      }

      .container {
        width: 100%;
        height: 100%;
        display: flex;
        padding: 100px;
      }

      .info {
        max-width: 370px;
        z-index: 1;
        position: relative;
      }

      h1 {
        margin: 0;
        font-size: 40px;
        line-height: 130%;
        font-weight: bold;
      }

      a {
        color: #000;
      }

      .decorative-image {
        position: absolute;
        right: 80px;
        bottom: 80px;
        width: 50vw;
        max-width: 1000px;
      }

      @media(max-width: 620px) {
        .container {
          padding: 40px;
        }

        .decorative-image {
          right: 20px;
          bottom: 20px;
          width: 80vw;
        }
      }

      .button-wrap {
        display: flex;
        flex-direction: row;
      }

      .button-wrap * + * {
        margin-left: 7px;
      }

      .button {
        border-radius: 5px;
        border: 2px solid black ;
        box-sizing: border-box;
        background-color: white;
        text-decoration: none;
        text-align: center;
        padding: 0.375em 0.5em 0.1875em;
        font-weight: 600;
        line-height: 1;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="info">
        <h1>Well, you found a glitch.</h1>
        <p>
          Did you expect to see an app here? You might need to log in to get access.
          If something went wrong, you can check out our <a href="http://glitch.com/help">Help Center</a> if you need a hand.
        </p>
        <div class="button-wrap">
          <a class="button" href="//glitch.com">Back to Glitch</a>
          
            <a id="login-button" class="button" href="https://glitch.com/authorize?requestToken=eyJhdWRpZW5jZSI6WyJ1cm46Z2xpdGNoOmNsaWVudCJdLCJpc3N1ZXIiOiJodHRwczovL29wLmdsaXRjaC5jb20iLCJoZWFkZXIiOnsidHlwIjoiSldUIn0sImVuYyI6IkExMjhDQkMtSFMyNTYiLCJhbGciOiJQQkVTMi1IUzI1NitBMTI4S1ciLCJwMmMiOjI2MDQsInAycyI6InA3aDJXMnVHaHdraWlROTRVX3haclEifQ.Q-gWQIgW6XYUy3BuJe2Ys2GeegaHrDdDAEyf9rOD4YccRt-T2aPjiQ.fgsZyldmoHPkQX44rF-OEQ.TisBpLT_Bf5wbu1lm_UgCDMimdEbjhQto5RUy-0Dku_uzh5zvamtx7bn6y2tNx1oCNIq4IPLLSNsM3ysSczJjPZ_yxfGRflosfuj0wBW4MQ.vXzLUA6o9U4icl73qSZ92g">Log in</a>
          
        </div>
      </div>
      <img src="https://cdn.glitch.com/d7f4f279-e13b-4330-8422-00b2d9211424%2FGlitch-Error-Rainbow-Mug-hires.png?v=1595481653593" class="decorative-image">
    </div>
    <script>
      function requestStorageAccess() {
        if ('requestStorageAccess' in document === false) {
          return Promise.resolve();
        }

        return document.requestStorageAccess();
      }

      function loginClicked(e) {
        if (!window.parent || window.parent === window) {
          return;
        }

        const requestToken = "eyJhdWRpZW5jZSI6WyJ1cm46Z2xpdGNoOmNsaWVudCJdLCJpc3N1ZXIiOiJodHRwczovL29wLmdsaXRjaC5jb20iLCJoZWFkZXIiOnsidHlwIjoiSldUIn0sImVuYyI6IkExMjhDQkMtSFMyNTYiLCJhbGciOiJQQkVTMi1IUzI1NitBMTI4S1ciLCJwMmMiOjI2MDQsInAycyI6InA3aDJXMnVHaHdraWlROTRVX3haclEifQ.Q-gWQIgW6XYUy3BuJe2Ys2GeegaHrDdDAEyf9rOD4YccRt-T2aPjiQ.fgsZyldmoHPkQX44rF-OEQ.TisBpLT_Bf5wbu1lm_UgCDMimdEbjhQto5RUy-0Dku_uzh5zvamtx7bn6y2tNx1oCNIq4IPLLSNsM3ysSczJjPZ_yxfGRflosfuj0wBW4MQ.vXzLUA6o9U4icl73qSZ92g" || null;

        requestStorageAccess()
          .then(() => {
            window.parent.postMessage({ type: "REQUEST_AUTH_TOKEN", requestToken }, "https://glitch.com");
          }, (e) => {
            window.alert("There was an issue logging you in.");
          });

        e.preventDefault();
      }

      window.addEventListener("message", (e) => {
        if (e.data.type === "AUTH_TOKEN") {
          const url = new URL('/.glitch/authorize', window.location.origin);
          url.searchParams.set('authorizationToken', e.data.authorizationToken);
          url.searchParams.set('location', window.location.href.substring(window.location.origin.length));
          window.location = url.toString();
        }
      }, false);

      document.getElementById('login-button').addEventListener('click', loginClicked);
    </script>
  <script type='text/javascript'  src="https://groovy-ludicrous-marimba.glitch.me/93791460bd4591916fae6788dd691570096e47a0e47061cdead407edc2363560/inject.js?id=86286ce8-454f-443d-8507-d9cacb6e5c6a"></script></body>
</html>
