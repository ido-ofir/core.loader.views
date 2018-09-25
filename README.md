# core.loader.views

load views from plugin definition

related to <a href="https://github.com/ido-ofir/core.type.view">core.type.view</a>

```js
let core = new require('core.constructor')();
 
core.plugin(
    require('core.type.view'),
    require('core.loader.views')
);

// plugins can now declare views on the plugin definition object:
core.plugin({
    name: 'test',
    tree: {    // define plugin's tree
        a: '√'
    },
    views: [
        {
            name: 'SomeView',
            bindings: {   // binding data from the plugin's tree
                a: 'a'
            },
            get(){
                return {
                    render(){
                        let { a } = this.props;   // bound data is available in props
                        return <div>{ a }</div>
                    }
                };
            }
        }
    ]
});

// require this new view
core.require(['test.SomeView'], SomeView => { ... })

// exists on core.views
core.views['test.SomeView'];

// exists on plugin views
core.plugins.test.views.SomeView;
```
