#Foursquare

Foursquare is a location-based social networking website mainly for mobile devices. Users "check in" at venues using a mobile, website, text messaging or a device-specific application by selecting from a list of venues the application locates nearby.

Foursquare allows users to let their friends know what they are up to by checking in to different venues. This is great for businesses as it helps them track consumers whereabouts as well as the things they are saying about each venue.  

[Foursquare API](https://developer.foursquare.com/docs/) gives brief about Foursquare APIs.
First you have to create a app in foursquare.just follow below link      
[create a new application in foursquare](https://foursquare.com/developers/register).

Here you have to provide welcome page url and callback url after provioding this much information it will provide you the client ID and Client Secrete save those in development.rb.
In the settings for an app's credentials, there is an option to support connecting via the web. If this option is enabled, foursquare shows a connect button on your foursquare hosted app details page, which takes the user to the first URL in the flow above and then lands the user at your registered redirect URI. If a separate account is required to use your app, you‘ll need to have the user sign-in or create that account in order to associate the foursquare token with the correct account. For example, if you use Facebook identities, the user will need to sign-in via Facebook on your landing page.

In parameteres we will get code,used that for getting access token with the help of **'gem oauth2'** (I have used oauth2).Here I am providing a code snippet for accessing Acess Token.


    code=params[:code] //callback url returns me the 'code' as a parameter
    if code!= nil
    client = OAuth2::Client.new(client_id,client_Secrete,
             :authorize_url => "/oauth2/authorize",
             :token_url => "/oauth2/access_token",
             :site => "https://foursquare.com/")
    token = client.auth_code.get_token(@code, :redirect_uri => 'page address where u want to
                                      redirect after registering to your application  
                                      created in foursquare')
    access_token=token.token
    end


We got **access_ token** now it’s easy to use any of the endpoints,for accessing users data.
different methods for accessing users data is provided [here](https://developer.foursquare.com/docs/.).  
by just adding **oauth token=access_token** as well as **v=Date.today** to your GET or POST request you can access check-ins,tips vennues etc. 
for eg.  
https://api.foursquare.com/v2/users/self/checkins??oauth_token=ACCESS_TOKEN v=Date.today   
####Foursquare2 Gem  
**Foursquare2** is a Ruby gem that provides a wrapper for interacting with the Foursquare API.just run following command:  
**sudo gem install foursquare2**.  

Currently this gem does not handle the oauth2 authentication flow for you, use the oauth2 gem to retrieve and store oauth tokens for a user.eg;    
**client** = Foursquare2::Client.new(:oauth_token => 'user_oauth_token')   
afterwords u can use number of methods (provided by Forsquare2 gem or [Foursquare methods]( https://developer.foursquare.com/docs/)) to fetch client related data.
