---
title: "Como: unir duas coleções (LINQ to XML) (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b336337d068799a68fd84d41be5e265cc6486171
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a><span data-ttu-id="06ec2-102">Como: unir duas coleções (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06ec2-102">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="06ec2-103">Um elemento ou atributo em um documento XML, algumas vezes, pode fazer referência a outro elemento ou atributo.</span><span class="sxs-lookup"><span data-stu-id="06ec2-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="06ec2-104">Por exemplo, o [arquivo XML de exemplo: clientes e pedidos (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) documento XML contém uma lista de clientes e uma lista de pedidos.</span><span class="sxs-lookup"><span data-stu-id="06ec2-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="06ec2-105">Cada elemento `Customer` contém um atributo `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="06ec2-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="06ec2-106">Cada elemento `Order` contém um atributo `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="06ec2-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="06ec2-107">O elemento `CustomerID` em cada pedido faz referência ao atributo `CustomerID` em um cliente.</span><span class="sxs-lookup"><span data-stu-id="06ec2-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="06ec2-108">O tópico [arquivo XSD de exemplo: clientes e pedidos](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) contém um XSD que pode ser usado para validar esse documento.</span><span class="sxs-lookup"><span data-stu-id="06ec2-108">The topic [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="06ec2-109">Usa os recursos de XSD `xs:key` e `xs:keyref` para estabelecer que o atributo `CustomerID` do elemento `Customer` é uma chave, e para estabelecer uma relação entre o elemento `CustomerID` em cada elemento `Order`, e o atributo `CustomerID` em cada elemento `Customer`.</span><span class="sxs-lookup"><span data-stu-id="06ec2-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="06ec2-110">Com o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], você pode tirar proveito dessa relação usando a cláusula `Join`.</span><span class="sxs-lookup"><span data-stu-id="06ec2-110">With [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you can take advantage of this relationship by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="06ec2-111">Observe que como não existe nenhum índice disponível, essa junção terá um desempenho inadequado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="06ec2-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="06ec2-112">Para obter mais informações sobre `Join`, consulte [operações Join (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="06ec2-112">For more detailed information about `Join`, see [Join Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06ec2-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06ec2-113">Example</span></span>  
 <span data-ttu-id="06ec2-114">O exemplo a seguir une os elementos `Customer` aos elementos `Order` e gera um novo documento XML que inclui o elemento `CompanyName` nos pedidos.</span><span class="sxs-lookup"><span data-stu-id="06ec2-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="06ec2-115">Antes de executar a consulta, o exemplo valida que o documento está em conformidade com o esquema no [arquivo XSD de exemplo: clientes e pedidos](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="06ec2-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="06ec2-116">Isso garante que a cláusula join sempre funcionará.</span><span class="sxs-lookup"><span data-stu-id="06ec2-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="06ec2-117">Esta consulta retorna primeiro todos os elementos `Customer` e, em seguida, une-os aos elementos `Order`.</span><span class="sxs-lookup"><span data-stu-id="06ec2-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="06ec2-118">A consulta seleciona apenas os pedidos de clientes com um `CustomerID` maior que "K".</span><span class="sxs-lookup"><span data-stu-id="06ec2-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="06ec2-119">Em seguida, projeta um novo elemento `Order` que contém as informações do cliente dentro de cada pedido.</span><span class="sxs-lookup"><span data-stu-id="06ec2-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="06ec2-120">Este exemplo usa o seguinte documento XML: [arquivo XML de exemplo: clientes e pedidos (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="06ec2-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="06ec2-121">Este exemplo usa o seguinte esquema XSD: [arquivo XSD de exemplo: clientes e pedidos](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="06ec2-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span>  
  
 <span data-ttu-id="06ec2-122">Observe que a junção dessa forma não será muito bem-executada.</span><span class="sxs-lookup"><span data-stu-id="06ec2-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="06ec2-123">As junções são executadas por meio de uma pesquisa linear.</span><span class="sxs-lookup"><span data-stu-id="06ec2-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="06ec2-124">Não há nenhuma tabela de hash ou índice para ajudar no desempenho.</span><span class="sxs-lookup"><span data-stu-id="06ec2-124">There are no hash tables or indexes to help with performance.</span></span>  
  
```vb  
Public Class Program  
    Public Shared errors As Boolean = False  
  
    Public Shared Function LamValidEvent(ByVal o As Object, _  
                 ByVal e As ValidationEventArgs) As Boolean  
        Console.WriteLine("{0}", e.Message)  
        errors = True  
    End Function  
  
    Shared Sub Main()  
        Dim schemas As New XmlSchemaSet()  
        schemas.Add("", "CustomersOrders.xsd")  
  
        Console.Write("Attempting to validate, ")  
        Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")  
  
        custOrdDoc.Validate(schemas, Function(o, e) LamValidEvent(0, e))  
        If errors Then  
            Console.WriteLine("custOrdDoc did not validate")  
        Else  
            Console.WriteLine("custOrdDoc validated")  
        End If  
  
        If Not errors Then  
            'Join customers and orders, and create a new XML document with  
            ' a different shape.  
            'The new document contains orders only for customers with a  
            ' CustomerID > 'K'.  
            Dim custOrd As XElement = custOrdDoc.<Root>.FirstOrDefault  
            Dim newCustOrd As XElement = _  
                <Root>  
                    <%= From c In custOrd.<Customers>.<Customer> _  
                        Join o In custOrd.<Orders>.<Order> _  
                        On c.@CustomerID Equals o.<CustomerID>.Value _  
                        Where c.@CustomerID.CompareTo("K") > 0 _  
                        Select _  
                        <Order>  
                            <CustomerID><%= c.@CustomerID %></CustomerID>  
                            <%= c.<CompanyName> %>  
                            <%= c.<ContactName> %>  
                            <%= o.<EmployeeID> %>  
                            <%= o.<OrderDate> %>  
                        </Order> _  
                    %>  
                </Root>  
            Console.WriteLine(newCustOrd)  
        End If  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="06ec2-125">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="06ec2-125">This code produces the following output:</span></span>  
  
```  
Attempting to validate, custOrdDoc validated  
<Root>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-03-21T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-05-22T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-06-25T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-10-27T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>6</EmployeeID>  
    <OrderDate>1997-11-10T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>4</EmployeeID>  
    <OrderDate>1998-02-12T00:00:00</OrderDate>  
  </Order>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="06ec2-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06ec2-126">See Also</span></span>  
 [<span data-ttu-id="06ec2-127">Técnicas avançadas de consulta (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06ec2-127">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
