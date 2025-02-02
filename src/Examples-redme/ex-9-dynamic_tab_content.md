![output](../../section-3.png)



```javascript
export default function TabButton({ children , onSelect}) {

  return (
    <li>
      <button onClick={onSelect}>{children}</button>{" "}
    </li>
  );
}
```

```javascript
import Header from "./components/Header";
import { CORE_CONCEPTS } from "../data";
import CoreConcept from "./components/CoreConcept";
import TabButton from "./components/TabButton";
import { useState } from "react";

function App() {

  const [seletedTopic, setSelectedTopic]=useState('Please click a tab button');


  function handleSelect(selectedButton) {
    //selectedButton=>'componetBtn',jsxBtn  // string takes
    console.log(selectedButton,"button --selected");
    setSelectedTopic(`${selectedButton} content is Showing. This done by useState() hook.`);
  }

  return (
    <div>
      <Header />
      <main>
        <section id="core-concepts">
          <h2>Core Concept</h2>
          <ul>
            <CoreConcept {...CORE_CONCEPTS[0]} />
            <CoreConcept {...CORE_CONCEPTS[1]} />
            <CoreConcept {...CORE_CONCEPTS[2]} />
            <CoreConcept
              title={CORE_CONCEPTS[2].title}
              description={CORE_CONCEPTS[2].description}
              image={CORE_CONCEPTS[2].image}
            />
          </ul>
        </section>
        <section id="examples">
          <h2>Tab Buttons</h2>
          <menu>
            <TabButton onSelect={()=>handleSelect('component')}>Component-Btn</TabButton>
            <TabButton onSelect={()=>handleSelect('jsx')}>JSX-Btn</TabButton>
            <TabButton onSelect={()=>handleSelect('props')}>Props-Btn</TabButton>
            <TabButton onSelect={handleSelect }>State-Btn</TabButton>
          </menu>
          <b>useState hook</b> for Dynamic Content showing. <br /> <br />
          <span style={{ }}> {seletedTopic}</span>
        </section>
      </main>
    </div>
  );
}

export default App;

```