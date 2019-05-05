# CCNA/Ethernet

layer 1 實體層:線路基礎

layer 2 網路層:路由和尋址的功能，有一定的擁塞控制和流量控制的能力

* Virtual LAN (VLAN) 虛擬區域網絡
	* Trunk Link設定:VLAN ID,VLAN Tag
	* Allowed VLAN:我們可以設定 Trunk Link 只讓特定的 VLAN 通過
	* Native VLAN 預設VLAN ex:VLAN1

* Spanning Tree Protocol生成樹協議(switch):
	為防止Broadcast Storm，switch間協調，建立Loop-free。Root Switch(Priority 最小),PVST+,Root Switch(Priority=Priority(MAC)+VLAN Number 最小),

	* Root Port(Root Switch以外,Bandwidth cost 最小),Designated Port(同root port，but Root Port 較優先) 
	
    * Bridge Protocol Data Unit (BPDU) 是 Switch 間用來傳送 STP 資訊的 Frame:Disabled,Blocking,Listening,Learning,Forwarding，變更狀態要很久
	
    * Topology Change:因為要等很久，所以有PortFast,UplinkFast,BackboneFast
	
    * MSTP:Spanning Tree 的終極版
	
    * 保護 STP Topology:Root Switch 的角色不可被新加的 Switch 搶去，所以要保護
* ARP(Address Resolution Protocol):ARP Table,Proxy ARP(預設開啟)
* EtherChannel:提高 Bandwidth,Redundancy (冗餘) PAgP,LACP,LOAD balence(小心port ID 相衝)
* 要連接不同品牌 Router 的 Serial Interface，就必需使用 PPP Point-to-Point Protocol
* Internet Group Management Protocol (Router) 網際網路組管理協定
	* IGMP 的作用就是 Host 和 Router 之間溝通的語言，透過使用 IGMP，Router 可以知道那些 Host 需要什麼 Multicast Group，其最大的好處在於節省整個網路的頻寬。
	* IGMP Querier:同一網段中只有一隻 Router 被選為 IGMP Querier
	* IGMP Filtering:可以用 access-list 控制 Router 只接受或不接受某些 Multicast Group，
	* IGMP Version 3:支援 Source Specific Multicast (SSM)，讓 Host 可以選擇接收特定  Source Address 的 Multicast Traffic(PIM相關)
	* IGMP Snooping: Snooping Table。解決在 Router 與 Client 之間加入一隻 Switch產生的問題

layer 3 應用層:直接和應用程式介面結合並提供常見的網路應用服務，封包資料相關

* Protocol Independent Multicast (Switch) 獨立組播協定
	* PIM 用了 RPF checking 的技術，在 Routing Table 查找 Source Address 來建立自己的 * * Multicast Routing Table 把 Multicast packets forward 出去。它在IGMP前面
	* Source Specific Multicast (SSM)

* Routing Information Protocol (RIP) 路由信息協定
	* Network 指令,Unicast 與 Broadcast等其他.....

* Open Shortest Path First 開放最短路由優先協定(router)
	一個開放型的鏈路狀態協議，用來幫助路由器計算到達目的地的最短路徑
	* Neighbor :Router 們成為 Neighbor 其實中間經過多個 State 
	* OSPF Neighbor 的三大元素
		* Router 透過 Multicast 搜尋 Neighbor
		* DR/BDR 的選擇條件 (先比 Prioriy，再比 Router ID)
		* Timer 值 (Hello Interval 與 Dead Interval)，預設為 10/40 秒
### VPN
...待補

模擬器相關:EVE-NG掛IOU(IOS on unix)
## 題庫
https://github.com/benpengtw/my_note_data/tree/master/study/network/CCNA（200-125）题库V3.0（2019.01.08）选择题.pdf


參考資料

* https://www.jannet.hk/zh-Hant/

* https://bbs.hh010.com/ (hh010/鴻鹄論壇)

