# Filet

Filet is a dsl for acceptance testing on top of Test::Unit.

## Installation

    gem install filet

## Usage

To use filet just include in your test_helper

    require 'filet'
    include Filet

## Hooks

We provide several hooks for options processing.

1. Filet.feature_hook

This allows to process the options you pass for the feature

    Filet.feature_hook do |base, options|
      base.send(:include, Capybara)
    end

2. Filet.context_hook

This allows to process the options you pass for the context

    Filet.context_hook do |base, options|
      base.send(:include, SomeModule) if options[:js]
    end

## Example

    feature ‘Creating a post’, %{
      As a user
      I want to create a post
      In order to show it to people
    } do

      scenario 'Everything goes fine after a submit' do
        # test code
      end

      context 'Something goes wrong', :js => true do
        scenario 'my keyboard stopped working' do
          # test code
        end

        scenario 'I forgot to fill up the form' do
          # test code
        end
      end
    end

## Acknowledgements

We'd like to thank our employer XING AG for letting us work on this project as part of our innovation time and releasing it as open source.
We also want to thank Luismi Cavallé for steak which was our inspiration to do this and all the great people that have made Testing so easy.
