---
title: Como controlar o tipo de uma projeção (C#)
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 4aea9fd07ff2a128da9be0a17e5f70a25c9f3853
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146557"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="135c3-102">Como controlar o tipo de uma projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="135c3-102">How to: Control the Type of a Projection (C#)</span></span>
<span data-ttu-id="135c3-103">A projeção é o processo de receber um dataset, de filtre-o, para alterar sua forma, e mesmo de alterar seu tipo.</span><span class="sxs-lookup"><span data-stu-id="135c3-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="135c3-104">A maioria das expressões de consulta executam projeções.</span><span class="sxs-lookup"><span data-stu-id="135c3-104">Most query expressions perform projections.</span></span> <span data-ttu-id="135c3-105">A maioria das expressões de consulta mostradas nesta seção valor para <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, mas você pode controlar o tipo de projeção para criar coleções de outros tipos.</span><span class="sxs-lookup"><span data-stu-id="135c3-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="135c3-106">Este tópico mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="135c3-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="135c3-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="135c3-107">Example</span></span>  
 <span data-ttu-id="135c3-108">O exemplo a seguir define um novo tipo, `Customer`.</span><span class="sxs-lookup"><span data-stu-id="135c3-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="135c3-109">A expressão de consulta cria uma instância em novos objetos de `Customer` na cláusula `Select` .</span><span class="sxs-lookup"><span data-stu-id="135c3-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="135c3-110">Isso faz com que o tipo da expressão de consulta para ser <xref:System.Collections.Generic.IEnumerable%601> de `Customer`.</span><span class="sxs-lookup"><span data-stu-id="135c3-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="135c3-111">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: clientes e pedidos (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="135c3-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
        return $"{this.customerID}:{this.companyName}:{this.contactName}";
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
  
 <span data-ttu-id="135c3-112">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="135c3-112">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="135c3-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="135c3-113">See Also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>  
- [<span data-ttu-id="135c3-114">Projeções e transformações (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="135c3-114">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
