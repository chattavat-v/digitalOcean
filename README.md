# DigitalOcean

## deploy (How to ?)

### DROPLETS - [CREATE]
  - Droplets - deploy server (Node.JS)
  - Click Create -> choose droplets
  - เข้าไปที่ marketplace -> เลือก Node.JS
  - กด create node.js droplet
  - กลับมายังหน้าหลัก (Redirect) 
    - เลือก spec (ขั้นต่ำ 5$)
    - region เลือก singapore
    - select additional option 
      - private networkng
      - IPv6
      - Monitoring
      - Authentication ให้สร้าง ssh key ถ้ามีอยู่แล้วกดเลือกได้ ถ้ายังไม่มีให้สร้าง กด new SSH key
      - Filnalize Droplet - choose hosting name เราเปลี่ยนชื่อได้
      - Add tag สร้างชื่อแทค สำหรับ ใช้ในการค้นหาหรือทำ load balancer
      - create droplet

### DROPLETS - [Connect Droplets with SSH]
  - link https://www.digitalocean.com/docs/droplets/how-to/connect-with-ssh/
  - copy ip node.js droplets ที่สร้างขึ้นมา
  - เข้า terminal พิมพ์ ssh root@192.169.2.2
  - เอา project ที่สร้างมาโยนใส่
  - เข้า project ที่สร้างมา ทำการ npm install 
  - set port firewall 
  - run server 

## SSH key การสร้าง
  - link https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2
  - open terminal
  - พิมพ์ cd ~./ssh
  - ls หา id_rsa.pub
  - ถ้าไม่มี ให้พิมพ์ ssh-keygen -t rsa
  - กรอกว่า id_rsa
  - ลอง ls อีกครั้งเพื่อ check ว่ามี id_rsa.pub ไหม
  - ถ้ามีให้เข้าไปยัง file ด้วย cat id_rsa.pub
  - copy key -> ทั้งหมด ssh-rsa.......
  - เอา key ไปใช้งานได้เลย

## Set up fire wall
  - link https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-18-04
  - ufw status แสดงค่า port ทั้งหมดที่ set up ไว้
  - ufw allow 3000/tcp กำหนด port project ที่ใช้งาน
  - ufw reload ทำการ reload fire wall
  - ufw enable
  - ufw delete [number] port ที่เราจะลบ