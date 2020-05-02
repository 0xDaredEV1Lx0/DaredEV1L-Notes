There is my first Solved Active Machine From Hack The Box ,Surely my First Write Up :) 

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

Oh yeaah here we are  , OpenNetAdmin provides a database managed inventory of your IP network. 














