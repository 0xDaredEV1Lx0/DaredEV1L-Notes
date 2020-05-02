There is my first Solved Active Machine From Hack The Box ,Surely my First Write Up :) 

OpenAdmin Retired today 2-5-2020 , and it was awesome box to do for me ;)

So Lets Jump in it ,Have Fun

IP for this Easy Linux Box : 10.10.10.171

First of all, i used nmap to check open ports and services

![01](https://user-images.githubusercontent.com/43730847/80852285-6078cf80-8bf5-11ea-999b-8314b529c011.png)

I got SSH on 22 , HTTP on 80 .... and thats made me happy cuze i think that would be an EZ PZ BOX :) 

I Checked http://10.10.10.171/ , and i got that

![02](https://user-images.githubusercontent.com/43730847/80852943-bd2ab900-8bfa-11ea-9926-0abdc629f0b7.png)

just an Apache Default Page 

I run GOBUSTER TO Check another Directories 

Got http://10.10.10.171/artwork/

![03](https://user-images.githubusercontent.com/43730847/80853169-7473ff80-8bfc-11ea-912c-30533ce5a28c.png)

After 2 minutes in this site , i realized that's Not useful at all ....

and also i got http://10.10.10.171/ona/ from GOBUSTER .. I hurried to open it & got that ^0^

![04](https://user-images.githubusercontent.com/43730847/80853353-16e0b280-8bfe-11ea-88d5-1bb64fc0f575.png)





Oh yeaah here we are  , OpenNetAdmin provides a database managed inventory of your IP network , and this version is v18.1.1 ... 
I asked GooGle if its Vurnalble or not  , amriunix told me there was a Vurnable published on 18-1-2020 and gave me this one
https://github.com/amriunix/ona-rce/blob/master/ona-rce.py , its Remote Code Execution vulnerability written in python3
to get shell in BOX, I tried it and its WORKED <3 
 

![05](https://user-images.githubusercontent.com/43730847/80854881-96c04a00-8c09-11ea-9d95-62db27f899e5.png)

Then 

![06](https://user-images.githubusercontent.com/43730847/80854940-3087f700-8c0a-11ea-9663-2427abdacd37.png)

i cat .htaccess.example hope to find something 

![07](https://user-images.githubusercontent.com/43730847/80855440-42b86400-8c0f-11ea-8d50-57db3bed73bf.png)

but no thing useful here , i think that i known it worked on 127.0.0.1 as localhost 

i spent alot Enumerating and Finally i found that 

![08](https://user-images.githubusercontent.com/43730847/80855539-f3befe80-8c0f-11ea-8950-113f9a9e018b.png)

"'db_passwd' => 'n1nj4W4rri0R!'" more interesting .... what can i do with this .. i had to find users to log with 
this password XD 

SO, i tried $ cat /etc/passwd .. & got  

![09](https://user-images.githubusercontent.com/43730847/80855642-d63e6480-8c10-11ea-80b7-2ec59d7a8fe3.png)

After i grep all "no login" and deleted all thats lines,i loved joanna so i will SSH with her first  

![10](https://user-images.githubusercontent.com/43730847/80855797-09352800-8c12-11ea-930d-abe009209149.png)

OH WHAT O_- , i cant access with her :( ... oops that means 'jimmy' not important in this network and 'joanna'has more 
permissions , thats not make sense for me .. i think the Machine maker is Fiminist one :) or he love his girl more than his boy ..... Doesn't Matter it is just my overthinking 

![11](https://user-images.githubusercontent.com/43730847/80855926-667da900-8c13-11ea-8786-80f130768bd7.png)

I  got access with little 'jimmy'

lets see what we can do with JIMMY...

After much time of enumerating and enumerating with jimmy i found that ...

![13](https://user-images.githubusercontent.com/43730847/80856604-536dd780-8c19-11ea-9d90-3433403a1594.png)

NICE .. its PHP script if we Execute it we can get "id_rsa" ,So how we can execute it .. we need a localhoat and it was 
127.0.0.1 and Which port is listening by the way it is 52846 listening on that localhost ,i used $netstat -tunlp to know

another thing i noted that header says "dont forget your 'ninja' password" !!!!!

lets Execute our PHP Script ;)

![14](https://user-images.githubusercontent.com/43730847/80856772-d2afdb00-8c1a-11ea-970f-9a8d2b7fcc77.png)

mmmmmmm now we have to HASH this PRIVATE KEY then CRACK it to get the ninja PASSWORD XD 

i used ssh2john to HASH it and john to CRACK it, its JohnTheRipper tool https://github.com/magnumripper/JohnTheRipper

![12](https://user-images.githubusercontent.com/43730847/80857075-36d39e80-8c1d-11ea-967a-3e2c77f77528.png)
 
 HASHED
 
![15](https://user-images.githubusercontent.com/43730847/80857202-469fb280-8c1e-11ea-891a-ed85f13f19d3.png)

 CRACKED and the PASSWORD is  'bloodninjas' <3 <3 
 
 NOW lets SSH login  with id_rsa for Joanna ... NoTe : I had to chmod 600 id_rsa First to protect this SSH KEY  
 
 ![16](https://user-images.githubusercontent.com/43730847/80857297-245a6480-8c1f-11ea-866a-22ee76b607e8.png)

WOW i got access with joanna and got user FLAG :) 

LETS DO some Privilige Escalation to get some of root permissions in this Machine

![17](https://user-images.githubusercontent.com/43730847/80858252-46a3b080-8c26-11ea-9d63-337fbcd49f40.png)

Now we have to $ sudo nano /opt/priv 

Then .. you need to ctrl R to Write /root/root.txt 

![21](https://user-images.githubusercontent.com/43730847/80858305-9edab280-8c26-11ea-868c-aad304b6de25.png)

![22](https://user-images.githubusercontent.com/43730847/80858319-ae59fb80-8c26-11ea-94e3-5b28b9c99c0f.png)

AND we GOT ROOT FLAG 

That was AWESOME MACHINE <3 


















































