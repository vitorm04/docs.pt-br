---
title: Como unir duas coleções (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 00db2decfb8595c32e86f76c8aa139d91e75d112
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513524"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="23d4e-102">Como unir duas coleções (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="23d4e-102">How to: Join Two Collections (LINQ to XML) (C#)</span></span>
<span data-ttu-id="23d4e-103">Um elemento ou atributo em um documento XML, algumas vezes, pode fazer referência a outro elemento ou atributo.</span><span class="sxs-lookup"><span data-stu-id="23d4e-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="23d4e-104">Por exemplo, o documento XML [Arquivo XML de exemplo: clientes e pedidos (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) contém uma lista de clientes e uma lista de pedidos.</span><span class="sxs-lookup"><span data-stu-id="23d4e-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="23d4e-105">Cada elemento `Customer` contém um atributo `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="23d4e-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="23d4e-106">Cada elemento `Order` contém um atributo `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="23d4e-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="23d4e-107">O elemento `CustomerID` em cada pedido faz referência ao atributo `CustomerID` em um cliente.</span><span class="sxs-lookup"><span data-stu-id="23d4e-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="23d4e-108">O tópico [Arquivo XSD de exemplo: clientes e pedidos](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) contém um XSD que pode ser usado para validar esse documento.</span><span class="sxs-lookup"><span data-stu-id="23d4e-108">The topic [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="23d4e-109">Usa os recursos de XSD `xs:key` e `xs:keyref` para estabelecer que o atributo `CustomerID` do elemento `Customer` é uma chave, e para estabelecer uma relação entre o elemento `CustomerID` em cada elemento `Order`, e o atributo `CustomerID` em cada elemento `Customer`.</span><span class="sxs-lookup"><span data-stu-id="23d4e-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="23d4e-110">Com o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você pode tirar proveito dessa relação usando a cláusula `join`.</span><span class="sxs-lookup"><span data-stu-id="23d4e-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>  
  
 <span data-ttu-id="23d4e-111">Observe que como não existe nenhum índice disponível, essa junção terá um desempenho inadequado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="23d4e-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="23d4e-112">Para obter informações mais detalhadas sobre `join`, consulte [Operações de junção (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="23d4e-112">For more detailed information about `join`, see [Join Operations (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23d4e-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="23d4e-113">Example</span></span>  
 <span data-ttu-id="23d4e-114">O exemplo a seguir une os elementos `Customer` aos elementos `Order` e gera um novo documento XML que inclui o elemento `CompanyName` nos pedidos.</span><span class="sxs-lookup"><span data-stu-id="23d4e-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="23d4e-115">Antes de executar a consulta, o exemplo valida que o documento está de acordo com o esquema em [Arquivo XSD de exemplo: clientes e pedidos](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="23d4e-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="23d4e-116">Isso garante que a cláusula join sempre funcionará.</span><span class="sxs-lookup"><span data-stu-id="23d4e-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="23d4e-117">Esta consulta retorna primeiro todos os elementos `Customer` e, em seguida, une-os aos elementos `Order`.</span><span class="sxs-lookup"><span data-stu-id="23d4e-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="23d4e-118">A consulta seleciona apenas os pedidos de clientes com um `CustomerID` maior que "K".</span><span class="sxs-lookup"><span data-stu-id="23d4e-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="23d4e-119">Em seguida, projeta um novo elemento `Order` que contém as informações do cliente dentro de cada pedido.</span><span class="sxs-lookup"><span data-stu-id="23d4e-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="23d4e-120">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: clientes e pedidos (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="23d4e-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="23d4e-121">Este exemplo usa o seguinte esquema XSD: [Arquivo XSD de exemplo: clientes e pedidos](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="23d4e-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span>  
  
 <span data-ttu-id="23d4e-122">Observe que a junção dessa forma não será muito bem-executada.</span><span class="sxs-lookup"><span data-stu-id="23d4e-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="23d4e-123">As junções são executadas por meio de uma pesquisa linear.</span><span class="sxs-lookup"><span data-stu-id="23d4e-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="23d4e-124">Não há nenhuma tabela de hash ou índice para ajudar no desempenho.</span><span class="sxs-lookup"><span data-stu-id="23d4e-124">There are no hash tables or indexes to help with performance.</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.Write("Attempting to validate, ");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
if (!errors)  
{  
    // Join customers and orders, and create a new XML document with  
    // a different shape.  
  
    // The new document contains orders only for customers with a  
    // CustomerID > 'K'  
    XElement custOrd = custOrdDoc.Element("Root");  
    XElement newCustOrd = new XElement("Root",  
        from c in custOrd.Element("Customers").Elements("Customer")  
        join o in custOrd.Element("Orders").Elements("Order")  
                   on (string)c.Attribute("CustomerID") equals  
                      (string)o.Element("CustomerID")  
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0  
        select new XElement("Order",  
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),  
            new XElement("CompanyName", (string)c.Element("CompanyName")),  
            new XElement("ContactName", (string)c.Element("ContactName")),  
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),  
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))  
        )  
    );  
    Console.WriteLine(newCustOrd);  
}  
```  
  
 <span data-ttu-id="23d4e-125">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="23d4e-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="23d4e-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23d4e-126">See Also</span></span>

- [<span data-ttu-id="23d4e-127">Técnicas avançadas de consulta (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="23d4e-127">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
