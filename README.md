import { useState } from "react";

function App() {
  const [formData, setFormData] = useState({
    name: "",
    email: "",
    phone: "",
    password: "",
    gender: "",
    country: ""
  });

  const handleChange = (e) => {
    setFormData({
      ...formData,
      [e.target.name]: e.target.value
    });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(JSON.stringify(formData, null, 2));
  };

  return (
    <>
      <style>{`
        body {
          font-family: Arial, sans-serif;
          background: #f5f5f5;
        }

        #center {
          display: flex;
          flex-direction: column;
          align-items: center;
          margin-top: 40px;
        }

        h1 {
          margin-bottom: 5px;
        }

        .form-box {
          display: flex;
          flex-direction: column;
          gap: 12px;
          width: 300px;
          background: white;
          padding: 20px;
          border-radius: 10px;
          box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        .form-box input,
        .form-box select {
          padding: 10px;
          border: 1px solid #ccc;
          border-radius: 6px;
          font-size: 14px;
        }

        .form-box label {
          font-size: 14px;
        }

        .form-box button {
          padding: 10px;
          background: #646cff;
          color: white;
          border: none;
          border-radius: 6px;
          cursor: pointer;
        }

        .form-box button:hover {
          background: #535bf2;
        }

        .radio-group {
          display: flex;
          gap: 10px;
        }
      `}</style>

      <section id="center">
        <h1>Registration Form</h1>
        <p>Fill all details</p>

        <form className="form-box" onSubmit={handleSubmit}>
          <input
            type="text"
            name="name"
            placeholder="Enter Name"
            value={formData.name}
            onChange={handleChange}
          />

          <input
            type="email"
            name="email"
            placeholder="Enter Email"
            value={formData.email}
            onChange={handleChange}
          />

          <input
            type="tel"
            name="phone"
            placeholder="Enter Phone"
            value={formData.phone}
            onChange={handleChange}
          />

          <input
            type="password"
            name="password"
            placeholder="Enter Password"
            value={formData.password}
            onChange={handleChange}
          />

          {/* Gender */}
          <label>Gender:</label>
          <div className="radio-group">
            <label>
              <input
                type="radio"
                name="gender"
                value="Male"
                onChange={handleChange}
              /> Male
            </label>

            <label>
              <input
                type="radio"
                name="gender"
                value="Female"
                onChange={handleChange}
              /> Female
            </label>
          </div>

          {/* Country */}
          <select name="country" onChange={handleChange}>
            <option value="">Select Country</option>
            <option value="India">India</option>
            <option value="USA">USA</option>
            <option value="UK">UK</option>
          </select>

          <button type="submit">Register</button>
        </form>
      </section>
    </>
  );
}

export default App;# new
