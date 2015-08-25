# -*- mode: ruby -*-
# vi: set ft=ruby :
require 'yaml'

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  env = ENV.fetch('IOTA_ENV', 'local')

  if File.exist?("config/#{env}/ips.yaml")
    ips = YAML.load_file("config/#{env}/ips.yaml")
  else
    ips = nil
  end

  config.vm.define 'iota' do |iota|
    iota.vm.network 'private_network', ip: ips['iota'] if ips
    iota.vm.network "forwarded_port", guest: 8000, host: 8001
  end
end
