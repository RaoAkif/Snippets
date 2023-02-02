# Snippets


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
