# JBDeviceOwner

Typing names, email addresses, and other personal info is never fun. This is often your user's first experience with your app, and it sucks.

Fortunately, these data often already exist somewhere on your user's phone. `JBDeviceOwner` presents them to you in a simple interface.

`JBDeviceOwner` currently gets you the following attributes:

- Name
- Email address
- Phone number

More are coming.

## API

``` objc
JBDeviceOwner *owner = [UIDevice currentDevice].owner;

// owner will be nil if the user's data could not be found.
if (owner != nil) {
  self.firstNameTextField.text = owner.firstName;
  self.lastNameTextField.text  = owner.lastName;
  self.emailTextField.text     = owner.email;
  self.phoneTextField.text     = owner.phone;
}
```

## How does it work?

It's really simple actually.

Most iPhones are named "Jake Boxer's iPhone" (sometimes with a different person's name instead of mine). Most iPhones have their owner saved in their address book.

`JBDeviceOwner` extracts the owner's name from the device name, finds the matching record in the address book, and populates the `JBDeviceOwner` instance with the data from the record.

If `JBDeviceOwner` can't figure out the owner's name, or if it can't find a matching record in the address book, it won't return anything.

## How to install

1. Download a ZIP/TAR of the framework from the Downloads tab. Unzip/untar it.
1. Drag `JBDeviceOwner.framework` into your project.
1. Add `AddressBook.framework` to your project if it's not there already (it's an Apple framework).
1. Add `-ObjC -all_load` to your target's "Other Linker Flags".
1. Add `#import <JBDeviceOwner/JBDeviceOwner.h>` to any file where you want to use `JBDeviceOwner`.
1. Delight your users!

## Requirements

- iOS 5.0

## Thanks

This library was inspired by [Square](https://squareup.com/)'s iOS app, and by [John Feminella's awesome Quora explanation](http://www.quora.com/Square-company/How-does-Square-know-my-name-in-their-apps-registration-process) of Square's magic.