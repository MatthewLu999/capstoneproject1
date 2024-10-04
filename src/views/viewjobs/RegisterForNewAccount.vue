<template>
 <div class="container">
        <h2>Membership Registration</h2>
        <form id="membershipForm">
            <label for="fullName">Full Name:</label>
            <input type="text" id="fullName" name="fullName" placeholder="Enter your full name" required>

            <label for="email">Email:</label>
            <input type="email" id="email" name="email" placeholder="Enter your email" required>

            <label for="phone">Phone Number:</label>
            <input type="tel" id="phone" name="phone" placeholder="Enter your phone number" pattern="[0-9]{10}" required>

            <label for="dob">Date of Birth:</label>
            <input type="date" id="dob" name="dob" required>

            <div class="radio-group">
                <label>Gender:</label>
                <input type="radio" id="male" name="gender" value="male">
                <label for="male">Male</label>
                <input type="radio" id="female" name="gender" value="female">
                <label for="female">Female</label>
            </div>

            <label for="address">Address:</label>
            <input type="text" id="address" name="address" placeholder="Enter your address" required>

            <label for="membershipType">Membership Type:</label>
            <select id="membershipType" name="membershipType" required>
                <option value="">Select...</option>
                <option value="basic">Basic</option>
                <option value="premium">Premium</option>
            </select>

            <label for="password">Password:</label>
            <input type="password" id="password" name="password" placeholder="Enter your password" minlength="6" required>

            <label for="confirmPassword">Confirm Password:</label>
            <input type="password" id="confirmPassword" name="confirmPassword" placeholder="Confirm your password" required>
            <button type="button">Register</button>
        </form>
    </div>
</template>
<script>
export default {
  name: 'RegisterForNewAccount',
  mounted () {
    document.getElementById('membershipForm').addEventListener('submit', function (event) {
      const password = document.getElementById('password').value
      const confirmPassword = document.getElementById('confirmPassword').value
      const phoneNumber = document.getElementById('phone').value
      // Check if passwords match
      if (password !== confirmPassword) {
        alert('Passwords do not match.')
        event.preventDefault()
      }
      // Validate phone number (should be exactly 10 digits)
      const phonePattern = /^[0-9]{10}$/
      if (!phonePattern.test(phoneNumber)) {
        alert('Please enter a valid 10-digit phone number.')
        event.preventDefault()
      }
      this.LoginPageBack()
    })
  },
  methods: {
    LoginPageBack () {
      this.$router.push({ name: 'LoginForm' })
    }
  }
}
</script>
