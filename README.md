# apache-virtual-host
Apache Virtual Host Settings On Ubuntu

#### 1 - nano editörü ile *.conf* dosyası oluşturup düzenlemek açıyoruz.
~~~ ssh
sudo nano /etc/apache2/sites-available/[site adresiniz].conf
~~~

#### 2 - oluşturduğumuz .conf dosyasına aşağıdaki kod bloğunu yapıştırıyoruz.
~~~ ssh
<VirtualHost *:80>
    ServerAdmin orhancelik@windowslive.com
    DocumentRoot /var/www/html/[proje klasörü]
    ServerName [site adresiniz]
    ServerAlias *.[site adresiniz]
    <Directory "/var/www/html/[proje klasörü]">
        AllowOverride All
        Require all granted
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
~~~

#### 3 - oluşturduğumuz .conf dosyasını apache ye bildiriyoruz.
~~~ ssh
sudo a2ensite [site adresiniz].conf
~~~

#### 3.1 - eğer isterseniz default ayarları pasif hale getirebilirsiniz. (zorunlu değil)
~~~ ssh
sudo a2dissite 000-default.conf
~~~

#### 4 - host dosyasını açıyoruz
~~~ ssh
sudo nano /etc/hosts
~~~

#### 5 - host dosyasına ilgili kaydı ekliyoruz
~~~ ssh
127.0.1.1 [site adresiniz]
~~~

#### 6 - ayarların geçerli olabilmesi için apache sunucusunu yeniden başlatıyoruz.
~~~ ssh
sudo systemctl reload apache2
~~~
