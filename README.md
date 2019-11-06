# PersonalBugLog
When creating software, you’ll make mistakes. Sometimes they’ll be huge, sometimes they’ll be small, sometimes they' ll be stupid but you can always learn from them. This is my attempt to document all the bugs and mistakes I make throughout my dev career. If you happen to find this particular repo useful leave a ⭐️ above. Thanks.


# Bug Entry  #1
## Context
When working on implementing SFsafariview controller in my ios project i ran into the following error.

## Name Of Error:
Terminating app due to uncaught exception 'NSGenericException', reason: 'Misuse of SFSafariViewController interface. Use -initWithURL: or -initWithURL:configuration: instead.'

## Why the bug happened
tried linking the    SFSafariViewController to a view controller int he storyboard 

## How I fixed it.
I removed the main storyboard from the project and instantiated my ViewController from the app delegate file 
```
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey:             Any]?) -> Bool {
        window = UIWindow(frame: UIScreen.main.bounds)
        window?.makeKeyAndVisible()
        window?.rootViewController = UINavigationController(rootViewController: "Name of your View Controller"())
        return true
    }
```

then i wrote this function in the view did load 
```
 let svc = SFSafariViewController(url: NSURL(string: "name of your website")! as URL)
        svc.delegate = self
        self.present(svc, animated: true, completion: nil)
        svc.delegate = self
```


## Lesson learned.
none.
