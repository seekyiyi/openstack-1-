# openstack-1-

# OpenStack基本介紹
OpenStack是IaaS（基礎設施即服務）軟體，讓任何人都可以自行建立和提供雲端運算服務。
此外，OpenStack也用作建立防火牆內的「私有雲」（Private Cloud），提供機構或企業內各部門共享資源

## OpenStack Conceptual Architecture
![openstack](http://7xo6kd.com1.z0.glb.clouddn.com/upload-ueditor-image-20160331-1459396288164018195.jpg)

# openstack service

Nova：管理VM 的生命週期，是OpenStack 中最核心的服務。 
Neutron：為OpenStack 提供網絡連接服務，負責創建和管理L2、L3 網絡，為VM 提供虛擬網絡和物理網絡連接。 
Glance：管理VM 的啟動鏡像，Nova 創建VM 時將使用Glance 提供的鏡像。 
Cinder：為VM提供塊存儲服務。Cinder提供的每一個Volume在VM看來就是一塊虛擬硬盤，一般用作數據盤。
Swift：提供對象存儲服務。VM可以通過RESTful API存放對像數據。作為可選的方案，Glance可以將鏡像存放在Swift中；Cinder也可以將Volume備份到Swift中。
Keystone：為OpenStack 的各種服務提供認證和權限管理服務。簡單的說，OpenStack 上的每一個操作都必須通過Keystone 的審核。
Ceilometer：提供OpenStac k監控和計量服務，為報警、統計或計費提供數據。 
Horizon：為OpenStack 用戶提供一個Web 的自服務Portal。 

# Logical Architecture 
![openstack](http://7xo6kd.com1.z0.glb.clouddn.com/upload-ueditor-image-20160331-1459396289980075632.jpg)

# OpenStack架構圖及交互性

# 整體軟體架構圖

![openstack](https://farm6.staticflickr.com/5456/17612175358_ce88a63db0_z.jpg)

- Nova 運算套件 (Compute) 架構圖

![openstack](https://farm6.staticflickr.com/5449/17177502064_796c4331ac_z.jpg）
運算套件Nova：提供部署與管理虛擬機器的功能。

Nova 主要擔任著部署與管理虛擬機角色。
Nova提供了一套API來開發額外的應用程式，IT人員可以透過網頁介面來查看與管理資源狀態，且可以控制啟動、停止、調整虛擬機。

類似 Amazon AWS 的EC2。


- Swift 物件儲存套件 (Object Storage) 架構圖

![openstack](https://farm9.staticflickr.com/8864/17179640403_fd10cca4d2_z.jpg)
物件儲存套件Swift：是個分散式儲存平臺，可存放非結構化的資料

Swift套件提供可擴展的分散式儲存平臺，以防止單點故障的情況發生。
使用者可透過API進行存取，可存放非結構化的資料，像是圖片、網頁、網誌等，並可作為應用程式資料備份、歸檔以及保留之用。

透過Swift套件，可讓業界標準的設備存放PB等級的資料量。而且，當新增伺服器後，儲存群集可輕易的橫向擴充。

此外，因為Swift套件是透過軟體的邏輯，確保資料被複製與分布在不同設備上，這可讓企業使用較便宜的設備，節省成本。

類似 Amazon AWS 的 S3。

- Cinder 區塊儲存套件 (Block Storage) 架構圖

![openstack](https://farm6.staticflickr.com/5455/17179630023_a20295be35_z.jpg)
區塊儲存套件Cinder：提供區塊儲存容量，具有快照功能

Cinder套件允許區塊儲存設備能夠整合商業化的企業儲存平臺，像是NetApp、Nexenta、SolidFire等。
區塊儲存系統可讓IT人員設置伺服器和區塊儲存設備的各項指令，包括建立、連接和分離等，並整合了運算套件，可讓IT人員查看儲存設備的容量使用狀態。
Cinder套件並提供快照管理功能，可保護虛擬機器上的資料，作為系統回復時所用，快照甚至可用來建立一個新的區塊儲存容量。

類似 Amazon AWS 的 EBS。

- Quantum 架構圖
網通套件Quantum：透過API來管理的網路架構系統，支援多家網通廠商技術

![openstack](https://farm9.staticflickr.com/8833/17797234232_ca85a1f6ba_z.jpg)

- Keystone 架構圖

![openstack](https://farm8.staticflickr.com/7744/17800436291_c90789162c_z.jpg)

身分識別套件Keystone：提供了多種驗證方式，能查看哪位使用者可存取哪些服務

Keystone套件作為OpenStack的身份驗證服務，具有中央目錄能查看哪位使用者可存取哪些服務，並且提供了多種驗證方式，包括使用者帳號密碼、Token以及類似AWS的登入機制。另外，Keystone可以整合現有的中央控管系統，像是LDAP（輕型目錄訪問協議）。

類似 Amazon AWS 的 IAM。

- Glance 架構圖

![openstack](https://farm8.staticflickr.com/7737/17800436561_c3c59d0911_z.jpg)
映象檔管理套件Glance：提供映象檔尋找、註冊以及服務交付等功能

Glance套件提供了硬碟或伺服器的Image尋找、註冊以及服務交付等功能。
儲存的Image可作為新伺服器部署所需的範本，加快服務上線速度。若是有多臺伺服器需要配置新服務，就不需要額外花費時間單獨設定，也可做為備份時所用。

類似 Amazon AWS 的 VM Import／Export。

- Keystone 身分識別套件 (Identity service)

![openstack](https://farm8.staticflickr.com/7696/17797228942_a2b4de7e05_z.jpg)
Keystone套件作為OpenStack的身份驗證服務，具有中央目錄能查看哪位使用者可存取哪些服務，並且提供了多種驗證方式，包括使用者帳號密碼、Token以及類似AWS的登入機制。另外，Keystone可以整合現有的中央控管系統，像是LDAP（輕型目錄訪問協議）。

類似 Amazon AWS 的 IAM。

# Nova 創建虛擬機器流程
這個流程就在解釋著在Openstack建立一個虛擬機器所需的步驟
http://ilearnstack.com/2013/04/26/request-flow-for-provisioning-instance-in-openstack/comment-page-1/
![openstack](https://farm6.staticflickr.com/5322/17773702256_148740f4e1_z.jpg)


參考資料 | 
- https://goo.gl/DhFpBG
- https://goo.gl/VRuptw
