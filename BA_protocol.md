# Byzantine Agreement Protocal
## Summary of Byzantine Agreement papers
list of classic BA papers by topic & timeline 
### Byzantine generals problem
#### PSL80
  - Marshall C. Pease, Robert E. Shostak, and Leslie Lamport. Reaching agreement in the presence of faults. 
  - https://lamport.azurewebsites.net/pubs/reaching.pdf

PSL80是拜占庭将军问题的起源，更早地根源于科学家为了研究飞行器的安全而遇到的问题。也是规约与验证（specification and verification ）这种研究方法的早期表现。可目为形式化验证滥觞之一。
PSL80需要解决的是正确输入的有效性。即决策值必须来自非故障节点，而不能受到故障节点的干扰。也就是如何能拒绝故障节点的假消息。
注意论文对故障节点的行为进行了假设，故障节点可以拒绝传递消息，但不能修改传递的消息（通过加密学方法解决）

PSL80的牛逼在于证明了33%这个结论（n>=3m+1), m为故障节点，n为节点总数。也就是说故障节点不能多于33%，这个是后世所有BFT协议的理论基础。
PSL80获得了2005年的Dijkstra奖

#### LSP82
  - Leslie Lamport, Robert E. Shostak, and Marshall C. Pease. The byzantine generals problem
  - http://lamport.azurewebsites.net/pubs/byz.pdf
###
- BO83
- Rab83
- FLP85
- DLS88
- BG93
- FM97
- FG03
- Nak08b
- KK09
- BSV+96
- Oku05b, Oku05a
- OB08
- BCL+11
- ML14
- GKL15,GKL16
- PSS16



### Reference
- The Bitcoin Backbone Protocol: Analysis and Applications 
  - https://eprint.iacr.org/2014/765.pdf 
- https://en.wikipedia.org/wiki/Byzantine_fault_tolerance
- 区块链核心算法解析 Roger Wattenhofer 
