```react
<!DOCTYPE html>
<html>
  <body> 
    <div id="root"></div>
  </body>
  <script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
  <script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  <script type="text/babel">
    function MinutesToHours() {
      const [amount, setAmount] = React.useState(0);
      const [inverted, setInverted] = React.useState(false);
      const onChange = (event) => {
        setAmount(event.target.value) // event가 발생했을 때, 값을 업데이트해주고
      };
      const reset = () => setAmount(0);
      const onInvert = () => {
        reset();
        setInverted((current) => !current);
      };
      return (
      <div>
        <div>
          <label htmlFor="minutes">Minutes</label>
          <input 
            value={inverted ? amount * 60 : amount} // UI에 보여준다
            id="minutes" 
            placeholder="Minutes" 
            type="number" 
            onChange={onChange} // event를 들어주고
            disabled={inverted}
            />  
        </div>
        <div>
          <label htmlFor="hours">Hours</label>
          <input value={inverted ? amount : Math.round(amount / 60)}
            id="hours" 
            placeholder="Hours" 
            type="number"
            onChange={onChange}
            disabled={!inverted}
          />  
        </div>
        <button onClick={reset}>Reset</button>
        <button onClick={onInvert}>{inverted ? "Turn back" : "Invert"}</button>
      </div>
      );
    }
    function KmToMiles() {
      const [distance, setDistance] = React.useState(0);
      const [flipped, setFlipped] = React.useState(false);
      const onChange = (event) => {
        setDistance(event.target.value)
      }
      const reset = () => setDistance(0);
      const onFlip = () => {
        reset();
        setFlipped((current) => !current);
      };
      return (
        <div>
          <div>
            <label htmlFor="km">Km</label>
            <input 
              value={flipped ? distance * 1.609344 : distance} 
              id="km" 
              placeholder="km" 
              type="number" 
              onChange={onChange}
              disabled={flipped}
            />  
          </div>
          <div>
            <label htmlFor="miles">Miles</label>
            <input 
              value={flipped ? distance : distance / 1.609344} 
              id="miles" 
              placeholder="miles" 
              type="number" 
              disabled={!flipped}
              onChange={onChange}
            />   
          </div>
          <button onClick={reset}>Reset</button>
          <button onClick={onFlip}>{flipped ? "Turn back" : "Flip"}</button>
        </div>
      )
    }
    function KgToPound() {
      const [weight, setWeight] = React.useState(0);
      const [flipped, setFlipped] = React.useState(false);
      const onChange = () => {
        setWeight(event.target.value)
      }
      const reset = () => setWeight(0);
      const onFlip = () => {
        reset();
        setFlipped((current) => !current);
      };
      return (
        <div>
          <div>
          <label htmlFor="kg">Kg</label>
          <input
            value={flipped ? weight / 2.2046 : weight}
            id="kg"
            placeholder="kg"
            type="number"
            onChange={onChange}
            disabled={flipped}
          />  
          </div>
          <div>
            <label htmlFor="pound">Pound</label>
            <input
              value={flipped ? weight : weight * 2.2046}
              id="pound"
              placeholder="pound"
              type="number"
              disabled={!flipped}
              onChange={onChange}
            />  
          </div>
          <button onClick={reset}>Reset</button>
          <button onClick={onFlip}>{flipped ? "Turn back" : "Flip"}</button>
        </div>
      )
    }
    function App() {
      const [index, setIndex] = React.useState("xx")
      const onSelect = (event) => {
        setIndex(event.target.value)
      }
      // console.log('render w/', index)
      return (
      <div>
        <h1 className="hi">Super Converter</h1>
        <select value={index} onChange={onSelect}>
          <option value="xx">Select your units</option>
          <option value="0">Minutes & Hours</option>
          <option value="1">Km & Miles</option>
          <option value="2">Kg & Pound</option>
        </select>
        <hr />
        {index === "xx" ? "Please select your units" : null}
        {index === "0" ? <MinutesToHours /> : null}
        {index === "1" ? <KmToMiles /> : null}
        {index === "2" ? <KgToPound /> : null}
      </div>
      );
    }
    const root = document.getElementById("root");
    ReactDOM.render(<App />, root);
  </script>
</html>
```

