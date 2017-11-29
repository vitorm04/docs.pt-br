---
title: "Como controlar o tipo de uma projeção (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9b7b5b39ca308449b09023bc21446859a728e738
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-type-of-a-projection-c"></a>Como controlar o tipo de uma projeção (C#)
A projeção é o processo de receber um dataset, de filtre-o, para alterar sua forma, e mesmo de alterar seu tipo. A maioria das expressões de consulta executam projeções. A maioria das expressões de consulta mostradas nesta seção valor para <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, mas você pode controlar o tipo de projeção para criar coleções de outros tipos. Este tópico mostra como fazer isso.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um novo tipo, `Customer`. A expressão de consulta cria uma instância em novos objetos de `Customer` na cláusula `Select` . Isso faz com que o tipo da expressão de consulta para ser <xref:System.Collections.Generic.IEnumerable%601> de `Customer`.  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: clientes e pedidos (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
```csharp  
public class Customer  
{  
    private string customerID;  
    public string CustomerID{ get{return customerID;} set{customerID = value;}}  
  
    private string companyName;  
    public string CompanyName{ get{return companyName;} set{companyName = value;}}  
  
    private string contactName;  
    public string ContactName { get{return contactName;} set{contactName = value;}}  
  
    public Customer(string customerID, string companyName, string contactName)  
    {  
        CustomerID = customerID;  
        CompanyName = companyName;  
        ContactName = contactName;  
    }  
  
    public override string ToString()  
    {  
        return String.Format("{0}:{1}:{2}", this.customerID, this.companyName, this.contactName);  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement custOrd = XElement.Load("CustomersOrders.xml");  
        IEnumerable<Customer> custList =  
            from el in custOrd.Element("Customers").Elements("Customer")  
            select new Customer(  
                (string)el.Attribute("CustomerID"),  
                (string)el.Element("CompanyName"),  
                (string)el.Element("ContactName")  
            );  
        foreach (Customer cust in custList)  
            Console.WriteLine(cust);  
    }  
}  
```  
  
 Esse código gera a seguinte saída:  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.Enumerable.Select%2A>  
 [Projeções e transformações (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
