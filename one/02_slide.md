!SLIDE
# in the wild #

!SLIDE
# setup #

!SLIDE

    @@@ ruby
    Capybara.default_driver = :selenium

    # sinatra
    Capybara.app = App

    # remote app
    Capybara.app_host = 'http://www.google.com'

!SLIDE
# set browser #

    @@@ ruby
    Capybara.register_driver :selenium do |app|
      Capybara::Selenium::Driver.new(
        app, :browser => :chrome
      )
    end

!SLIDE
# spec reload #

    @@@ ruby
    context 'when i change the unit width' do
      it 'should show the loading indicator' do
        fill_in 'param-unit-width', :with => 2
        page.should have_selector(
          '.preview-loading-text')
      end
    end

