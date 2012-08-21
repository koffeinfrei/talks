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
# per spec #

    @@@ ruby
    Capybara.javascript_driver = :selenium

    # ...

    describe 'requires js', :js => true do
      it 'will use the default js driver'
      it 'will switch to one specific driver',
        :driver => :webkit
    end

!SLIDE
# set browser #

    @@@ ruby
    Capybara.register_driver :selenium do |app|
      Capybara::Selenium::Driver.new(
        app, :browser => :chrome
      )
    end

!SLIDE
# in the wild #

!SLIDE bullets incremental
# metaflop #
* web based platform for metafonts and related type projects
* modulator
* experimental font generation
* export as otf, webfont

!SLIDE
# spec sample 1 #

    @@@ ruby
    context 'when i change the unit width' do
      it 'should show the loading indicator' do
        fill_in 'param-unit-width', :with => 2
        page.should have_selector(
          '.preview-loading-text')
      end
    end

!SLIDE
# spec sample 2 #

    @@@ ruby
    context 'when i enable anatomy' do
      it 'shows the anatomy image' do
        within '#menu' do
          click_link 'on'
        end
        page.should have_selector '#info-panel'
      end
    end

!SLIDE
# spec sample 3 #
    @@@ ruby
    context 'when i click the "webfont" link' do
      it 'should call the font generator url' do
        click_link('webfont')
        current_url.should
          include 'modulator/export/font/web'
      end
    end


.notes git co -b capybara-eachbrowser
.notes change to firefox/chrome
.notes change to webkit
