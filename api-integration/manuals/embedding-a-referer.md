# Embedding a referer

## Here is an example of how to embed a referer using axios.

```
import axios from 'axios';

// Create Axios instance with baseURL
const axiosInstance = axios.create({ baseURL: 'https://cdn.imagin.studio/getImage?customer=yourCustomerValue' });

// Function to fetch data with custom referrer header
const fetchData = async () => {
  try {
    const response = await axiosInstance.get('/data', { headers: { 'Referer': 'https://myapp.com' } });
    console.log('Data:', response.data);
  } catch (error) {
    console.error('Error fetching data:', error);
  }
};

// Example usage
fetchData(); // Make a GET request with custom referrer header
```

{% hint style="info" %}
Our service api’s (getCarListing, getPaints and getPaintSwatches), do pup up in usage but will not be charged.
{% endhint %}
