# app-doc-template

During the heat of the project and pressing deadlines we don't always have the time it takes to produce documentation for the future. Contributing to the problem is that we may not always know or agree what kind of documentation there should be and this ambiguity leads us to produce insufficient and unhelpful or even no documentation at all.

This document aims to provide simple but yet sufficient template to help you produce application documentation that covers at least the most crucial pieces of information.

To clarify the goal let's explain to whom and for what purpose we want to produce the documentation using this template. In the order of importance:
- Developers  
Developers are the main audience of the application document. Most importantly the document should enable smoother on-boarding and efficient introduction to the application. All the critical information on how to develop, maintain and troubleshoot the application should be documented.
- Architects  
Documentation should provide the architects with adequate high level overview of the application. 

## Solution architecture

Solution architecture describes high level architecture of the solution. It gives reader a quick overview of what are the related systems and their responsibilities and what are the main business functionalities provided by the solution.

### System context diagram

System context diagram shows the system in scope and its relationship with users and other systems.


```mermaid
  graph TD;
      A-->B;
      A-->C;
      B-->D;
      C-->D;
```

```mermaid
    C4Context
      title System Context diagram for Internet Banking System
      Enterprise_Boundary(b0, "BankBoundary0") {
        Person(customerA, "Banking Customer A", "A customer of the bank, with personal bank accounts.")
        Person(customerB, "Banking Customer B")      
        Person_Ext(customerC, "Banking Customer C", "desc")            

        Person(customerD, "Banking Customer D", "A customer of the bank, <br/> with personal bank accounts.")

        System(SystemAA, "Internet Banking System", "Allows customers to view information about their bank accounts, and make payments.")  

        Enterprise_Boundary(b1, "BankBoundary") {
         
          SystemDb_Ext(SystemE, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")      

          System_Boundary(b2, "BankBoundary2") {  
            System(SystemA, "Banking System A")  
            System(SystemB, "Banking System B", "A system of the bank, with personal bank accounts. next line.")        
          } 

          System_Ext(SystemC, "E-mail system", "The internal Microsoft Exchange e-mail system.") 
          SystemDb(SystemD, "Banking System D Database", "A system of the bank, with personal bank accounts.") 

          Boundary(b3, "BankBoundary3", "boundary") {  
            SystemQueue(SystemF, "Banking System F Queue", "A system of the bank.")        
            SystemQueue_Ext(SystemG, "Banking System G Queue", "A system of the bank, with personal bank accounts.") 
          }
        }
      }
      
      BiRel(customerA, SystemAA, "Uses")
      BiRel(SystemAA, SystemE, "Uses")
      Rel(SystemAA, SystemC, "Sends e-mails", "SMTP")
      Rel(SystemC, customerA, "Sends e-mails to")

      UpdateElementStyle(customerA, $fontColor="red", $bgColor="grey", $borderColor="red")
      UpdateRelStyle(customerA, SystemAA, $textColor="blue", $lineColor="blue", $offsetX="5")
      UpdateRelStyle(SystemAA, SystemE, $textColor="blue", $lineColor="blue", $offsetY="-10")
      UpdateRelStyle(SystemAA, SystemC, $textColor="blue", $lineColor="blue", $offsetY="-40", $offsetX="-50")
      UpdateRelStyle(SystemC, customerA, $textColor="red", $lineColor="red", $offsetX="-50", $offsetY="20")
      
      UpdateLayoutConfig($c4ShapeInRow="3", $c4BoundaryInRow="1")

```

# Deployment architecture

Where is this shit running?

# Developer documentation

## Crucial links

Links to app running in different envs

## Releasing

How to release? How to do hot fix?

### CI setup