# 雲
**Iaas,Paas,Saas**

**基礎設施即服務(Infrastructure as a Service，簡稱IaaS)** 

消費者使用處理、儲存、網路以及各種基礎運算資源，部署與執行作業系統或應用程式等各種軟體。客戶端無須購買伺服器、軟體等網路設備，即可任意部署和運行處理、存儲、網絡和其它基本的計算資源，不能控管或控制底層的基礎設施，但是可以控制作業系統、儲存裝置、已部署的應用程式，有時也可以有限度地控制特定的網路元件，像是主機端防火牆。

**平台即服務（platform as a service，縮寫作PaaS）**

一種雲端運算服務，提供運算平台與解決方案服務。在雲端運算的典型層級中，PaaS層介於軟體即服務與基礎設施即服務之間。
PaaS提供使用者將雲端基礎設施部署與建立至用戶端，或者藉此獲得使用程式語言、程式庫與服務。使用者不需要管理與控制雲端基礎設施（包含網路、伺服器、作業系統或儲存），但需要控制上層的應用程式部署與應用代管的環境。
PaaS將軟體研發的平台做為一種服務，以軟體即服務（SaaS）模式交付給用戶。因此，PaaS也是SaaS模式的一種應用。但是，PaaS的出現可以加快SaaS的發展，尤其是加快SaaS應用的開發速度。

**軟體即服務（英語：Software as a Service，縮寫為 SaaS，發音：sæs或sɑs）**

有時被作為「即需即用軟體」提及，它是一種軟體交付模式。在這種交付模式中雲端集中式代管軟體及其相關的資料，軟體僅需透過網際網路，而不須透過安裝即可使用。用戶通常使用精簡用戶端經由一個網頁瀏覽器來存取軟體即服務。
對於許多商業應用來說，軟體即服務已經成為一種常見的交付模式。這些商業應用包括會計系統、協同軟體、客戶關係管理、管理資訊系統、開票系統、人力資源管理、內容管理、以及服務台管理。軟體即服務已經被吸納進所有領先的企業級軟體公司的戰略中。這些公司的最大的賣點之一就是通過將硬體和軟體維護及支援外包給軟體即服務的提供者，來降低資訊科技（Information Technology，簡稱IT）成本

