!SLIDE
# dsl #

!SLIDE
# navigating #
    @@@ ruby
    visit('/projects')
    visit(post_comments_path(post))

!SLIDE
# clicking links and buttons #
    @@@ ruby
    click_link('id-of-link')
    click_link('Link Text')
    click_button('Save')
    click_on('Link Text') # links or buttons

!SLIDE
# interacting with forms #
    @@@ ruby
    fill_in('Username', :with => 'user')
    choose('A Radio Button')
    check('A Checkbox')
    attach_file('Image', '/path/to/image.jpg')
    select('Option', :from => 'Select Box')

!SLIDE
# querying (rspec matchers) #
    @@@ ruby
    page.should have_selector('table tr')
    page.should have_selector(
      :xpath, '//table/tr')
    page.should have_xpath('//table/tr')
    page.should have_css('table tr.foo')
    page.should have_content('foo')

!SLIDE
# finding #
    @@@ ruby
    find_field('First Name').value
    find_link('Hello').visible?
    find_button('Send').click

    find("#overlay").find("h1").click
    all('a').each { |a| a[:href] }

!SLIDE
# scoping #
    @@@ ruby
    within("li#employee") do
      fill_in 'Name', :with => 'Jimmy'
    end

!SLIDE
# scripting #
    @@@ ruby
    page.execute_script("$('body').empty()")
    result = page.evaluate_script('4 + 4');

!SLIDE
# debugging #
    @@@ ruby
    save_and_open_page # snapshot
    print page.html

