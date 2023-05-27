import React, { useState } from 'react';

const App = () => {
  const [backgroundColor, setBackgroundColor] = useState('white');

  const toggleBackgroundColor = () => {
    setBackgroundColor(prevColor => prevColor === 'white' ? 'lightblue' : 'white');
  };

  return (
    <div style={{ backgroundColor, height: '100vh', display: 'flex', alignItems: 'center', justifyContent: 'center' }}>
      <button onClick={toggleBackgroundColor} style={{ padding: '10px 20px', fontSize: '16px' }}>
        Toggle Background Color
      </button>
    </div>
  );
};

export default App;
