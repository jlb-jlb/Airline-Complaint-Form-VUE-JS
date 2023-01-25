<template>
  <div class="container">
    <div class="card opacity-75 bg-light">
      <div class="card-body">
        <div class="row">
          <div class="col-sm">
            <h4><b>Complaint Form</b></h4>
            <h5>Flight got canceled? Luggage Lost? Get a refund!</h5>
            <hr class="my-4"/>
          </div>
        </div>
        <div class="row">
          <div class="col-sm">
<!--            <p>First Column</p>-->
<!--            FLIGHT NUMBER -->
            <label for="flight-number" class="form-label">Flight Number</label>
            <div class="input-group mb-3">
  <!--            :class="{ 'is-valid': formSubmitted && flightNumberValid(flightNumber), 'is-invalid': formSubmitted && !flightNumberValid(flightNumber) }"-->
              <span class="input-group-text" id="basic-addon1">ID + up to 4 digits</span>
              <input type="text"
                     class="form-control"
                     id="flight-number"
                     v-model="flightNumber"
                     placeholder="e.g. LH 0001, LH 0001, LH 1..."
                     aria-label="Flight Number"
                     aria-describedby="basic-addon1"
                     :class="{
                       'is-valid': formSubmitted && flightNumberValid(flightNumber),
                       'is-invalid': formSubmitted && !flightNumberValid(flightNumber) }"
              />
            </div>
            <div class="invalid-feedback">
              Please provide a valid flight number.
            </div>
          </div>
          <div class="col-sm">
<!--            <p>Second Column</p>-->
<!--            EMAIL ADDRESS-->
              <div>
                <label for="email-address" class="form-label">Email address</label>
                <div class="input-group mb-3">
                  <input type="email"
                         class="form-control"
                         id="email-address"
                         v-model="emailAddress"
                         placeholder="muster@tu-berlin.de, muster@campus.tu-berlin.de, muster@mailbox.tu-berlin.de"
                         :class="{
                           'is-valid': formSubmitted && emailAddressValid(emailAddress),
                           'is-invalid': formSubmitted && !emailAddressValid(emailAddress) }"
                  >
                </div>
                <div class="invalid-feedback">
                  Please provide a valid email address.
                </div>
              </div>
          </div>
        </div>
        <div class="row">
          <div class="col-sm">
<!--            END EMAIL ADDRESS-->
            <!--            DATE OF FLIGHT-->
            <label for="flight-date" class="form-label">Date of flight</label>
            <div class="input-group mb-3">
              <input type="date"
                     class="form-control"
                     id="flight-date"
                     v-model="flightDate"
                     placeholder="DD-MM-YYYY"
                     :class="{
                       'is-valid': formSubmitted && dateValid(flightDate),
                       'is-invalid': formSubmitted && !dateValid(flightDate) }"
              />
            </div>
            <div class="invalid-feedback">
              Please provide a valid date.
            </div>
          </div>
          <!--            END DATE OF FLIGHT-->
          <!--                  TIME OF FLIGHT-->
          <div class="col-sm">
            <div>
              <label for="flight-time" class="form-label">Time of flight</label>
              <div class="input-group mb-3">
                <input type="time"
                       class="form-control"
                       id="flight-time"
                       v-model="flightTime"
                       placeholder="HH:MM"
                       :class="{
                         'is-valid': formSubmitted && timeValid(flightTime),
                         'is-invalid': formSubmitted && !timeValid(flightTime) }"
                />
              </div>
              <div class="invalid-feedback">
                Please provide a valid time.
              </div>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-sm">
<!--            END FLIGHT TIME-->
<!--            IBAN -->
          <label for="bank-iban" class="form-label">IBAN</label>
            <div class="input-group mb-3">
          <input type="text"
                 class="form-control"
                 id="bank-iban"
                 v-model="bankIban"
                 placeholder="DE12 3456 7890 1234 5678 90"
                  :class="{
                    'is-valid': formSubmitted && ibanValid(bankIban),
                    'is-invalid': formSubmitted && !ibanValid(bankIban) }"
          />
            </div>
            <div class="invalid-feedback">
              Please provide a valid IBAN.
            </div>
          </div>
        </div>
        <hr class="my-4"/>
<!--        END IBAN  -->
<!--        BUTTON SUBMIT  -->
        <div class="container">
          <button type="submit"
                  class="btn btn-primary bi-cursor-fill float-end"
                  @click="formSubmitted = true"
          >
            Submit complaint</button>
        </div>
      </div>
    </div>
  </div>
<!--  <img src='@/assets/overview.jpg' class='img-fluid rounded' alt=''>-->
</template>

<script>

export default {
  name: 'ComplaintForm',
  data() {
    return {
      formSubmitted: false,
      flightNumber: '',
      emailAddress: '',
      flightDate: '',
      flightTime: '',
      bankIban: ''
    };
  },
  methods: {
    flightNumberValid(value) {
      // TODO: implement me
      // regex:
      const regex = /^(([A-Z][A-Z0-9])|([A-Z0-9][A-Z]))([ ]?)([0-9]{1,4})$/; //Up to 10 white spaces between the flight number and the airline code
      console.log("Testing flightNumberValid: " + value + " " + regex.test(value));
      return regex.test(value);
    },
    emailAddressValid(value) {
      // TODO: implement me
      // value; // to suppress warning, delete line
      // regex:
      // check for valid TU Berlin Email address
      const regex = /^([a-zA-Z0-9]+(\.[a-zA-Z0-9]+)*)([.]?)@(((mailbox.)?|(campus.)?)tu-berlin.de)$/;
      console.log("Testing emailAddressValid: " + value + " " + regex.test(value));
      return regex.test(value);
      // return false;
    },
    dateValid(value) {
      // TODO: implement me
      // value; // to suppress warning, delete line
      // regex:
      const regex =/^\d{1,4}-(0?[1-9]|1[0-2])-(0?[1-9]|[1-2][0-9]|3[0-1])$/;
      console.log("Testing dateValid: " + value + " " + regex.test(value));
      return regex.test(value);

      // return false;
    },
    timeValid(value) {
      // TODO: implement me
      // value; // to suppress warning, delete line
      // return false;
      const regex = /^([0-1]?[0-9]|2[0-3]):[0-5][0-9]$/;
      console.log("Testing timeValid: " + value + " " + regex.test(value));
      return regex.test(value);
    },
    ibanValid(value) {
      // TODO: implement me
      // value; // to suppress warning, delete line
      // return false;
      // valid IBAN

      const regex = /^DE[0-9]{2}([ ]?)([0-9]{4})([ ]?)([0-9]{4})([ ]?)([0-9]{4})([ ]?)([0-9]{4})([ ]?)([0-9]{2})$/;
      console.log("Testing ibanValid: " + value + " " + regex.test(value));
      if (!regex.test(value)) {
        return false;
      } else {
        let iban = value.replace(/ /g, '');
        let checksum = parseInt(iban.substring(2, 4), 10);
        console.log("Checksum: " + checksum);
        let rest = iban.substring(4);
        console.log("Rest: " + rest);
        let summed = parseInt((rest.split("")).reduce((a, b) => parseInt(a) + parseInt(b)));
        console.log("Summed: " + summed);
        console.log("Summed % 100: " + (summed % 100));
        console.log("Testing ibanValid: " + value + " " + (checksum === (summed % 100)));
        return checksum === (summed % 100);

      }


    },
  }
}
</script>

<style scoped>
#main-card {
  background-color: rgba(255, 255, 255, 0.9);
}
</style>