---
title: 'Como: Projetar um tipo anônimo (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: 613bf97556306503c427a70720272dd985495b13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527751"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a><span data-ttu-id="9da48-102">Como: Projetar um tipo anônimo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9da48-102">How to: Project an Anonymous Type (Visual Basic)</span></span>
<span data-ttu-id="9da48-103">Em alguns casos você pode querer projetar uma consulta a um novo tipo, mesmo que você soubesse que você usará apenas este tipo para um curto quando.</span><span class="sxs-lookup"><span data-stu-id="9da48-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="9da48-104">É muito trabalho adicional para criar apenas um novo tipo para usar na projeção.</span><span class="sxs-lookup"><span data-stu-id="9da48-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="9da48-105">Uma abordagem mais eficiente nesse caso é projeto para um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="9da48-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="9da48-106">Tipos anônimos permitem que você defina uma classe, então declare e inicialize um objeto de aquela classe, sem dar um nome para a classe.</span><span class="sxs-lookup"><span data-stu-id="9da48-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="9da48-107">Os tipos anônimos são a implementação de C# do conceito matemático de uma *tupla*.</span><span class="sxs-lookup"><span data-stu-id="9da48-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="9da48-108">O tuple o termo matemático proveniente da sequência única, double, triplo, quádruplo, quintuple, n- tuple.</span><span class="sxs-lookup"><span data-stu-id="9da48-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="9da48-109">Refere-se a uma sequência finito rotuladas de objetos, cada um de um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="9da48-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="9da48-110">Isso é às vezes chamado uma lista de pares nome/valor.</span><span class="sxs-lookup"><span data-stu-id="9da48-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="9da48-111">Por exemplo, o conteúdo de um endereço no [arquivo XML de exemplo: Ordem de compra típica (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) documento XML pode ser expresso da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9da48-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="9da48-112">Quando você cria uma instância de um tipo anônimo, é conveniente pensar nele como criar um tuple de Em ordem.</span><span class="sxs-lookup"><span data-stu-id="9da48-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="9da48-113">Se você escrever uma consulta que cria um tuple na cláusula `Select` , a consulta retorna `IEnumerable` de tuple.</span><span class="sxs-lookup"><span data-stu-id="9da48-113">If you write a query that creates a tuple in the `Select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9da48-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9da48-114">Example</span></span>  
 <span data-ttu-id="9da48-115">Nesse exemplo, a cláusula de `Select` projetos de um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="9da48-115">In this example, the `Select` clause projects an anonymous type.</span></span> <span data-ttu-id="9da48-116">O exemplo usa em `Dim` para criar o objeto de `IEnumerable` .</span><span class="sxs-lookup"><span data-stu-id="9da48-116">The example then uses `Dim` to create the `IEnumerable` object.</span></span> <span data-ttu-id="9da48-117">Dentro do loop de `For Each` , a variável de iteração torna-se em uma instância do tipo anônimo criado na expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="9da48-117">Within the `For Each` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="9da48-118">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Os clientes e pedidos (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9da48-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
```  
  
 <span data-ttu-id="9da48-119">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="9da48-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="9da48-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9da48-120">See also</span></span>
- [<span data-ttu-id="9da48-121">Projeções e transformações (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9da48-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