![cloud](https://az787680.vo.msecnd.net/user/凌凌漆/ac5bf37a-bcad-413d-9a85-6d106e9a4f08/1504243049_55741.png "cloud")

**私有雲與公有雲的抉擇**

藉由伺服器虛擬化的技術，有些企業逐漸取得了類似Google、AWS、微軟Azure雲端業者規模與能力的IT服務，再加上這些公司當中，有許多普遍希望自行建置並掌控IT環境，擔心資料外洩或效能受到影響，而不願與他人共用，僅服務內部員工或合作廠商，也因此，這類型雲端服務在部署模式上，會被歸類在所謂的私有雲（Private Cloud）。

相對地，直接面向一般使用者或各種組織、企業的服務商，像是Google、AWS、微軟Azure、SoftLayer，他們所提供的服務，就稱為公有雲（Public Cloud）。

私有雲和公有雲的差異，主要是基於擁有權的不同，但兩者的環境建置上，可採用相同或不同的技術。例如許多業者皆運用伺服器虛擬化技術，將伺服器、儲存設備與網路設備，建構成共用資源池（Resource Pool），不過由於部署規模較大，為了節省軟體授權支出，有許多公司會選擇開放原始碼、成本較低的Xen、KVM的Hypervisor，並且基於這樣的架構，來搭建整個服務的IT基礎架構。

**Azure Stack(混合雲)**

Azure Stack運用與 Azure相同的管理與自動化工具、快速佈建及擴充服務，無論開發人員在哪裡佈建資源， Azure API 皆為一致，開發人員只需撰寫一次即能部署至 Azure或 Azure Stack，並可隨著旺季、開發測試用途或需求來調整使用規模，發揮最大生產力。Azure Stack 可視為是 Azure 的延伸模組，為企業打造真正的混合雲環境，建置符合商業及法規要求的現代化應用程式。

* Edge 及離線的解決方案：先用 Azure Stack 系統處理本地數據，再彙整至 Microsoft Azure 進一步分析，以解決延遲及連接性的需求。
* 跨雲端及內部部署的現代應用程式：使用 Microsoft Azure 網頁及行動服務、容器、無伺服器運算 (Serverless) 及微服務架構，以透過 Azure Stack 更新及延伸舊有應用程式，同時跨內部部署及雲端運用一致的 DevOps 流程。
* 符合所有法律規範的雲端應用程式：於 Microsoft Azure 開發及部署的應用程式，不必改變程式碼，即可在 Azure Stack 上完整及彈性的部署，同時能符合企業客戶所有法規或政策需求。
    Azure Stack 在台正式上市  隨用隨付 (pay-as-you-use) 方案依客戶需求選擇

參考資料
* https://dotblogs.com.tw/007_lawrence/2017/08/21/155203 Iaas、Pass、Saas
* http://www.taiwancloud.com.tw/products/iaas/introduction/
* https://news.microsoft.com/zh-tw/microsoft-azure-stack/
* https://www.ithome.com.tw/tech/94707

## 機房
* 有使用Juniper設備，所以除了IOS外，也要會JUNOS
* SONET/SDH(光纖通訊標準) 可與 10GBE 相接
* 超融合基礎架構：超融合架構以通用硬體伺服器構成的叢集為基礎、以VM為核心，具備管理簡單、便於以積木堆疊方式擴充等特性。(伺服器的一種形式)
	* EX：VMware EVO:RAIL,Nutanix,SimpliVity

### Hypervisor(虛擬機器監視器 or virtual machine monitor) ###
* type I : 又稱為 bare-metal hypervisor ，看這個詞大致上就是跟裸機裝虛擬機有點關係，直接裝一層 hypervisor 在空機上面，然後 VM 的系統在安裝在 hypervisor ，這樣的虛擬系統離硬體控制比較接近，VM 要控制的硬體資源直接透過 hypervisor 去操作
	* EX： xen, kvm, VMware ESX/ESXi (後者為免費版本), Microsoft Hyper-V
* type II : 又稱為 hosted hypervisor ，跟 type I 相反，就是我必須裝作業系統之後，再去安裝 hypervisor ，通常都附在虛擬機軟體了，這種 hypervisor 的控制硬體方式是透過原本的作業系統代為處理
	* EX：Oracle Virtual Box, Microsoft Virtual PC, VMware Workstation/Fusion/Player

管理平台選擇
* VMwareESX<===>vCenter

* HyperV<===>SCVMM

* XEN<===>XEN server

* KVM<===> (multi)

__KVM__

KVM的管理平台選擇較多，沒有一個管理平臺能夠拿來直接使用，每個平臺都有自己的特點，要使用都要長期打磨。

**CloudStack：**
    特點是聲音越來越小，社群活躍度下降，可能剩下的問題是什麼時候shutdown。

**OpenNebula：**
    是個小眾的管理平臺，比較穩定，但是生產環境用起來，也至少需要幾個月的時間摸索。

**Proxmox VE：**
    PVE是目前為止，最接近vCenter的管理平臺，穩定性非常好，基本是拿來就有。PVE的問題是給人感覺概念比較另類，基於Debian定製，不使用Libvirt，雖然開源，但是要根據自己的需求定製很難，因為門檻非常高。

**oVirt：**
    oVirt的目標就是瞄準vCenter，oVirt的問題是還有許多功能有待完善，穩定性有待提升，大問題比較少了，但是小問題不斷。oVirt和RHEV的關係，有可能永遠就像Fedora和RHEL，oVirt就是一個實驗版本，不斷的在更新。

**OpenStack**
是一個雲操作系統，通過數據中心可控制大型的計算、存儲、網絡等資源池。所有的管理通過前端界面管理員就可以完成，同樣也可以通過web接口讓最終用戶部署資源。(大型)

簡單理解: 可以把它類比公有雲，它將各種基礎資源虛擬化，並提供簡化的方式去管理。偏向IAAS服務

### container與hypervisor區別 ###
![container](https://blog.mikesir87.io/images/containers-vs-vms-old.jpg "container")

A “more correct” version

![container](https://blog.mikesir87.io/images/containers-vs-vms-correct.png "container")
**Docker容器技術**

**k8s**

基于容器的集群管理平台，全稱是kubernetes，
是用於自動部署、擴展和管理容器化（containerized）應用程序的開源系統。

簡單理解: 容器編排，管理多機的容器狀態. 偏向PAAS服務

### 軟體定義網路（Software Defined Networking，SDN） ###
**OpenFlow**
OpenFlow技術後續的制定，其特色就是修改了傳統網路架構的控制模式，將網路的管理權限交由控制層的SDN控制器（Controller）軟體負責，採用集中控管的方式。 如同本文章前面的比喻 － 控制器軟體就像是人類的大腦，基礎設施層的SDN交換機就像是人類的四肢，而OpenFlow技術則用於在控制層與基礎設施層間建立傳輸通道，就像是人類的神經一樣，負責大腦與四肢的溝通。

**Overlay**
以重疊網路為基礎的解決方案並不是最近才被提出，例如：VLAN（虛擬區域網路）就是其中的典型代表，然而由於VLAN數量的不足（理論上最多只能有4096個VLAN，因為在802.1Q協定中只定義了12 個位元的VLAN ID欄位）大大限制了多租戶（Multi-Tenancy）雲端業務的規模； 在目前以重疊網路為基礎的SDN方案中，採用了VXLAN、NVGRE等的隧道（Tunneling）技術，它是以現行的IP網路為基礎，在其上部署重疊的邏輯網路（Overlay Logical Network），使得原本邏輯上屬於相同租戶的多台伺服器（或虛擬機器），雖然在實體位置上彼此分開，但是可以透過Layer 2 over Layer 3隧道的建立來進行網路通訊； 換句話是利用重疊在三層IP網路之上的虛擬網路傳遞二層資料封包，實現了可以跨越三層實體網路進行通訊的二層邏輯網路（也就是業界所謂“大二層”的網路虛擬化概念），並進而使得分開在不同位置的伺服器主機上實施虛擬機器的線上移轉（vMotion）與高可用性的容錯機制（Fault Tolerance）成為可能。 

### 網路功能虛擬化（Network Virtualization Function，NFV) ###
NFV則是將實體設備的網路功能，以軟體的型態呈現，例如路由器（Router）、防火牆（Firewall）、負載平衡器（Load Balancer）與用戶終端設備（CPE）等；這種將網路功能虛擬化（意即軟體化）的概念，顛覆過去網路功能必須存在特定硬體設備中的傳統架構。因網路功能被虛擬化後，有著極佳的彈性配置特性，能加速網路服務的部署效率，亦能降低購置專用硬體的開銷。
![cloud](https://cdn-images-1.medium.com/max/1600/1*KpRM2S5AhrhBLl0GetuVpg.png "cloud")

參考資料
* https://www.ithome.com.tw/tech/92534
* https://freedomknight.me/chu-tan-xu-ni-ji-he-xu-ni-hua/ hypervisor 
* https://juejin.im/post/5b953d21f265da0afa3dc61b Kubernetes/OpenStack 
* https://www.ithome.com.tw/tech/98858 ceph,Server SAN
* https://blog.mikesir87.io/2017/05/docker-is-not-a-hypervisor/
* https://zhuanlan.zhihu.com/p/53260098
* https://www.itread01.com/content/1546859350.html