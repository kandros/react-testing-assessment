# react-testing-assesment

## Faq

#### Can i eject from create-react-app's react-script?

Yes

#### Can i edit xxx?

Sure, you can editing anything in the project.

#### What test runner or mocking framework should i use?

create-react-app comes with Jest pre-configures and it suppporta mocking out of the box but you can use anything you are confortable with.

---

## Tasks

#### 1) withSwitch Higher order Component testing

Create a **withToggle** HOC that can be used as follows and write tests for `getSecretNumber()`, `defaultIsOn`, `isOn`, `toggle()` and `getSwitchState()` and anything else you find important to test (if any)

```
// BaseSwitch.js
const secretNumber = 42
class BaseSwitch extends React.Component {
  static getSecretNumber = () => {
    return secretNumber
  }

  getSwitchState = () => {
    return { isOn: this.props.isOn }
  }

  render() {
    const { toggle, on } = this.props
    return <div onClick={toggle}> I'm {isOn ? 'on' : 'off'} </div>
  }
}
```

```
// withToggleDemo.js
const Switch = withToggle({defaultIsOn: false })(BaseSwitch)

class App extends Component {
  componentDidMount() {
    console.log(this.r.getSwitchState()) // on or off
    console.log(Switch.getSecretNumber()) // 42
  }

  render() {
    return <Switch ref={n => (this.switch = n)} />
  }
}
```

#### 2) Switch Function children Component testing

Create and test (as withSwitch) a **Switch** component that can be used as follows

```
<Switch defaultIsOn>
{({isOn, toggle}) => <div onClick={toggle}> I'm {isOn ? 'on' : 'off'} </div>}
</Switch>
```

#### 3) withRepo Function children Component testing

Create a **withRepo** HOC with uses Github Api that can be used as follows.

Test loading, error and good-response scenarios (the network calls should be mocked and not hit the network)

`RepoCard`, `Loader`, and `ErrorMessage` implementation is up to you.

```
const WithRepo = withRepo({
  loadingComponent: Loader
  errorComponent: ErrorMessage
})(RepoCard)

...
render{
  return <WithRepo/>
}
...
```

#### 4) Repo Function children Component testing

create and test (as withRepo) a **Repo** Function children that
can be used ad follow.

```
<Repo owner="zeit" project="next.js">
 {({loading, error, repo}) => {
   if (loading) return <Loader/>
   if (error) return <ErrorMessage error={error}/>
   return <RepoCard repo={repo}/>
 }}
</Repo>
```

---

## Bonus Tasks:

These tasks are not mandatory but very appreciated, can be done in any order
but do not focus of these unless the above tasks are completed

### Bonus 1:

Automated testing using [Cypress](https://www.cypress.io/)

### Bonus 2:

Write the app is TypeScript

### Super Bonus:

Use github GraphQL api
