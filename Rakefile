# frozen_string_literal: true

# {{{ Intended Use
#     rake validate:git
#     Use amber to run git client tool validation.
#
# -------------------------------------------------------------------------- }}}
# {{{ Required files.

require 'open3'
require 'fileutils'
require 'rake'
require 'rake/clean'
require 'shellwords'

# -------------------------------------------------------------------------- }}}
# {{{ Customize build and validate variables.

validate_cmd = lambda {
  [File.join(ENV.fetch('AMBERPATH'), 'bin', 'amber'),
   '-n', '-L', '-O', '-w', 'LaTeX', '-p', 'command-line']
}
pdf_cmd = -> { ['rake', '--rakefile', File.join(ENV.fetch('DOCBLDPATH'), 'Rakefile'), '--build-all', 'deploy'] }
quicksort_source = '/home/traap/soup/quicksort'
quicksort_remote = 'remote/quicksort.git'

# -------------------------------------------------------------------------- }}}
# {{{ Validate Git.

task default: :'validate:git'

namespace :validate do
  task git: %i[check_env prepare_quicksort_remote clean_workspace run docbld]

  task :check_env do
    require_env('AMBERPATH')
    require_env('AUTODOCPATH')
    require_env('DOCBLDPATH')
    abort "#{quicksort_source} must exist." unless Dir.exist?(quicksort_source)
    abort "#{amber_bin} must be executable." unless File.executable?(amber_bin)
  end

  task :prepare_quicksort_remote do
    FileUtils.rm_rf quicksort_remote
    FileUtils.mkdir_p File.dirname(quicksort_remote)
    run_command!(['git', 'clone', '--bare', quicksort_source, quicksort_remote])
  end

  task :clean_workspace do
    FileUtils.rm_rf %w[package-0 package-1 package-2 test-output _build]
  end

  task :run do
    run_command!(validate_cmd.call)
  end

  task :docbld do
    run_command!(pdf_cmd.call)
  end

  def require_env(name)
    abort "#{name} must be defined." if ENV[name].to_s.empty?
  end

  def amber_bin
    File.join(ENV.fetch('AMBERPATH'), 'bin', 'amber')
  end

  def run_command!(command)
    puts command.shelljoin
    stdout, stderr, status = Open3.capture3(*command)
    puts stdout unless stdout.empty?
    warn stderr unless stderr.empty?
    abort "Command failed with status #{status.exitstatus}: #{command.shelljoin}" unless status.success?
  end
end

# -------------------------------------------------------------------------- }}}
