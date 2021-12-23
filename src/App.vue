<template>
  <div id="app">
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
    <div class="container">
      <div class="row">
        <div v-for="item in products" :key="item" class="col-md-4">
          <div class="card">

            <div class="card-header">
              <img :src="item.image" alt="" width="300">
            </div>
            <div class="card-body">
              <h2>{{ item.name }}</h2>
              <h3>{{ item.price }}$</h3>
              {{ item.country }}
            </div>
            <div class="card-footer">
              <button class="btn btn-primary">add card</button>
            </div>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-md-12">
          <table class="table table-stripped m-5">
            <thead>
            <tr>
              <th>№</th>
              <th>Name</th>
              <th>Price</th>
              <th>Country</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="item in products" :key="item">
              <td>{{ index++ }}</td>
              <td>{{ item.name }}</td>
              <td>{{ item.price }}$</td>
              <td><img :src="item.image" alt="" width="100"></td>
            </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios"

export default {
  name: 'App',
  data() {
    return {
      index: -403,
      products: [
        {
          name: "Olma",
          price: 2,
          country: "Saudia Arabi",
          image: "https://i.pinimg.com/originals/b3/c7/8e/b3c78e7e0ae84dd29968531a9cb1f526.jpg"
        },
        {
          name: "Mandarin",
          price: 5,
          country: "Malaziya",
          image: "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHCBYVFRgVFRUYGRgYGRgYGBgYGBgcGhwYGBgaGhgZGhkcIS4lHB4rIRoaJjgmKy8xNTU1GiQ7QDszPy40NTEBDAwMEA8QHhISHzQrJSs0NDQ2NjQ0NDQ0NDY0NDQ0NDQ0NDQ0NDQ0NDQ0NDQ0NDQ0NDQ0NDQ0NjQ0NDQ0NDQ0NP/AABEIAMIBAwMBIgACEQEDEQH/xAAbAAACAwEBAQAAAAAAAAAAAAACAwABBAUGB//EADQQAAEDAgQEBAYCAgMBAQAAAAEAAhEhMQMSQVEEYXGBBSKR8AYTobHB0ULxMuEjUmIVFP/EABoBAAIDAQEAAAAAAAAAAAAAAAECAwQFAAb/xAArEQACAgEEAQEHBQEAAAAAAAAAAQIRAwQSITFBURMiMmFxgcEFQpGx8CP/2gAMAwEAAhEDEQA/APGIkKJUGYDCYmtS2hNao5EsBrVq4dZmLRw91DPosQ7NjVbxRU1HCqt8lgSxaGoeE4V+I7Ixpc7Yfc7Beu8K+Fo82NXZjTTubnokzZow7f2DjxSk+DieH8C/FMMaTuf4jqV6HhvhwfzeSRo2gjWuq9Jh4LWgNaAI0AEDlTVC8kExXlIWdlyzbpcF/Hhiu+TFw/h+Gz/Fo63PqVoJ/pKfMwKjlX7JYYXU7zNxyryULjJ8suRhFIc7FE17pLsQH091S3NgAwJ/E0IS3OFz6/Si5RJYxQ04mlBWfXZJOVwMxy8oqlPxduceysz8c8hFTW3onUCaOGxrsJuxB96Jfy9iCs7sY0JPQX+6t/ET2190R9mwvRxl4HwpCR8/baekhE3HEe/uo5Y34KuTQyirjyNUUaQbKJEUZJp0xjUYS2poTgRbUYQtCMIoYsBEFQVhOjiwjahCNqcKLUVwoiE+HogqVhemZ5djGprEtqYxRyJojmp+BdJanYVwoZliJtatPDcK7EdlY0udsEHB8M7EeGMaSTttqTsF9B4HgMPAEsacxADnVNtJ0WbnzbOF2XcOF5H8hHgPg7eGaXEziOgPOguco/a2v4lxcA2oIJLtGi0gRUnT10Q+I4+RsAgxqDPOu0LHw+OCB5iS+oJkQ3Q9qnuFSnu37n3+TWxYEoWkdXCx21aJOWJOnITvr/a04rWhpc8gAVJNqcyvO4fHkn5WE3MQPM5xgAk3c4arqeHeFyc2I4vcNXCgP/lth9SpsMLlVW/T8sGTGoct0EziWPksY52zoyt7TUjnBSXOLJL3XaR5W/4mk1NT/tdsNgSKaxTTouBxvEBwc7cAFuwDvK5xdbVW8uLbFN9/ITE90qXRg4jFIodNJJ+qyYnE1uemv1VYjjO5Jj0v2lJcRMSBod5Nwqe1GzCCSCfjzFTyoJ6yLJfzWkERI0vQnWQludBI0G/KtkDpE5gSQf4gkf76oqNEyggcTEqQRWhrSk803EeAGjLJNSZsaeo1WUiSaARfedpQPeCQTT/tBMfpPtJdt0bc0C9+eu5ohc4wYNPSl4FFmLpmhiPKDrEieiFzxQkjcXjYIbQbDVhcTlMwcsCx5+hXR4bimvtcXH5Xn3v8pnWTBn0GwmUr5haZaZcIMggbW3qhLCpfUpanSxyr0fqevYmBczwzxEYnlNHjQ6xQwuoqkouLpmJPHKEtrCCJqoImooUJWorTo4gRtQhG1MFBKKQoiE+HqworC9Kzy/kc0I2oGpgUbJ4jWp+EwkwASdgJKS1ev+C/CnF3z3UbVrJ/kTQnoFVzZFCLky1hxuckkdj4e4IYGHmdHzHiv/lujeXNaOI40CQ401AntMFbOL4MubmaYNibAxvt1XmOKztOWPNYA3k0p3KyVFzlvfk9PpcOPbV9DuP4iWsYHTmcZIEXIkx63RgOxnZMPyg/5O/6s07mkBVxPAE42A5tWta9joGsAtNOpXd8P4f5bTUS7zOdpMUAGoAgJsrUFxyyRamGz3e+R3AcKzDaGtEDU6mY8zjqTSq6rcVrQCSADNSQBP8AuvouNh4waRzIudNRA9eydxOO1rQcznCSALkHeSDIrGt1LpKhc338ylkhKUub5H8XxgvmDaRl1NaTE5QuFxPEEkgVOUlxmBQyKdZF9VON8RIGSA0+WTOYgACARuLxN1yMXFLiazu7lKfNNyZd02mpWxjsQkUjn+ZKRJIi8mAJueyU/EJEA0sZAr6pOJiAAAVPLfWVEompGA1xE1EQSdfvoqxMZpb5SZANRNTXW2qynFAFIk1Mz9N+6XBdDY1gQY+9k22yTZ6+BuLiEgTmNqUqVeJikCDAm0j1ssj3hphtwNa66SgD7ukk2ExRNtDwa38ScpE63pSNAlNe2ktrpJsIn7JLXwDXNWYjkg+ZBvUiKBMoiN0OzEyZgZmgdzWVncbiPNWT0/pBmFG1vU+hUz01rpKdKiKQTMRzXBwJm4glev8ABvExith0B4uN+YXj8VgIzNEQPMJ1tRThscscHMJBEJMmJTj8ypnwLJH5+D6K1E1Y/DOMbisDxezhsVtas6mnTMWUXF0wgiCoKwihSwjahCJqcKLUVwoiE+HomIUeGvSM8uuxrQmBC1GAo2yzFG7wrgnY2I1jQYJGYj+LZqTsvo3ynMY1mE05WgACR+1xvg7gCzDOKXScQANaLhom/f7L0uBiVyxEAk/snZY2qy+0ybF0v7N/Q4fZw3tcv+jjPxuIwQ7EIc1oFYGYRSZFQBGq8R8ReNPc9pzO+ZOYPNIb/EAUAb0G+6+neKcfg4bCHgOc8EBhsZGomorp2XgvD+DwuNxyGMeW4TQB/Fji3/FhmoHXQWKt4VGEbl0h88nklaX8Hc+FnPxsMBwInz4roIIY6Pl4Y/8ATmtzO1DXDVwj0ePiEzAFIgd9AqLW4bcjIAkkzck1J57bUAWLGxAZIuBckgAys7JNZZ2lS8E+DFSHOe7TI0E/5Oh0OFKAW7rBxWMRJLs1DBa4A1ucsWm1EjisZtcwcZtJiDqRBIPcLFJJIBjp5jrc9lMqSNDFg8v/AH5KxMUgzae578+qT8+LAHkbH0Wd+JeM1KE+/wAJeIBSYidaj+0VE0441XJbMQgTHIkim9JFTRB82BWJuJFgYp9EAcBQEVmhg0N4OiS7HaDNOVVJVktI0OBIzEkiSBWNYqBpVZ8Qubd2ukx2S3vpqBsDfqszn7TPNOoiN+B5xSbkkmg3OystIuIi+qHh3hrmuNhWm+9NjXsj4nEcCMrhBBtB7k+7I1zSEfALXACTv+ELTAk12/CXyUlGiNsNpgz6V9UGYRHdUobokbI46d+SqUeEAXAEX7VOqW8QSNpRFa4Or4H4icJ4n/E0cOX7XvGOBEioNR0K+YMcva/DHG52ZHXbboqmox/uRn6zDa3r7neCtQKKmjNLCNqAJgTnItRXCiJx8NTGJaYxekZ5iPY9q0cNgF72saPM4ho6lZ2r0Hwfhk8S0j+LXE9Ij7kKvlltg36FzDHdNR9We1wMEYWGxjTRjQO8VPMn8ocNz3OhtqguMho9L60Cc5he6P4g1P4C34USGxGkAWHIeqwNz3cds9Vaxw2peP4Ef/Lwi1uZoeT5S6MstNwQ27dMqa1rMJoaxrWtrDWgNA7DVaWYwJJIgNFAOXNcjieIJM29JTZLdc2v9yRY4uUuSuJxSRM0ncfXVc7ExyaEUBmAI6ybwr4niZAADhEzas1pG1fVYX8SRrpFYtGnqmhFpGlixOuhePiCDAAE0rYG/mNVmfxEAggkEGIMAGIE6lU6ZAFSTakk3oPyVjx8QVrAPTMDzrdWIxs0YY10Rj9YA2BmR1QtbmMxTSZqfvugxXQIvXU6IXuIEwJNgBXupaLHQbzEg0beIH1KzvGUAiKwQNvdkLswFSTSo5d1nBitOSZRI22FiO9dUGeLUVF0kTQTWFTVIkR/MMu32UAi6Bt7E9pPoiauaFZcqyUMqwgRsIo8XDymJBoDTmhdSJ1CEBADQIvdW5xMmZOpPMqKjsmFaDA7rpeD8UWPa/15ixXMA2WjAuOiSatUxJRTTTPpzDIBFjVWud4DxGfCbu2W/pdJZjVOjByR2ycfQgTGpYTGoiIJRRREJ8NITWIIRsXo2eYiuRzV7D4GwJOI/YNbO1yfwvIMC9z8FCMJ53f9mhUtW/8AmzU0EbzI9LlhvLqJlJ+cM0ais1vpKDGxKctB1r9ljdiU6n7f2sZI9NDHfZr+eADWpBHTc/Rc/ExM3Tt7hDiPinr3mVjx+IE8gAB26aqSMS1jxc8DG+a16xUWiba2+ixNYTaYJ8xAJjkIsUOMZEXJ93WY8UWAgCsHKQYgnXZTxi/BcjCSTaLxvK4gCSLcxE1WTG4jU1qJAH0qgc4mS41N/NJjnN0rPEkGxpJ9TS6mjGiwuFz2P4zHzEOGxnMGipsKUp+Vme5xmKaQPdLqPY4jMRShuJjQxoEl+KQRlpBBE8lIkLuSVIp7SDldIOoN0JPIJnE45cQYAiwmSdZ5pTkwtgkqNHsIY1rBoNvVMYJ1i6YA3h8XIZAkEQRN9b9kBdJJ3KEFEAlFYeE/KZIkbewq6DmqCsoCsgEojso1hULagIC0FhMzEiYgSOZ2QDdFQSNqK2D0qusDRGNtA6p2EI+31r+UDQTJjSi0NEGBoK+90smCj03wtiVe3cA+n9r0q8l8PP8A+UcwfsV61Ucq94xdZGsv1IEbUATGpCoWorURGPiEKMREKmr0R5muR7F7f4Nd/wAL+Tz9gvEMXrPg/FpiM18rhPoVV1EbgzT/AE51mR6TicQZYgSTM6ibgrnPf+r2BqtnFVbrrYC435Ln4luna4gVWaoI9dhiqK47HaYIyiknKI6Ai0rC7GjN9uu6b8suJgwPN5jUCKwsWJiZiTqXE9d5P1TKPgt4oxXuisd5mtNdK8lkxC4ydNNpTMQTJJNzrpT0WbiBQD8qWKLHQ7heFz5iXTEABrZrpPLpzWV7DMwWggESPsdR+1TyWwWktOhbII7hTG4hzoB0rcmpFTWymS8iNuy38S4tDZEamKkC0nVJDKZo5TzVhkzAJi5Eq2OgERffQjXqj10LYLmxEGZHpyQFMVOabLrOso4xLQ3QayZvSllUQrLYsoBuURi0QbqqaBdMaJ6JWwNAg6InNWhrxkyxMc6VMzG6V0CWxaLbg87INefuExxI0KosyiNfcrkw0Axs7R71RgTe337KNbSydhAXQbA0W29fYATmMi/U9NO6jWgXqf8ASa1uupP+0gjOl4JPzWnn9DRevXlfBGzit7/ZerVbN8Rja7419CBMCABG1RFIJRWoiE+IKgjQgL0J5tocxei+F+Max+TKMzyIfSQAD5ehXnmrXwj8r2utDmntNVFNWqLWmyeznFn0DiW06kn7lYccX5inUV/S3FxIJuJdB3boSsmK3QcvoPyPsqexUezxS4MGPiQx1YNwAYNYpz1XOIvHIjrFVtx2iIvYg3ECRX0WMsvXl0dT6GEFEuwaRncLuvWxssuIPQ2W8mB1WZ4rMWrHdGqJNxjLUOVbuKxc7pggxEm/fdZ8mqKZ3YWHj5WBoFZJ5dd5SBJqdTPqjOHXspl9EeDqFtbvojym/oiZCqKgeqFhoW5h7qZE8MJnZQsvVduOoXGiIN0CMsjumsZFroOQaFim/NWHbfVMaPX6BW5lhRJYaM8uJV5Dr7K1Nw+SY1k9tea7cIzO3DOvoE1jdY2A/NE4Mm3ryTQ2gpznYftCxWxDGamqfhM1+/vqjGGPvRPw8OUSOTOn4EyXzsCfVegXK8EwoDnbwF1lUyu5GHq5XlZEbUIVhIVg1FFEQnxMhVCIql6A880MantSWpzUkhonrPh7jczCxxq31LYp75LpvFDHILxvAcScN4eOhG41XscN+cBwIgifpRQNHpv0/Pvx7X2jBjYdQdxB+qxPZfnT0XWx2fT8FYsdkXFDePulo2ISOe9uhvod0t+G4AOIoZiJ9Ctj2W1j36pTgZisIMlTMTsOeSF2EBGUzSsixWosm8oHtIsEjJEzJkJ1iqF0ytpbtKAA62SjpmX5eyJrI/X5WgCDyVtZruhY5ldO0ctymfLM1P0uT7+qc3DEyTXqo5+gldZwtuCSZJREbFMY0nQ/lXlpRKzhYHRWxqP5W6a1v1+yBzYoN2KcGI2N2omBsLiOTB+XEpsH9D8q8NmruwRhta31/CKI2wGYYtc298ytLGclWGzl736rdweDmeB7hFulZDkmoptnV4DDysA3qe60hUFaot27MCct0m2WEQVBWEUBBKKKInHxUqAIiFS3jz7QTU9qS1Ow0rGiNau14JxuU5HGhPl67LitTWqKRbwZpYpKSPaOas72bDsVn8I4/OMjj5hbn/tb8YAdN+tkrPT4M0ckVJHNxcOLDtCUR297re8C2u3vRKew7e+SVluLML2bd0AwxBqZ0ArTVaXs3E7QDPoqDCLSD0IISMlTMmTYmfQ+irJstbmSZdEoDhjmlJEzMWjVW1l5+q0EN1QfKBsKblKOmIyDZAAZtRaS06W+qny/9ojqQqN/fZXOgEI2sgwB3TGtQYGxYby/tGG+qIN96Iw1LYjYIYAmNbVQMnpr+E4tA1rpyRQkpAltb2FeSNrdB3Ua2aeyVow2J0iOUqIxvvddfgMHKJ1P2WbhcGTyC6TVWzz/AGoy9Vmv3V9xgVqgoqyKAQRBAEYTHBQqVyqRCfGCFIVuUW/ZgMjU/DSGp+GlZ0RoCa1LamtUMiaI3CJBBFCLL0fhvHB4yujNTvFQV5xqewwQQoXKi5ps8sUuOvQ9Rj4LXNIgSf5RUVlKyA2+lkPBcbIDXX0Oh6rcWTXflqjGSkrRv4s0ZK0c9zTeYKU5hJkzzldJ2GlOwt69lziWYzRzHDQkHYEqOaeXRb/lUIgV3/CV/wDnoZdXQCI7paZKsiMnyQTUwNaVjkqcADAkjdavkHRv1ohewjl0/S6hlPkyRNgeqr5Ue6LS8U5dYVfLB9/ddQ6mZslPyryei0hnv/amSNveyDQd4prNgiybI8gtFeqIYc/uUjiI5C4ik1N0bW7XNyU1uCBUrQzCTJCSmkIwsKgH1W3CwtETMNa8NkKPLmUFS7KOfUUqXYeGyBATQgCNqz7t2zMbbdsMK1QRBMmEpGEIRBNZxaiiiJx8acFUJjwgK3kYLIAnYaUE3DQkBD2hMagamNUMiZDmBNalMTmqGRLE34Vgt3D8SW0NR9QsOBZOCo73CVot45yhzFnYw8Vr7H9o8q4ZeWulpgxC2YHiBs4TzH6VqGoTXvF/HrIviXBvOHKS7DjkmsxWuseyYAplT5RcjO1aZjdTWqVlHddE4YVHBXEqyI5oYZt9FDhe5W84aH5Mm32CA3tTCMPr3RFnRbRh8kQwVxzynP8Akge/cpjcLktowkTWJW0lbFllM7MIf2tDMNMZhoiqeXVpcRKeXUeEC1sJjUCNqqbnLllJtt2wgjagCMLkwoMK1QRBMgkCIIQiCcJaiii4B8ecgUUW+jBkQJuGooukBdmhqYFFFDInQ9ic1RRQSJYm7h7J4UUWfP4mWI9AYyjVFEPAr7GsXT4eyiilwfEXdJ8Q8XRN/Siivs0mQ39PyoP4+9FFEGKELeiFRRccim2RMsoos7W9ogzjQqKiipFUEomqKJl0AMIwoomCgwrCiidDFhE1WoicWooomOP/2Q=="
        },
        {
          name: "Nok",
          price: 3,
          country: "Uzbekistan",
          image: "https://cdn.shopify.com/s/files/1/0104/1059/0266/products/pears.jpg?v=1552283922"
        },
        {
          name: "Mango",
          price: 10,
          country: "Afrika",
          image: "https://imgk.timesnownews.com/story/mangoes.gif?tr=w-400,h-300,fo-auto"
        }
      ]
    }
  },
  created() {
    axios
        .get("http://localhost:3000/student")
        .then(response => (this.products = response.data))
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
