Facebook setup. Thanks to https://github.com/dagerydoo/ShareKit

1. At the top of your AppDelegate.m file, be sure to include SHKFacebook.h:

#import "SHKFacebook.h"

... and <FBSessionDelegate> to the AppDelegate interface.

2. In your AppDelegate, include these two methods (or merge if you already use them, remembering to properly delegate):

- (BOOL)application:(UIApplication *)application 
            openURL:(NSURL *)url 
  sourceApplication:(NSString *)sourceApplication 
         annotation:(id)annotation 
{
  return [SHKFacebook handleOpenURL:url];
}

- (BOOL)application:(UIApplication *)application 
      handleOpenURL:(NSURL *)url 
{
  return [SHKFacebook handleOpenURL:url];
}

3. In your App-Info.plist, include this property:

        <key>CFBundleURLTypes</key>
        <array>
                <dict>
                        <key>CFBundleURLName</key>
                        <string></string>
                        <key>CFBundleURLSchemes</key>
                        <array>
                                <string>fb${FACEBOOK_APP_ID}</string>
                        </array>
                </dict>
        </array>

Where fb${FACEBOOK_APP_ID} looks like fb1234

4. Finally, in SHKConfig.h, set the facebook API ID:

#define SHKFacebookAppID      @"1234"

5. Follow the standard ShareKit instructions...
