# Install-MiniO-on-Ubuntu
Install MiniO on Ubuntu
MiniO is s3 compatible API program
Minio is simpe easy, its writen in go, you can install on your own servers and produce
your own s3 buckets to store your data.
If we use a peace of software for your backup solutions that is capable takling to s3, then 
we can use Minio
We can use Minio over S3 because of cost, maybe we need to store data locally, like we have some
restrictions

    wget -c https://go.dev/dl/go1.23.3.linux-amd64.tar.gz
    tar xvf go1.23.3.linux-amd64.tar.gz
    sudo chown -R root:root ./go
    sudo mv go /usr/local ///Ovo je standardna lokacija za instalaciju softvera koji nije deo sistema
    echo 'export PATH=$PATH:/usr/local/go/bin' | sudo tee -a /etc/profile ///Dodaje liniju:export PATH=$PATH:/usr/local/go/bin
    source /etc/profile  ///učitava sve promene napravljene u fajlu /etc/profile


