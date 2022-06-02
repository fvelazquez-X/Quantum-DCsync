
# Implementation of a convoluted domain attack involving a quantum adversary

The following experiment describes a feasible way to perform a Quantum DCSync attack over a Quantum System, using the capabilities provided by Gate Identities and Multi-Qubit Operations deployed in Qiskit. DCSync is a credential dumping technique, widely utilized by adversaries, to extract individual user credentials in a domain, but more seriously as a prelude to the creation of a Golden Ticket giving complete persistance to the attacker; in effect, the adversary can access any resource from the domain they might choose. This capability is extremely powerful and difficult to detect. In an advanced stage of fully functional post-NISQ devices, attacks over theoretical “Quantum Active Directories” might be possible and the techniques developed to compromise classical systems can be translated into the quantum realm.

The general experiment approach is described in these steps, as we can check from the code:
1) A Quantum Communication Network is established within two peers (Alice and ServerDC) each of them using a theoretical Quantum device (post-NISQ era), which can be accessed also at gate level to execute quantum circuits. The representation of the quantum network can be perfectly abstracted in the quantum registers, and the gate operations between them can emulate the necessary protocols and components required for an Active Directory domain. The Quantum Communication circuit designed here is inspired by the implementations made by NetSquid (https://netsquid.org/), a tool for modelling and simulating quantum networks, as the one we are currently developing. (Coopmans, T., Knegjens, R., Dahlberg, A. et al. NetSquid, a NETwork Simulator for QUantum Information using Discrete events. Commun Phys 4, 164 (2021). https://doi.org/10.1038/s42005-021-00647-8). (Please refer to the Teleportation example in the official Netsquid documentation for more details).
2) The Kerberos authentication mechanism will be represented mainly by the delivery of the TGT to Alice's quantum registry and a later granted TGS for connecting to a Service A or B, using a single quantum operation. It is important to remark that the TGT will be created using a basic quantum encryption function generated from a “true” random quantum key, which at the same time willl be the representation of the KRBTGT account residing in the quantum registry ServerDC. Quantum RNG exploit elementary quantum processes that are fundamentally probabilistic to produce true randomness. More on topic can be found at https://qrng.anu.edu.au/ation.
4) It is assumed that attacker's registry is already executing post-exploitation techniques inside the domain, meaning that it made an intrusion, escalated privileges, and now it can introduce its quantum gates/operations arbitrarily in the Server's registry or Alice's registry. From the MITRE ATT&CK matrix we are going to apply the techniques located in Credential Access and subtechnique OS Credential Dumping: DCSync (OS Credential Dumping: DCSync, Sub-technique T1003.006 - Enterprise | MITRE ATT&CK®). (Classic ATT&CK matrix is referenced since there is still no "quantum" ATT&CK matrix released yet or equivalent). More to be detailed on the experiment.
5) For practicality, except the KRBTGT account, the other requirements for the Golden Ticket attack are given, (in a real engagement these are not very difficult to enumerate):

-Domain Name - foo.com

-Domain SID - SID-123

-UserID impersonated  Alice





## Golden Ticket Function

  
The golden ticket function contains the communication interchange between the registries, and the abstraction of the Active Directory domain with the presence of an attacker. It takes three main parameters:

service_TGS (String): The Service to be requested after obtaining a TGT (A or B).

TGT (boolean): If the value is set to True, the server grants a TGT to initiate a service connection.

attacker (boolean): If the attacker value is True, it will execute a Quantum DCSync attack towards the ServerDC registry.   


## Authors

- [@fvelazquez](https://www.github.com/fvelazquez-X)


## Acknowledgements

 - [Awesome qiskit learning resources]( https://qiskit.org/learn)
 - [Atacking the quantum internet](https://arxiv.org/abs/2005.04617)
 - [Enterprise tactics. ATT&CK](https://attack.mitre.org/tactics/enterprise/)


## Deployment

To run this project from a terminal using jupyter notebook:

- Firstly, you need to convert the jupyter notebook file which is in the format .ipynb to .py format using the jupyter nbconvert tool.
```bash
jupyter nbconvert --to <output format> <input notebook>
```

 Whereas, the <output format> is the desired output format. And the <input notebook> is the jupyter notbook filename.

- Verify whether .py file is created in your working directory.

- Finally, you could run a jupyter notebook .ipynb file from command prompt using the converted .py file as shown below.

```bash
   python MyFirstNotebook.py
```

## Documentation

[IBM Quantum Experience](https://quantum-computing.ibm.com/)


## Feedback

If you have any feedback, please reach out to us at jvelazqu@redhat.com


## 🚀 About Me

- 🔭 I’m an offensive security passionate working at [Red Hat](https://www.redhat.com/en)  
  

-  🔎 I’m currently learning more about [Quantum Technologies](https://quantum-explore.com/en/master/)   
  

- 📖 I recently wrote a book on Offensive Quantum Computing. Available at [Amazon](https://www.amazon.com/Introduction-Adversarial-Quantum-Computing-Practice-ebook/dp/B09YMJXQTX/ref=sr_1_1?crid=3VZONRJBAP2G3&keywords=fernando+velazquez+quantum&qid=1654154138&sprefix=%2Caps%2C138&sr=8-1)!!  
  

- ⚡ I publish articles on technology topics at  [Meer](https://www.meer.com/en/authors/390-fernando-velazquez)  


## License

[MIT](https://choosealicense.com/licenses/mit/)

