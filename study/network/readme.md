# CCNA/Ethernet
****
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
	** Router 透過 Multicast 搜尋 Neighbor
	** DR/BDR 的選擇條件 (先比 Prioriy，再比 Router ID)
	** Timer 值 (Hello Interval 與 Dead Interval)，預設為 10/40 秒
### VPN

模擬器相關:EVE-NG掛IOU(IOS on unix)

參考資料

https://www.jannet.hk/zh-Hant/

# 雲
****
## laas,Paas,Saas
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
https://dotblogs.com.tw/007_lawrence/2017/08/21/155203
http://www.taiwancloud.com.tw/products/iaas/introduction/
https://news.microsoft.com/zh-tw/microsoft-azure-stack/
https://kknews.cc/zh-tw/tech/qb8zxng.html
https://www.ithome.com.tw/tech/94707

## 機房
***
* 有使用Juniper設備，所以除了IOS外，也要會JUNOS
* 超融合基礎架構
* 虛擬機器監視器(Hypervisor)：VMware的ESX與後繼的vSphere、Xen與XenServer、微軟Hyper-V、Citrix、Red Hat、Xen、KVM虛擬化平臺，以及OpenStack

* IP over SDH 

參考資料
https://baike.baidu.com/item/IP%20over%20SDH
https://www.ithome.com.tw/tech/92534