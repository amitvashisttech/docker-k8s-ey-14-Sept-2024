 1189  mkdir 12-Helm-Custom-Charts
 1190  ls
 1191  cd 12-Helm-Custom-Charts/
 1192  ls
 1193  helm create my-tiny-web
 1194  ls
 1195  apt-get install tree -y
 1196  tree .
 1197  s
 1198  ls
 1199  cd my-tiny-web/
 1200  ls
 1201  cat Chart.yaml
 1202  ls
 1203  vim values.yaml
 1204  ls
 1205  cd ..
 1206  ls
 1207  helm install my-web my-tiny-web --dry-run
 1208  helm install my-web my-tiny-web
 1209  helm list
 1210  kubectl  get po
 1211  kubectl  get svc
 1212  ls
 1213  mkdir v1
 1214  ls
 1215  mv my-tiny-web v1/
 1216  ls
 1217  cp -rf v1 v2
 1218  ls
 1219  cd v2/
 1220  ls
 1221  cd my-tiny-web/
 1222  ls
 1223  vim Chart.yaml
 1224  ls
 1225  vim values.yaml
 1226  s
 1227  cd ..
 1228  ls
 1229  helm upgarde my-web my-tiny-web --dry-run
 1230  helm upgarde my-web my-tiny-web
 1231  helm upgrade my-web my-tiny-web/
 1232  helm list
 1233  kubectl  get po
 1234  kubectl  get svc
 1235  kubectl  get no -o wide
 1236  curl 10.4.0.140:30872
 1244  cp -rf v2 v3
 1245  cd v3/
 1246  ls
 1247  vi my-tiny-web/values.yaml
 1248  ls
 1249  vim my-tiny-web/Chart.yaml
 1250  helm upgrade my-web my-tiny-web/
 1251  helm list
 1252  kubectl  get po
 1253  kubectl  get svc
 1254  curl 10.4.0.140:30872
 1255  helm list
 1256  helm history my-web
 1257  helm rollback my-web
 1258  helm history my-web
 1259  kubectl  get po
 1260  curl 10.4.0.140:30872
 1261  helm rollback my-web
 1262  helm history my-web
 1263  kubectl  get po
 1264  curl 10.4.0.140:30872
 1265  helm rollback my-web  1
 1266  helm history my-web
 1267  kubectl  get po
 1268  kubectl  get svc
 1269  curl 10.4.0.140:30872

