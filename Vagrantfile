required_plugins = %w{
  vagrant-openstack-provider
}

plugins_to_install = required_plugins.select { |plugin| not Vagrant.has_plugin? plugin }
if not plugins_to_install.empty?
  puts "Installing plugins: #{plugins_to_install.join(' ')}"
  system "vagrant plugin install #{plugins_to_install.join(' ')}"
  exec "vagrant #{ARGV.join(' ')}"
end

require 'vagrant-openstack-provider'
#require 'aws-sdk-v1'
#require 'vagrant-aws-route53'

Vagrant.configure('2') do |config|
  config.ssh.username = 'vagrant'
  config.vm.boot_timeout = 960

  config.vm.define 'a-es-1' do |define|
    define.vm.provider :openstack do |provider, override|
      provider.image = 'ubuntu_pan_es_20161117051135'
      provider.flavor = 'n-rd1.large'
      provider.server_name = "a-es-1-athornton"
      provider.security_groups = ['default', 'panopticon_site', 'remote SSH', 'elasticsearch']
    end
  end

  config.vm.define 'a-es-2' do |define|
    define.vm.provider :openstack do |provider, override|
      provider.image = 'ubuntu_pan_es_20161117051135'
      provider.flavor = 'n-rd1.large'
      provider.server_name = "a-es-2-athornton"
      provider.security_groups = ['default', 'panopticon_site', 'remote SSH',
                                  'elasticsearch']
    end
  end

  config.vm.define 'a-es-3' do |define|
    define.vm.provider :openstack do |provider, override|
      provider.image = 'ubuntu_pan_es_20161117051135'
      provider.flavor = 'n-rd1.large'
      provider.server_name = "a-es-3-athornton"
      provider.security_groups = ['panopticon_site', 'remote SSH',
                                  'elasticsearch']
    end
  end

  config.vm.define 'a-es-4' do |define|
    define.vm.provider :openstack do |provider, override|
      provider.image = 'ubuntu_pan_es_20161117051135'
      provider.flavor = 'n-rd1.large'
      provider.server_name = "a-es-4-athornton"
      provider.security_groups = ['default', 'panopticon_site', 'remote SSH',
                                  'elasticsearch']
    end
  end

  config.vm.define 'a-es-k' do |define| # a-es-5
    define.vm.provider :openstack do |provider, override|
      provider.image = 'ubuntu_pan_es_k_20161117053129'
      provider.flavor = 'n-rcd1.large'
      provider.server_name = "a-es-k-athornton"
      provider.security_groups = ['default', 'panopticon_site', 'remote SSH',
                                  'remote HTTP', 'remote https',
                                  'elasticsearch', 'logstash']
    end
  end

  config.vm.define 'a-es-6' do |define|
    define.vm.provider :openstack do |provider, override|
      provider.image = 'ubuntu_pan_es_20161117051135'
      provider.flavor = 'n-rd1.large'
      provider.server_name = "a-es-6-athornton"
      provider.security_groups = ['default', 'panopticon_site', 'remote SSH',
                                  'remote HTTP', 'remote https',
                                  'elasticsearch', 'logstash']
    end
  end

  config.vm.define 'a-lfr' do |define|
    define.vm.provider :openstack do |provider, override|
      provider.image = 'ubuntu_pan_lfr_20161117054440'
      provider.flavor = 'm4.large'
      provider.server_name = "a-lfr-athornton"
      provider.security_groups = ['default', 'panopticon_site', 'remote SSH',
                                  'elasticsearch', 'logstash']
    end
  end

  config.vm.provider :openstack do |os, override|
    os.sync_method        = 'none'
    os.user_data          = <<-EOS
#cloud-config
system_info:
  default_user:
    name: vagrant
    EOS
    os.username           = ENV['OS_USERNAME']
    os.password           = ENV['OS_PASSWORD']
    os.tenant_name        = ENV['OS_PROJECT_NAME']
    os.openstack_auth_url = ENV['OS_AUTH_URL']
    os.floating_ip_pool   = 'ext-net'
    os.networks           = ['5b8760e4-06ed-4f73-8c8d-bb1543b0bc74']
  end
end
