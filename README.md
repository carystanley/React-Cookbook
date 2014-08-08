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
   * [Reduce can be used for simple list filtering](#reduce-can-be-used-for-simple-list-filtering)
   * [Use bind to map specifiic parameters for event handlers](#use-bind-to-map-specifiic-parameters-for-event-handlers)
   * [Handler callback functions can be used a props to get events for subcomonents](#handler-callback-functions-can-be-used-a-props-to-get-events-for-subcomonents)

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

#### Reduce can be used for simple list filtering

```
return (
  <ul>
      {messages.reduce(function(messages, item) {
        if (match(item, filter)) {
          messages.push(<li>{item.title}</li>)
        }
        return messages;
      }, [])}
  </ul>
);
```

[view fiddle](http://jsfiddle.net/qTQtD/)

#### Use bind to map specifiic parameters for event handlers

```
		onClick: function(value, e) {
			e.preventDefault();
			this.props.onChange({
				choice: value
			}, true);
			this.setState({
				choice: value
			});
		},

		render: function() {
			var self = this,
				cx = React.addons.classSet,
				choices = this.props.choices,
				selected = this.state.choice;

			return (
				<ul className="Choices">
					{choices.map(function(choice) {
						return <li key={choice.value} className={cx({'Selected': (choice.value === selected)})}><a href='#' onClick={self.onClick.bind(null, choice.value)}>{choice.label}</a></li>;
					})}
				</ul>
			);
		}
```

> Note: bind should have "null" as its first parameter, React will automatically re-bing with "this"

[view fiddle](http://jsfiddle.net/1w57b59n/3/)

#### Handler callback functions can be used a props to get events for subcomonents

```
		onClick: function(value, e) {
			e.preventDefault();
			this.props.onChange({
				choice: value
			}, true);
			this.setState({
				choice: value
			});
		},


...

    <div>
        <div>{'Selected: ' + this.state.selected}</div>
        <Chooser choices={choices} onChange={this.choiceChange} />
    </div>
```

[view fiddle](http://jsfiddle.net/1w57b59n/3/)

