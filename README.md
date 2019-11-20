# PersonalBugLog
When creating software, you’ll make mistakes. Sometimes they’ll be huge, sometimes they’ll be small, sometimes they' ll be stupid but you can always learn from them. This is my attempt to document all the bugs and mistakes I make throughout my dev career. If you happen to find this particular repo useful leave a ⭐️ above. Thanks.


# Bug Entry  #1
## Context
When working on implementing SFsafariview controller in my ios project i ran into the following error.

## Name Of Error:
```
Terminating app due to uncaught exception 'NSGenericException', reason: 'Misuse of SFSafariViewController interface. Use -initWithURL: or -initWithURL:configuration: instead.'
```

## Why the bug happened
 i was linking the SFSafariViewController to a view controller in the storyboard 

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
# Bug Entry  #2
## Context
Android app crashing due to inability to instantiate image view.

## Name Of Error:
```
android.view.InflateException: Binary XML file line #9: Error inflating class ImageView
```

## Why the bug happened
 putting the image resources in the drawable-v24 file instead of the drawable file 

## How I fixed it.
move images to the drawable folder


# Bug Entry  #3
## Context
attempting to run a kotlin project, i ran into the following error.

## Name Of Error:
```
Cannot inline bytecode built with JVM target 1.8 into bytecode that is being built with JVM target 
1.6. Please specify proper '-jvm-target' option
```

## Why the bug happened
 ....

## How I fixed it.
I  had to add following in app build.gradle file to make it work.
```
 android {
     // Other code here...
     kotlinOptions {
        jvmTarget = "1.8"
     }
 }
```
