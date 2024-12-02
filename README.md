# Install-MiniO-on-Ubuntu
# ➖➖➖➖➖➖ 🌟 Install MiniO on Ubuntu 🌟 ➖➖➖➖➖➖
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
    go version
    rm go1.23.3.linux-amd64.tar.gz
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
    cd ~
    wget https://dl.min.io/server/minio/release/linux-amd64/minio
    
    sudo useradd --system minio --shell /sbin/nologin  ///kreiranje sistemskog korisnika, naziv korisnika minio
    sudo usermod -L minio  ///zaključava korisnički nalog minio na Linux sistemu, opcija -L (skraćeno od lock) modifikuje korisnički nalog tako da korisnik ne može da se prijavi koristeći svoju lozinku
    sudo chage -E0 minio   ///postavlja datum isteka korisničkog naloga minio na trenutni datum
    
    sudo mv minio /usr/local/bin
    sudo chmod +x /usr/local/bin/minio
    sudo chown minio:minio /usr/local/bin/minio

    sudo touch /etc/default/minio
    echo 'MINIO_ACCESS_KEY="minio"' | sudo tee -a /etc/default/minio
    sudo echo 'MINIO_VOLUMES="/usr/local/share/minio/"' | sudo tee -a /etc/default/minio
    echo 'MINIO_OPTS="-C /etc/minio --address :9000"' | sudo tee -a /etc/default/minio
    echo 'MINIO_SECRET_KEY="miniostorage"' | sudo tee -a /etc/default/minio

    
    sudo mkdir /usr/local/share/minio
    sudo mkdir /etc/minio

    
    sudo chown minio:minio /usr/local/share/minio
    sudo chown minio:minio /etc/minio

    cd ~

    ======================now we are going to set ap a service======================
    wget https://raw.githubusercontent.com/minio/minio-service/master/linux-systemd/minio.service
    sudo vi minio.service and chande user and group from minio-user to minio !

    sudo mv minio.service /etc/systemd/system
    
    sudo systemctl daemon-reload
    sudo systemctl enable minio
    sudo systemctl start minio

    sudo systemctl status minio

    cd ~
