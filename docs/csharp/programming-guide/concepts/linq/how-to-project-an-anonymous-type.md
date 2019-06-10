---
title: 'Como: Projetar um tipo anônimo (C#)'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 68b008d70474c927a7911dc77e60afb634035b77
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485134"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="a01ac-102">Como: Projetar um tipo anônimo (C#)</span><span class="sxs-lookup"><span data-stu-id="a01ac-102">How to: Project an Anonymous Type (C#)</span></span>
<span data-ttu-id="a01ac-103">Em alguns casos você pode querer projetar uma consulta a um novo tipo, mesmo que você soubesse que você usará apenas este tipo para um curto quando.</span><span class="sxs-lookup"><span data-stu-id="a01ac-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="a01ac-104">É muito trabalho adicional para criar apenas um novo tipo para usar na projeção.</span><span class="sxs-lookup"><span data-stu-id="a01ac-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="a01ac-105">Uma abordagem mais eficiente nesse caso é projeto para um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="a01ac-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="a01ac-106">Tipos anônimos permitem que você defina uma classe, então declare e inicialize um objeto de aquela classe, sem dar um nome para a classe.</span><span class="sxs-lookup"><span data-stu-id="a01ac-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="a01ac-107">Os tipos anônimos são a implementação de C# do conceito matemático de uma *tupla*.</span><span class="sxs-lookup"><span data-stu-id="a01ac-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="a01ac-108">O tuple o termo matemático proveniente da sequência única, double, triplo, quádruplo, quintuple, n- tuple.</span><span class="sxs-lookup"><span data-stu-id="a01ac-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="a01ac-109">Refere-se a uma sequência finito rotuladas de objetos, cada um de um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="a01ac-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="a01ac-110">Isso é às vezes chamado uma lista de pares nome/valor.</span><span class="sxs-lookup"><span data-stu-id="a01ac-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="a01ac-111">Por exemplo, o conteúdo de um endereço no documento XML [Arquivo XML de exemplo: Ordem de compra típica (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) pode ser expresso da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a01ac-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="a01ac-112">Quando você cria uma instância de um tipo anônimo, é conveniente pensar nele como criar um tuple de Em ordem.</span><span class="sxs-lookup"><span data-stu-id="a01ac-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="a01ac-113">Se você escrever uma consulta que cria um tuple na cláusula `select` , a consulta retorna `IEnumerable` de tuple.</span><span class="sxs-lookup"><span data-stu-id="a01ac-113">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a01ac-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a01ac-114">Example</span></span>  
 <span data-ttu-id="a01ac-115">Nesse exemplo, a cláusula de `select` projetos de um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="a01ac-115">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="a01ac-116">O exemplo usa em `var` para criar o objeto de `IEnumerable` .</span><span class="sxs-lookup"><span data-stu-id="a01ac-116">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="a01ac-117">Dentro do loop de `foreach` , a variável de iteração torna-se em uma instância do tipo anônimo criado na expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="a01ac-117">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="a01ac-118">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Clientes e ordens (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="a01ac-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
var custList =  
    from el in custOrd.Element("Customers").Elements("Customer")  
    select new {  
        CustomerID = (string)el.Attribute("CustomerID"),  
        CompanyName = (string)el.Element("CompanyName"),  
        ContactName = (string)el.Element("ContactName")  
    };  
foreach (var cust in custList)  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);  
```  
  
 <span data-ttu-id="a01ac-119">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="a01ac-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  