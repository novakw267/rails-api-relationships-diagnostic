# Rails API Relationships Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  Describe a reason why a join tables may be valuable.

  ```md
    It is valuable because it allows a representation of different types of relationships between tables. Join tables give more options as far as how to represent and manipulate the data in the tables.
  ```

1.  Provide a database table structure and explain the Entity Relationship that
  describes a many-to-many relationship for `Profiles`, `Movies` and `Favorites`
  (Think of Netflix). A `Profile` has a `given_name`, `surname` and `email` and a
  `Movies` have `title`, `release_date`, and `length` and `Favorites` would be the
  join table with references to `Movies` and `Profiles`.

  ```md
  profiles has many movies through favorites. And movies have many profiles through favorites. Favorites belongs to profiles.
  ```

1.  For the above example, what needs to be added to the Model files?

  ```rb
  class Profile < ActiveRecord::Base
  has_many movies through favorites
  has_many favorites

  validates :given_name, presence true
  validates :surname, presence true
  validates :email, presence true
  end
  ```

  ```rb
  class Movie < ActiveRecord::Base
  has_many :profiles through: :favorites

  validates :title, presence true
  validates :release_date, presence true
  validates :length, presnce true
  end
  ```

  ```rb
  class Favorite < ActiveRecord::Base
  has_many :profiles
  has_many :movies

  end
  ```

1.  What is the purpose of a serializer? What would our `Profile` serializer look
like to show all movies favorited by a profile on
`http://localhost:3000/profiles/1`

  ```md
  The Serializer gives the id, and defines the attributes used for the class. This allows the profile to be tracked by their id number.
  ```

  ```rb
  class ProfileSerializer < ActiveModel::Serializer
  attributes :id, :given_name, :surname, :email

  def show_all_movies()
  
  end
  ```

1.  What would the command be to _scaffold_ out a **join table** for Favorites from
the above `Movies` and `Profiles`.

  ```sh
    # < Your Response Here >
  ```

1.  What is `Dependent: Destroy` and where/why would we use it?

  ```md
    # < Your Response Here >
  ```

1.  Think of **ANY** example where you would have a one-to-many relationship as well
as a many-to-many relationship in an application. You only need to list the
description about the resources and how they relate to one another.

  ```md
    # < Your Response Here >
  ```
