#Spree

Spree is a full featured commerce platform written for the Ruby on Rails framework. It is designed to make programming commerce applications easier by making several assumptions about what most developers needs to get started.

#Installation

          $ gem install spree
          $ spree install 
          
# Table of Contents
    
* [Custom Authentication in Spree](#custom-authentication-in-spree)
* [Role Management in Spree](#role-management-in-spree)
* [Logic Customization in Spree](#logic-customization-in-spree)
    * [Extending Classes](#extending-classes)
    * [Adding a custom method to the Model](#adding-a-custom-method-to-the-model)
    * [Adding a custom method to the Controller](#adding-a-custom-method-to-the-controller)
* [View Customization in Spree](#view-customization-in-spree)
    * [Using Deface for view customization](#using-deface-for-view-customization)
    * [Replacing entire view templates](#replacing-entire-view-templates)
* [Overriding Spree’s core assets](#overriding-spree’s-core-assets)
    * [Overriding individual CSS styles](#overriding-individual-css-styles)
    * [Overriding entire CSS files](#overriding-entire-css-files)
    * [Overriding individual JavaScript functions](#overriding-individual-javaScript-functions)
    * [Overriding entire JavaScript files](#overriding-entire-javaScript-files)
    * [Overriding images](#overriding-images)
    
# Custom Authentication in Spree

In USAF store we used spree E-Commerce Platform. For admin side authentication we used Rails Devise. Spree already provide Devise for user and admin authentication but we customized spree authentication to achieve different admin roles and their authentication. For this we refereed [Spree Custom Authentication](http://guides.spreecommerce.com/authentication.html)

# Role Management in Spree

Spree by default provide only two major roles (user & admin) but in USAF store we created multiple admin roles (usaf admin & c4g admin) to achive this spree provide Rails cancan. Using this we customized cancan so that we can manage multiple admin roles with different privileges. For this we refereed [Spree Role Management](http://guides.spreecommerce.com/security.html#authorization)

