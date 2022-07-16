# frozen_string_literal: true

# {{{ Intended Use
#     rake validate:git
#     Use amber to run git client tool validation.
#
# -------------------------------------------------------------------------- }}}
# {{{ Required files.

require 'open3'
require 'rake'
require 'rake/clean'

# -------------------------------------------------------------------------- }}}
# {{{ Prerequisite checks.

if ENV['AMBERPATH'].empty?
  puts 'WARNING: Amber is not installed.'
  abort = true
end

if ENV['AUTODOCPATH'].empty?
  puts 'WARNING: Autodoc is not installed.'
  abort = true
end

if ENV['DOCBLDPATH'].empty?
  puts 'WARNING: docbld is not installed.'
  abort = true
end

exit if abort

# -------------------------------------------------------------------------- }}}
# {{{ Customize build and validate variables.

validate_cmd = 'amber -n -L -O -w LaTeX -p command-line'
pdf_cmd = "rake --rakefile #{ENV['DOCBLDPATH']}/Rakefile"

# -------------------------------------------------------------------------- }}}
# {{{ Validate Git.

task default: :'validate:git'

namespace :validate do
  task git: %i[do_validation docbld]

  task :do_validation do
    puts validate_cmd.to_s
    _stdout, stderr, _status = Open3.capture3 validate_cmd
  rescue StandardError => e
    echo_exception(stderr, e)
  end

  task :docbld do
    puts 'docbld'
    _stdout, stderr, _status = Open3.capture3 pdf_cmd
  rescue StandardError => e
    echo_exception(stderr, e)
  end

  def echo_exception(_, exception)
    puts "Exception Class: #{exception.class.name}"
    puts "Exception Message: #{exception.class.message}"
    puts "Exception Backtrace: #{exception.class.backtrace}"
  end
end

# -------------------------------------------------------------------------- }}}
