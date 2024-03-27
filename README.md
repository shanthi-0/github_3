# github_3
// Express.js server code

const express = require('express');
const mongoose = require('mongoose');
const app = express();
const PORT = process.env.PORT || 5000;

// Connect to MongoDB
mongoose.connect('mongodb+srv://<username>:<password>@<cluster>/<dbname>?retryWrites=true&w=majority', {
  useNewUrlParser: true,
  useUnifiedTopology: true
});

// Define MongoDB Schema and Model
const Schema = mongoose.Schema;
const YourDataSchema = new Schema({
  // Define your schema fields
});
const YourDataModel = mongoose.model('YourData', YourDataSchema);

// Endpoint to fetch data
app.get('/api/data', async (req, res) => {
  try {
    const data = await YourDataModel.find();
    res.json(data);
  } catch (err) {
    console.error(err);
    res.status(500).json({ message: 'Server Error' });
  }
});

app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
