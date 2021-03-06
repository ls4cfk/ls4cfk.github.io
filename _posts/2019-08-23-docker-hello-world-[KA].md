# Docker - Hello world

![](img/1__GU8Zdm__oyCWhxSmDNguxbA.jpeg)

ავტორები: [Aleksi Kistauri](https://medium.com/u/c0fbcc820d6d), [Nikoloz Bokeria](https://medium.com/u/6498150f0037)

### რა არის დოკერი?

  

შენ ალბათ უკვე გაგიგია დოკერის შესახებ და გიფიქრია, თუ რაში შეიძლებოდა გამოგეყენებინა ის. ამ სტატიაში, სწორედ ამ კითხვაზე გაგცემთ პასუხს.

დოკერი არის **კონტეინერიზაციის** პლატფორმა (Runtime environmet), რომელიც გაძლევს საშუალებას, აპლიკაციისთვის შექმნა იზოლირებული გარემო, სადაც აპლიკაციასთან ერთად თავს მოუყრი მის მოდულებს(**dependencies**), კონფიგურაციის ფაილებს და ა.შ. რომლებიც საჭიროა აღნიშნული აპლიკაციის გასაშვებად.

დოკერი ასევე შეიძლება გამოიყენო მაშინ, როდესაც გინდა აპლიკაციის გაშვება უკვე არსებულ გარემოში, რამაც შეიძლება გამოიწვიოს კონფლიქტი.

მაგალითად გაქვს სერვერი, სადაც გაშვებულია აპლიკაცია, რომელიც იყენებს **Node 6** ვერსიას, მაგრამ გინდა გაუშვა ახალი აპლიკაცია - იგივე სერვერზე, **Node 12** ვერსიით. კონტეინერიზაციის შემთხვევაში, თითოეულ აპლიკაციას ექნება იზოლირებული გარემო, შესაბამისად სხვა და სხვა **Node**\-ის ვერსიაც, რაც არ დაუშვებს ვერსიათა კონფლიქტს.

### რა არის კონტეინერი?

![](img/1__bOrphmm1BtsoUc9rND7lmw.png)

როგორც უკვე ავღნიშნეთ, კონტეინერი არის იზოლირებული გარემო, რომლისთვისაც კომპიუტერი გამოყოფს შესაბამის რესურსებს (**Network, hardware …**)

შესაძლოა მანქანაზე იყოს გაშვებული ბევრი კონტეინერი, სხვა და სხვა აპლიკაციებით. რომელთა ცვლილება არ აისახება სხვა კონტეინერებზე.

![](img/1__UEmLmenrxKp0Hwid4xxGwQ.png)

### **დოკერი არ არის ვირტუალური მანქანა !**

  

![](img/1__8rLp2Zg1d3ablZg0MOPQag.png)

ვირტუალური მანქანისგან განსხვავებით, კონტეინერი, არ საჭიროებს მისთვის გამოყოფილ ოპერაციულ სისტემას. ის იყენებს კერნელის ფუნქციონალს და გააჩნია საკუთარი **_namespace_** (გამოყოფილი რესური) რაც ნიშნავს იმას, რომ **Network**, **Memory** და ა.შ.გამოყოფს პატარა ნაწილს კონტეინერისთვის.

### დოკერის ინსტალაცია

> თუ შენ იყენებ **OS X**\-ს ან **Windows**\-ს დოკერი ავტომატურად დააინსტალირებს **Linux**\-ის ვირტუალურ მანქანას.

**OS X** -ზე დასაყენებლად გვაქვს ორი ვარიანტი:

1.  **Homebrew** — ის გამოყენებით, რომელიც ცოტა კომპლექსური პროცედურაა, რადგან ხელით გვიწევს ვირტუალური მანქანის დაყენება და კონფიგურაცია. [installation docker with homebrew](https://medium.com/@yutafujii_59175/a-complete-one-by-one-guide-to-install-docker-on-your-mac-os-using-homebrew-e818eb4cfc3)
2.  შეგიძლია ჩამოტვირთო **DMG**\- ფაილი და დააყენო როგორც აპლიკაცია — [https://docs.docker.com/docker-for-mac/install/](https://docs.docker.com/docker-for-mac/install/)

**Linux (Debian)**

sudo apt update

sudo apt install apt-transport-https ca-certificates curl software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb \[arch=amd64\] https://download.docker.com/linux/ubuntu bionic stable"

sudo apt update

apt-cache policy docker-ce

sudo apt install docker-ce

**Windows** 

**Windows**\-ის შემთხვევაში დოკერის ინსტალაცია შესაძლებელია მხოლოდ შემდეგ ვერსიებზე: **Windows 10 64-bit: Pro, Enterprise, ან Education (Build 15063).**

.**EXE** ფაილის ჩამოტვირთვა შესაძლებელია ლინკიდან — [https://hub.docker.com/?overlay=onboarding](https://hub.docker.com/?overlay=onboarding)

**შევამოწმოთ დაყენდა თუ არა დოკერი:**

\# გახსენი **CMD** ან **Terminal**\-ი და გაუშვი:

docker -v

![](img/1__K6Xdw5C08UPVHXeoA74__Tg.png)

### Get hands dirty !

  

გავუშვათ პირველი **Docker** **image**

docker run hello-world

![](img/1__knvXxjVSRrurkDajz9nOxg.png)

როდესაც გაუშვებ ამ **Command**\-ს, დოკერი თავდაპირველად შეამოწმებს არის თუ არა აღნიშნული **_image_** ლოკალურად.

ჩვენ შემთხვევაში, **hello-world** ის **image** არ გვაქვს, ამიტომ ვიღებთ შეტყობინებას :

> **Unable to find image ‘hello-world:latest’ locally**

დოკერი ავტომატურად ჩამოტვირთავს [**hub.docker.com**](https://hub.docker.com/) — იდან ჩვენს **image**\-ს.

[**Docker Hub **](https://hub.docker.com)—  არის **Docker**\-ის სერვისი, სადაც განთავსებულია სხვა და სხვა კონტეინერების **image**\-ები (**image**\- ზე მოგვიანებით ვილაპარაკოთ) 

**Docker Hub** \- ზე შეგვიძლია ავტვირთოთ საკუთარი **Image**\-ები ან გამოვიყენოთ უკვე ატვირთული **Image**\-ები როგორიცაა: **Ngnix**, **Node**, **Redis** და ა.შ.

როდესაც **Image** ჩამოიტვირთება გაეშვება კონტეინერი, რომელიც გამოიტანს ეკრანზე შემდეგ შეტყობინებას:

![](img/1__EHkzaY____rq4pNgreaeE4Yw.png)

### პრაქტიკული მაგალითი

  

**Image** ებისა და კონტეინერების უკეთესად გასაგებად, განვიხილოთ პრაქტიკული მაგილითი.

შევქმნათ **Node**\-ის აპლიკაცია, რომელიც უბრალოდ დაგვიბრუნებს **Hello from container!** \- ს.

> [**https://github.com/nikolozz/docker\_simple\_app**](https://github.com/nikolozz/docker_simple_app)

![https://github.com/nikolozz/docker_simple_app](https://cdn-images-1.medium.com/max/1200/1*UfAMo1xBr-dg0I6xc1xRbw.png)

იმისათვის, რომ აპლიკაცია გავუშვათ საჭიროა კონტეინერის **Image**. 

**Image**\-ის შესაქმნელათ ვწერთ **Dockerfile**\-ს(**root** ფოლდერში) სადაც უნდა ავღწეროთ პროცესი, თუ როგორ უნდა შეიქმნას ჩვენი აპლიკაცია.

![](img/1__USukYA__4y8ZMmPChCgqdIw.png)

  

> Dockerfile — ს არ ჭირდება არანაირი გაფართოება (**.txt, .js, .sh** …)

![](img/1__bQqFa5R__16R4yaEvuaMwkw.png)

FROM node:alpine

**FROM** — ის მეშვეობით განვსაზღვრავთ **base image**\-ს, რადგან ჩვენი აპლიკაცია არის **Node**\-ზე **base image**\-ად ვიყენებთ [node:alpine](https://hub.docker.com/_/node/) -ს.

რადგან აქ უკვე დაყენებულია **npm** და **Node.js**, მაგალითად თუ **base** **image**\-ად განვსაზღვრავდით **Ubuntu**\-ს, ხელით მოგვიწევდა **Node**\-ისა და **npm** ის დაყენება.

ასევე, **Ubuntu** -ს **base image 1GB**\-ზე მეტია, ხოლო **node:alpine** 80 **MB**

WORKDIR /app

თუ შევალთ კონტეინერში და ვნახავთ ფაილებს, შევამჩნევთ ლინუქსის ფაილურ სტრუქტურას, რადგან **base image** ად **node:alpine**\- გვაქვს გამოყენებული.

> ფაილური სტრუქტურა დამოკიდებულია **base image**\-ზე

აღნიშნული **Command** შექმნის ფოლდერს სახელად **app**, სადაც იქნება ჩვენი აპლიკაციის ფაილები.

![](img/1__rNbP9zxwgAjSn2vZG7F5GQ.png)

COPY ./package.json ./  
RUN npm i  
COPY . .

**COPY** გვაძლევს საშუალებას გადავიტანოთ ლოკალური ფაილები კონტეინერში. ამ შემთხვევაში გადაგვაქვს **package.json**, სადაც გვაქვს **Dependency** ები, რომლებსაც შემდეგ ვაყენებთ **npm i **— ით (**npm install**)

**RUN** ის გამოყენებით შეგვიძლია გავუშვათ ნებისმიერი **Command**, მაგალითად **npm**

**npm** — უნდა იყოს **base image** ში.

რის შემდეგაც ვაკოპირებთ ყველა ფაილს კონტეინერში.

> იმისათვის, რომ **node\_modules** არ დაკოპირდეს კონტეინერში, ვქმნით .**dockerignore**\-ს და ვწერთ **node\_modules**/ -ს 

![](img/1__urjtRGp3WH__6ICxGTWgvPQ.png)

  

CMD \[ "npm", "start" \]

**CMD** -ის გამოყენებით განვსაზღვრავთ **Command**\-ს, რომელიც გაეშვება კონტეინერის დასტარტვის დროს.

ჩვენ დავწერეთ **Dockerfile**, რის მიხედვითაც შევქმნით **image**\-ს და გავუშვებთ ჩვენ აპლიკაციას.

![](img/1__1ADybfejRF4UGrdNZciQnA.png)

იმისათვის რომ დავბილდოთ **Image**, გადავდივართ იმ დირექტორიაში სადაც **Dockerfile** არის განთავსებული და ვუშვებთ შემდეგ **Command**\-ს

docker build -t myapp .

![](img/1__WEgv59nsYwPR82673j1aVQ.png)

**docker build**\- ს პარამეტრად შეგვიძლია გადავცეთ **\-t** (**tag**), რაც იქნება ჩვენი **Image**\-ის სახელი, თუ არ გადავცემთ **tag name** -ს დოკერი ავტომატურად მიანიჭებს რენდომ **tag name**\-ს.

ასევე, ბოლოში აუცილებლად ვწერთ წერტილს(**.**)-ს რაც განსაზღვრავს კონტექსტს..

![](img/1__YTR1Jjs2RnimDAzR5NQ5Ww.png)

თუ გავუშვებთ **Command**\-ს

docker images

 ვნახავთ რომ შეიქმნა ორი ახალი **image** - **myapp** და **node**(რადგან უკვე დაყენებული მქონდა, ქეშიდან აიღო)

იმისათვის, რომ კონტეინერი გავუშვათ ვიყენებთ **Command**\-ს:

docker run myapp **#**(სადაც myapp თქვენი image-ს სახელია).

![](img/1__u__iO6vnzpL2ODOpp805nHw.png)

გაშვებული კონტეინერების სანახავად ვუშვებთ **Command**\-ს:

docker ps

თუ ჩვენ შევეცდებით **localhost:8000**\-ზე შესვლას გვიჩვენებს **Network error**\-ს რადგან როგორც უკვე ვახსენეთ, კონტეინერი არის იზოლირებულ გარემოში.

![](img/1__ToIhNQWopIDnXdgsfcHgew.png)

იმისათვის, რომ დავამყაროთ კონტეინერთან კავშირი უნდა გავხსნათ პორტი.

რისთვისაც **docker run** ს უნდა გადავცეთ დამატებით პარამეტრი **\-p 8000:8000**

რაც ნიშნავს იმას, რომ **8000** პორტიდან ვუკავშირდებით კონტეინერის **8000** პორტს.

docker run -p 8000:8000 myapp

![](img/1__Jnh0RyutyVPVnCuqxAGe0A.png)

პორტის მითითების შემდეგ დავინახავთ, რომ კონტეინერს მიენიჭა პორტი და შეგვიძლია ჩვენი აპლიკაცია გავხსნათ.

![](img/1__tRvPIyp3RNgdX__rbkVCQ0w.png)

  

### და მაინც, რატომ დოკერი? 🤔

  

დოკერმა დეველოპმენტ პროცესებში ძალიან ბევრი რამ შეცვალა, მან ბევრად უფრო გაამარტივა დეპლოიმენტი. 

დღესდღეობით ძალიან ბევრი სერვისი (**AWS ECS, AWS EKS, AWS Elastic beanstallk, GKE** და ა.შ.)არსებობს, რომლებშიც შეგვიძლია ავტვირთოთ, ჩვენი კონტეინერები და მარტივად მოვაგვაროთ ისეთი პრობლემა როგორიცაა სქეილინგი. 

რაც ნიშნავს იმას, რომ აპლიკაციის დატვირთვის ზრდასთან ერთად მარტივად შეგვიძლია დავსტარტოთ დამატებითი კონტეინერები.

