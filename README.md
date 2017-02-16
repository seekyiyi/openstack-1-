# openstack-1-

# OpenStack基本介紹
OpenStack是IaaS（基礎設施即服務）軟體，讓任何人都可以自行建立和提供雲端運算服務。
此外，OpenStack也用作建立防火牆內的「私有雲」（Private Cloud），提供機構或企業內各部門共享資源

## OpenStack Conceptual Architecture
[openstack](http://7xo6kd.com1.z0.glb.clouddn.com/upload-ueditor-image-20160331-1459396288164018195.jpg)

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
[openstack](http://7xo6kd.com1.z0.glb.clouddn.com/upload-ueditor-image-20160331-1459396289980075632.jpg)

# OpenStack架構圖及交互性

# 整體軟體架構圖

[openstack](http://www.flickr.com/photos/132122145@N02/17612175358)

- Nova 架構圖
運算套件Nova：提供部署與管理虛擬機器的功能。

Nova 主要擔任著部署與管理虛擬機角色。
Nova提供了一套API來開發額外的應用程式，IT人員可以透過網頁介面來查看與管理資源狀態，且可以控制啟動、停止、調整虛擬機。

[openstack](http://www.flickr.com/photos/132122145@N02/17177502064)

- Swift 架構圖
物件儲存套件Swift：是個分散式儲存平臺，可存放非結構化的資料

Swift套件提供可擴展的分散式儲存平臺，以防止單點故障的情況發生。
使用者可透過API進行存取，可存放非結構化的資料，像是圖片、網頁、網誌等，並可作為應用程式資料備份、歸檔以及保留之用。

[openstack](http://www.flickr.com/photos/132122145@N02/17179640403)

- Cinder 架構圖
區塊儲存套件Cinder：提供區塊儲存容量，具有快照功能

Cinder套件允許區塊儲存設備能夠整合商業化的企業儲存平臺，像是NetApp、Nexenta、SolidFire等。
區塊儲存系統可讓IT人員設置伺服器和區塊儲存設備的各項指令，包括建立、連接和分離等，並整合了運算套件，可讓IT人員查看儲存設備的容量使用狀態。
Cinder套件並提供快照管理功能，可保護虛擬機器上的資料，作為系統回復時所用，快照甚至可用來建立一個新的區塊儲存容量。

[openstack](http://www.flickr.com/photos/132122145@N02/17179630023)

- Quantum 架構圖
網通套件Quantum：透過API來管理的網路架構系統，支援多家網通廠商技術
[openstack](http://www.flickr.com/photos/132122145@N02/17797234232)

- Keystone 架構圖
身分識別套件Keystone：提供了多種驗證方式，能查看哪位使用者可存取哪些服務
[openstack](http://www.flickr.com/photos/132122145@N02/17800436291)

- Glance 架構圖
映象檔管理套件Glance：提供映象檔尋找、註冊以及服務交付等功能
[openstack](http://www.flickr.com/photos/132122145@N02/17800436561)

參考資料 | 
- https://goo.gl/DhFpBG
- 
