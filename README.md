# tutorial11
1.  Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?
   
   Setelah di expose, service bisa menerima request. Request ini akan muncul di log dalam bentuk request GET yang akan bertambah setiap kali aplikasi di buka.
   
2. Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to `kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you explicitly created?

   Opsi -n merupakan panjangan dari namespace, dimana jika -n digunakan, informasi yang diambil datang dari namespace spesifik (untuk kali ini, namespace kube-system). Jika tidak menggunakan -n, informasi akan diambil secara default. Karena pods/services yang saya buat tidak ada di namespace kube-system, pods/servicesnya tidak muncul.
