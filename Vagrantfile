Vagrant::Config.run do |config|

  IP_BASE = "192.168.33"
  ip_start = (ENV['IP_START'] || "70").to_i
  boxes = (ENV['BOXES'] || "1").to_i

  (1..boxes).each do | box_num |
    config.vm.define "box#{box_num}".to_sym do | box |
      box.vm.box = "precise64"
      box.vm.box_url = "http://files.vagrantup.com/precise64.box"
      box.vm.network :hostonly, "#{IP_BASE}.#{ip_start + (box_num - 1)}"
      box.vm.provision :shell, :inline => 'grep -c "vm\.overcommit_memory = 1" /etc/sysctl.conf || sudo echo "vm.overcommit_memory = 1" >> /etc/sysctl.conf && sudo sysctl -p'
    end
  end
end

