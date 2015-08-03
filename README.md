ActsAsAuthoritah
================

Authoritah was designed to provide fine grained access for Ruby on Rails applications. It allows you to specify ACLs (Access Control List) for a complex application with users having a variety of roles, and these roles changing dynamically depending on the part/pages in the application that they are on.

Authoritah abstracts out the rules for access control and moves it away from the code, so that its not spread across multiple files, making it difficult to understand or change.

Authoritah can work with any authentication or role system that your app uses.

ACLs can be specified as a matrix stored as a CSV file. Opening the CSV file in Excel or a CSV viewer makes the ACL readable/viewable instead of being embedded within code in multiple files within the application.

Installation
------------

Add this to your Gemfile:

```gem 'acts_as_authoritah'```

Basic Usage
-----------

* Add these lines to your User model (assuming that User is your model representing users in your app)

```
  include ActsAsAuthoritah::Core
  acts_as_authoritah Rails.root.join('config/access_rights/')
```

* Add a 'usertype' method to the User model

```
  def usertype(args={})
    // self.role_name - may be as simple as this or
    // something more complex depending on your app.
    // Also see advanced usage section below.
  end
```

This method should return the role of the the user. This is Authoritah's interface with your role system.

* Create config/access_rights/default.csv (path can be changed in the User model)

![default.csv](https://photos-4.dropbox.com/t/2/AACrz2ZBvZ3IW-jkCCnZTFgZsb2rJJ7uLdF6jKz4B-448w/12/16078516/png/32x32/1/1438621200/0/2/Screenshot%202015-08-03%2020.45.55.png/CLSt1QcgASACIAMgBCAFIAYgBygBKAIoBw/xu44g4ZZUOlR81T6LJ4Ccaio-_LyAw3lDDlGOLMpRhI?size_mode=5)



