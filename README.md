# Prelude

What are you thinking about seeing variable `get_UserProfile` in the code?

I think everybody remember [this story] (http://freelance.ru/img/portfolio/pics/00/04/EF/323514.jpg). It's ok for Crane to fly, it's ok for Pike to swim and Crayfish to walk on the ground but when they unite for a common goal they won't get success using only own skills.

The same with the ROR app. Image Crane, Pike and Crayfish began coding. What code would they get at the end?

Every project may have it's own code style but all developers on the project must follow same conventions.
Otherwise the variable `get_UserProfile` will be the smallest surprise along all those things you find in the code.

# Ruby

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
    buttons = "#{ok_button} {cancel_button} {abort_button}"
    
    # good
    buttons = [ok_button, cancel_button, abort_button].join(" ")
    ```
  
  
* Use positive conditions whenever it's possible

    ```Ruby
    # bad
    if !requests.any?
    
    # good
    if requests.empty?
    ```
    
    
# Model

* Don't use `get_`, `set_` prefixes in method names
    
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
        
        it 'should return invalid users' do
          expect(User.invalid).to eql(user2)
        end
      end
    ```
      
      
# Javascript

* Use CamelCase code style
  
    ```Javascript
    # bad
    function find_user_profile()

    # good
    function findUserProfile()
    ```
