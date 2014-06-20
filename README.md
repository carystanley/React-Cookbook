React-Cookbook
==============

Recipes for making your React.js Components Awesome, or at least a little cleaner

* [Basics](#basics)
   * [Use 'className' for class](#use-classname-for-class)
   * [Style tags can be done inline](#style-tags-can-be-done-inline)
* [Intermediate](#intermediate)
   * [Use ternary operator for if/else](#use-ternary-operator-for-ifelse)
   * [Use 'map' to cleanly iterate over arrays](#use-map-to-cleanly-iterate-over-arrays)
   * [Use 'classSet' to toggle classes](#use-classset-to-toggle-classes)
   * [ReactLink can be used for two-way data bindings](#reactlink-can-be-used-for-two-way-data-bindings)


### Basics

#### Use 'className' for class

```
render: function() {
  return (
    <button className="Btn Primary">Button</button>
  );
}
```

#### Style tags can be done inline

`NOTE: React uses camelCased for attribute names 'backgroundColor for 'background-color'`

```
render: function() {
  return (
    <div style={{color: 'white', backgroundColor: 'lightblue'}}>Test</div>
  );
}
```

[view fiddle](http://jsfiddle.net/EwCAf/)



### Intermediate

#### Use ternary operator for if/else

```
render: function() {
  var coinflip = Math.random() < .5;
  return (
    <div>
      {(coinflip) ?
        <div>Heads</div> :
        <div>Tails</div>
      }
    </div>
  );
}
```

[view fiddle](http://jsfiddle.net/MBu9v/)

#### Use 'map' to cleanly iterate over arrays

```
render: function() {
  var list = ['one', 'two', 'three'];
  return (
    <ul>
      {list.map(function(item) {
        return <li>{item}</li>
      })}
    </ul>
  );
}
```
[view fiddle](http://jsfiddle.net/ggVt6/)

#### Use 'classSet' to toggle classes
```
render: function() {
  var cx = React.addons.classSet;
  return <div className={cx({
    'message': true,
    'message-important': this.props.isImportant,
    'message-read': this.props.isRead
  })}>Great, I'll be there.</div>;
}
```

[view fiddle](http://jsfiddle.net/v4Uwb/2/)

#### ReactLink can be used for two-way data bindings

```
mixins: [React.addons.LinkedStateMixin],
getInitialState: function() {
  return {value: 'Hello!'};
},
render: function() {
  return (
    <div>
      <input type="text" valueLink={this.linkState('value')} />
      <div>You typed: {this.state.value}</div>
    </div>
  );
}
```

[view fiddle](http://jsfiddle.net/vvS8F/)
