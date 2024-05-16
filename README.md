# tutorial11
1.  Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?
   
   Setelah di expose, service bisa menerima request. Request ini akan muncul di log dalam bentuk request GET yang akan bertambah setiap kali aplikasi di buka.
   
2. Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to `kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you explicitly created?

   Opsi -n merupakan panjangan dari namespace, dimana jika -n digunakan, informasi yang diambil datang dari namespace spesifik (untuk kali ini, namespace kube-system). Jika tidak menggunakan -n, informasi akan diambil secara default. Karena pods/services yang saya buat tidak ada di namespace kube-system, pods/servicesnya tidak muncul.

Reflection on Rolling Update & Kubernetes Manifest File
1. What is the difference between Rolling Update and Recreate deployment strategy?
Jika menggunakan Rolling Update, pod yang diupdate akan di update secara perlahan-lahan tanpa perlu diterminate. Sebalinknya, Recreate Deployment akan terminate pod yang akan di update, sehingga ada downtime yang tidak muncul saat menggunakan Rolling Update. 

2. Try deploying the Spring Petclinic REST using Recreate deployment strategy and document your attempt.
Dengan mengikuti referensi dari https://dev.to/cloudskills/kubernetes-deployment-strategy-recreate-3kgn, saya melihat yaml yang menerapkan Recreate deploys dan membandingkannya dengan yaml yang sudah dibuat. Setelah itu, saya menjalankan kubectl edit replicaset archetype untuk membuat perubahan itu dan mengikuti step lain paga bagian manual recreate deployment.

3. Prepare different manifest files for executing Recreate deployment strategy.
Lihat file deployment2.yaml

4. What do you think are the benefits of using Kubernetes manifest files? Recall your experience in deploying the app manually and compare it to your experience when deploying the same app by applying the manifest files (i.e., invoking kubectl apply -f command) to the cluster
Dengan menggunakan manifest file, proses deploy bisa dipercepat karena kondisi deployment langsung ada pada file dan tidak harus dimasukkan satu per satu. Selain itu, human error seperti salah ketik dan kelupaan tidak ada risiko untuk terjadi jika file manifest sudah benar.
