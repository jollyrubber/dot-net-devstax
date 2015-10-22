# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

    # you can build this with https://github.com/jollyrubber/windows2012r2-packer
    config.vm.box = "windows2012r2"

    config.omnibus.chef_version = :latest
    config.berkshelf.enabled = true

    config.vm.provider "virtualbox" do |v|
        #v.gui = true
        v.memory = 4096
        v.cpus = 2
    end

    # shared folders
    local_packages = File.directory?("./local-packages")
    if local_packages
        config.vm.synced_folder "./local-packages", "/packages", :mount_options => ["ro"] # pre-downloaded software packages
    end

    config.vm.provision "chef_solo" do |chef|

        chef.log_level = :info
        chef.json = {
            "chef-devstax" => {
                :visualstudio => {
                    "2015" => {
                        :professional => {
                            :iso => {
                                :url => "file:///packages/vs2015.pro_enu.iso"
                                }
                            }
                        }
                    }
                },
            "chocolatey-installer" => {
                :packages => [
                    "7zip",
                    "tortoisegit",
                    "googlechrome",
                    "chocolateygui"
                    ]
                },
            :windows => {
                :reboot_timeout => 10
                }
            }

        chef.add_recipe "windows"
        chef.add_recipe "windows::reboot_handler"
        chef.add_recipe "iis"
        chef.add_recipe "iis::mod_aspnet45"
        chef.add_recipe "chef-devstax::visualstudio"
        chef.add_recipe "chocolatey-installer"
    end
end
