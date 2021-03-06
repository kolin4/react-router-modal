<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Table of Contents

-   [index](#index)
-   [ModalContainer](#modalcontainer)
-   [ModalLink](#modallink)
-   [ModalRoute](#modalroute)
-   [Modal](#modal)

## index

**Examples**

_TL;DR_

```javascript
import { ModalContainer, ModalRoute } from 'react-router-modal';
import { BrowserRouter, Link } from 'react-router-dom';

function FooModal() {
 return <div>FOO</div>;
}

function BarModal() {
 return <div>BAR</div>;
}

function Example() {
return (
  <BrowserRouter>
    <div>
      <Link to='/foo'>show foo</Link>
      <Link to='/bar'>show bar</Link>

      <ModalRoute component={FooModal} path='/foo' className='test-modal test-modal-foo'/>
      <ModalRoute component={BarModal} path='/bar' className='test-modal test-modal-bar'/>

      <ModalContainer />
    </div>
  </BrowserRouter>
);
}
```

## ModalContainer

**Extends React.Component**

Container for rendered modals.

This should be included in your react app as one of the last elements before the closing body tag.
When modals are rendered, they live inside this container.
When no modals are shown, nothing is rendered into the DOM.

**Parameters**

-   `props` **Props** 
    -   `props.modalClassName` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** class name to apply to modals (optional, default `react-router-modal__modal`)
    -   `props.backdropClassName` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** class name to apply to modal backdrops (optional, default `react-router-modal__backdrop`)
    -   `props.containerClassName` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** class name to apply to the container itself (optional, default `react-router-modal__container`)
    -   `props.bodyModalClassName` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** class name to apply to the <body /> when any modals are shown (optional, default `react-router-modal__modal-open`)

**Examples**

_Using default class names_

```javascript
<ModalContainer />
```

_Overriding the default class names_

```javascript
<ModalContainer
  bodyModalOpenClassName='modal-open'
  containerClassName='modal-container'
  backdropClassName='modal-backdrop'
  modalClassName='modal'
/>
```

_DOM structure_

```javascript
// Note that modals are made "modal" via CSS styles, and end up rendered like the following in the DOM (with two modals, for example):
<div className={containerClassName}>
  <div>
    <div className={backdropClassName} />
    <div className={modalClassName}>
      .. bottom-most modal contents ..
    </div>
  </div>
  <div>
    <div className={backdropClassName} />
    <div className={modalClassName}>
      .. top-most modal contents ..
    </div>
  </div>
</div>
```

## ModalLink

Link and ModalRoute in one convenient component
Renders a link that, when clicked, will navigate to the route that shows the modal.

**Parameters**

-   `props` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** 
    -   `props.path` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** path to match
    -   `props.exact` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** If set, only show modal if route exactly matches path.
    -   `props.parentPath` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** path to navigate to when backdrop is clicked
    -   `props.linkClassName` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** class name to apply to <Link />
    -   `props.modalClassName` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** class name to apply to modal container
    -   `props.children` **Children** Link contents. Note that Modal content must be specified by the component property.
    -   `props.component` **ReactComponent** Component to render in the modal.
    -   `props.props` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** Props to be passed to the react component specified by the component property.

**Examples**

_Example ModalLink_

```javascript
<ModalLink path='/hello' component={HelloComponent}>
  Say Hello
</ModalLink>
```

Returns **any** 

## ModalRoute

A react-router Route that shows a modal when the location pathname matches.

**Parameters**

-   `props` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** 
    -   `props.path` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** path to match
    -   `props.parentPath` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** path to navigate to when backdrop is clicked
    -   `props.className` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** class name to apply to modal container
    -   `props.children` **Children** modal content can be specified as chld elements
    -   `props.component` **ReactElement** modal content can be specified as a component type
    -   `props.exact` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** If set, only show modal if route exactly matches path.
    -   `props.props` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** Props to be passed to the react component specified by the component property.When the route matches, the modal is shown.
        If multiple routes match, the modals will be stacked based on the length of the path that is matched.
    -   `props.match`  
    -   `props.history`  

Returns **React.Element&lt;any>** 

## Modal

**Extends React.Component**

Renders its contents in a modal div with a backdrop.
Use Modal if you want to show a modal without changing the route.

The content that is shown is specified by _either_ the "component" prop, or by
child elements of the Modal.

**Parameters**

-   `props` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** 
    -   `props.stackOrder` **[Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** order to stack modals, higher number means "on top"
    -   `props.className` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** class name to apply to modal container
    -   `props.children` **Children** Modal content can be specified as chld elements
    -   `props.component` **Component** React component to render in the modal.
    -   `props.props` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** props to pass to the react component specified by the component property

**Examples**

_Modals using a component and props, vs. child elements_

```javascript
const Hello = ({ who }) => (<div>Hello {who}!</div>);

// component and props
const ComponentExample = () => (
  <Modal
   component={Hello}
   props={{ who: 'World' }}
  />
);

// using child elements
const ChildrenExample = () => (
  <Modal>
    <Hello who='World' />
  </Modal>
);
```

_Specifying stack order_

```javascript
<div>
  <Modal
    className='top-component-modal'
    component={MyTopComponent}
    props={ { foo: 'bar'} }
    stackOrder={2}
  />
  <Modal
    component={MyBottomComponent}
    props={ { bar: 'baz'} }
    stackOrder={1}
  />
</div>
```
