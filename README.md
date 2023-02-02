# Snippets

### Fetch Data using axios and useEffect from an endpoint with try and catch

```
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function UserData() {
  const [user, setUser] = useState({});
  const [error, setError] = useState(null);

  useEffect(() => {
    async function fetchData() {
      try {
        const response = await axios.get('https://randomuser.me/api/');
        setUser(response.data.results[0]);
      } catch (err) {
        setError(err);
      }
    }

    fetchData();
  }, []);

  if (error) {
    return <p>An error occurred: {error.message}</p>;
  }

  return (
    <div>
      <p>Name: {user.name && user.name.first} {user.name && user.name.last}</p>
      <p>Email: {user.email}</p>
      <p>Phone: {user.phone}</p>
    </div>
  );
}

export default UserData;

```

### Fetch Data using useEffect from an endpoint WITHOUT axios
```
import React, { useState, useEffect } from 'react';

function UserData() {
  const [user, setUser] = useState({});

  useEffect(() => {
    async function fetchData() {
      const response = await fetch('https://randomuser.me/api/');
      const data = await response.json();
      setUser(data.results[0]);
    }

    fetchData();
  }, []);

  return (
    <div>
      <p>Name: {user.name && user.name.first} {user.name && user.name.last}</p>
      <p>Email: {user.email}</p>
      <p>Phone: {user.phone}</p>
    </div>
  );
}

export default UserData;

```

### Fetch Data using axios and useEffect from an endpoint
```
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function UserData() {
  const [user, setUser] = useState({});

  useEffect(() => {
    async function fetchData() {
      const result = await axios.get('https://randomuser.me/api/');
      setUser(result.data.results[0]);
    }

    fetchData();
  }, []);

  return (
    <div>
      <p>Name: {user.name && user.name.first} {user.name && user.name.last}</p>
      <p>Email: {user.email}</p>
      <p>Phone: {user.phone}</p>
    </div>
  );
}

export default UserData;
```

### Map a list and map on the DOM
```
import React from 'react';

function FruitList() {
  const fruits = ['apple', 'banana', 'cherry', 'grape', 'orange'];

  return (
    <ul>
      {fruits.map((fruit, index) => (
        <li key={index}>{fruit}</li>
      ))}
    </ul>
  );
}

export default FruitList;

```

### Delete Operation on the list
```
import React, { useState } from 'react';

function FruitList() {
  const [fruits, setFruits] = useState(['apple', 'banana', 'cherry', 'grape', 'orange']);

  const handleDelete = (index) => {
    setFruits(fruits.filter((fruit, i) => i !== index));
  };

  return (
    <ul>
      {fruits.map((fruit, index) => (
        <li key={index}>
          {fruit}
          <button onClick={() => handleDelete(index)}>Delete</button>
        </li>
      ))}
    </ul>
  );
}

export default FruitList;

```
