# Prelude

What are you thinking about seeing variable `get_UserProfile` in the code?

I think everybody remember [this story] (http://ocka3ke.ru/sites/default/files/styles/large_tale/public/lebed_shchuka_i_rak_2.jpg?itok=LiKKkBQp). It's ok for Crane to fly, it's ok for Pike to swim and Crayfish to walk on the ground but when they unite for a common goal they won't get success using only own skills.

The same with the ROR app. Imagine Crane, Pike and Crayfish began coding. What code would they get at the end?

Every project may have it's own code style but all developers on the project must follow same conventions.
Otherwise the variable `get_UserProfile` will be the smallest surprise along all those things you find in the code.

# Code Smell
Code Smell is any symptom in the source code of a program that possibly indicates a deeper problem. Code smells are usually not bugs—they are not technically incorrect and don't currently prevent the program from functioning. Instead, they indicate weaknesses in design that may be slowing down development or increasing the risk of bugs or failures in the future. [Read more on Wikipedia] (http://en.wikipedia.org/wiki/Code_smell).

[List of Code Smells in Ruby] (https://docs.google.com/spreadsheet/ccc?key=0Anl_DlumkLHhdEtGQ0JHdUFhTG4tcGxldTJEbGZ1NXc&usp=sharing)

# Ruby
First read [Ruby Style Guide] (https://github.com/bbatsov/ruby-style-guide)

* Use double quotes for strings only when you use string interpolation

    ```Ruby
    # bad
    gem "linkedin"
    
    # good
    gem 'linkedin'
    ```
    
* Don't use string interpolation when you need to concatinate string variables

    ```Ruby
    # bad
    buttons = "#{ok_button} #{cancel_button} #{abort_button}"
    
    # good
    buttons = [ok_button, cancel_button, abort_button].join(' ')
    ``` 
  
* Use positive conditions whenever it's possible
    
    ```Ruby
    # bad
    if !requests.any?
    
    # good
    if requests.empty?
    ```
    
    
# Model

* Don't use `get_`, `set_` prefixes in getters/setters method names
    
    ```Ruby
    # bad
    def get_full_name

    # good
    def full_name
    ```    
    
# Rspec

* Avoid using global `let`s. Split big scopes of specs to small independend `context`s.
    
    ```Ruby
    # bad
    describe User do
      let(:user) { FactoryGirl.create(:user) }
      let(:user2) { FactoryGirl.create(:invalid_user) }
    
      it 'should return valid' do
        expect(User.valid).to eql(user)
      end
    
      it 'should return invalid users' do
        expect(User.invalid).to eql(user2)
      end
    end

    # good
    describe User do
      context '.valid' do
        let(:user) { FactoryGirl.create(:user) }
        
        it 'should find valid user' do
          expect(User.valid).to eql(user)
        ebd
      end
      
      context '.invalid' do
        let(:user) { FactoryGirl.create(:invalid_user) }
        
        it 'should find invalid user' do
          expect(User.invalid).to eql(user2)
        end
      end
    ```      
    
# View

* Don't use `#` for `href` in links
    
    ```Ruby
    # bad
    = link_to 'Edit', '#'

    # good
    = link_to 'Edit', 'javascript:void(false);'
    
      
# Javascript

* Use CamelCase code style 

    ```Javascript
    // bad
    function find_user_profile()

    // good
    function findUserProfile()
    ```
    
* Add a namespace to your variables and functions

    ```Javascript
    // bad
    var filters = ['email', 'name', 'timestamp']
    function applyFilter() { ... }
    
    // good
    CoachCatalog = function() {}
    CoachCatalog.filters = ['email', 'name', 'timestamp']
    CoachCatalog.applyFilter = function() { ... }
    ```
    
* Put space before curly bracket

    ```Javascript
    // bad
    function hi(){...}
    
    // good
    function hi() {...}
    ```
    
* Declare local variables with `var`

    ```Javascript
    // bad
    emails = [];
    
    // good
    var emails = [];

# CSS

* Put space before curly bracket

    ```css
    /* bad */
    .row-fluid{...}
    
    /* good */
    .row-fluid {...}
    ```
