# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "codem"

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get upgrade
    apt-get install -y language-pack-ja-base
    apt-get install -y language-pack-ja
    update-locale LANGUAGE=ja_JP.UTF-8 LC_ALL=ja_JP.UTF-8 LANG=ja_JP.UTF-8
    apt-get install -y fontforge
    cd /vagrant
    apt-get install -y unzip
    unzip 1.050R-it.zip
    unzip migu-1m-20150712.zip
    cp source-code-pro-2.030R-ro-1.050R-it/TTF/*.ttf .
    cp migu-1m-20150712/*.ttf .
    fontforge -script generate_CodeM.pe
    git clone https://github.com/Lokaltog/powerline-fontpatcher
    fontforge -lang=py -script ./powerline-fontpatcher/scripts/powerline-fontpatcher CodeM-Regular.ttf
    fontforge -lang=py -script ./powerline-fontpatcher/scripts/powerline-fontpatcher CodeM-Regular-Wide.ttf
    fontforge -lang=py -script ./powerline-fontpatcher/scripts/powerline-fontpatcher CodeM-Regular-Expanded.ttf
    fontforge -lang=py -script ./powerline-fontpatcher/scripts/powerline-fontpatcher CodeM-Bold.ttf
    fontforge -lang=py -script ./powerline-fontpatcher/scripts/powerline-fontpatcher CodeM-Bold-Wide.ttf
    fontforge -lang=py -script ./powerline-fontpatcher/scripts/powerline-fontpatcher CodeM-Bold-Expanded.ttf
    mkdir CodeM
    mv CodeM*ttf CodeM
    rm *.ttf
  SHELL
end
