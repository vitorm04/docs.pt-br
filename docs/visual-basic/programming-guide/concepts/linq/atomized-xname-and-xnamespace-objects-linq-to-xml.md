---
title: Objetos XName e XNamespace Atomizados (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: adf766dcb69477fbad8581b075a7c0ee8a82f728
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623667"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="bac3d-102">Objetos XName e XNamespace Atomizados (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bac3d-102">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="bac3d-103">Os objetos <xref:System.Xml.Linq.XName> e <xref:System.Xml.Linq.XNamespace> são *atomizados*, isto é, se eles contêm o mesmo nome qualificado, referem-se ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="bac3d-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="bac3d-104">Isso resulta em benefícios de desempenho para consultas: Quando você compara dois nomes atomizados para igualdade, a linguagem intermediária subjacente só precisa determinar se as duas referências apontam para o mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="bac3d-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="bac3d-105">O código subjacente não tem que fazer as comparações de cadeias de caracteres, que poderiam demoradas.</span><span class="sxs-lookup"><span data-stu-id="bac3d-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="bac3d-106">Semântica de atomização</span><span class="sxs-lookup"><span data-stu-id="bac3d-106">Atomization Semantics</span></span>  
 <span data-ttu-id="bac3d-107">A atomização significa que se dois objetos de <xref:System.Xml.Linq.XName> têm o mesmo nome local, e estão no mesmo namespace, compartilham a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="bac3d-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="bac3d-108">Da mesma forma, se dois objetos de <xref:System.Xml.Linq.XNamespace> têm o mesmo URI de namespace, compartilham a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="bac3d-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="bac3d-109">Para que uma classe permite objetos atomizados, o construtor para a classe deve ser particular, não público.</span><span class="sxs-lookup"><span data-stu-id="bac3d-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="bac3d-110">Isso ocorre porque se foi o construtor público, você pode criar um objeto não atomizado.</span><span class="sxs-lookup"><span data-stu-id="bac3d-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="bac3d-111">As classes de <xref:System.Xml.Linq.XName> e de <xref:System.Xml.Linq.XNamespace> implementam um operador de conversão implícita para converter uma cadeia de caracteres em <xref:System.Xml.Linq.XName> ou em <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="bac3d-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="bac3d-112">Isso é como você obtém uma instância desses objetos.</span><span class="sxs-lookup"><span data-stu-id="bac3d-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="bac3d-113">Você não pode obter uma instância usando um construtor, porque o construtor é inacessível.</span><span class="sxs-lookup"><span data-stu-id="bac3d-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="bac3d-114"><xref:System.Xml.Linq.XName> e <xref:System.Xml.Linq.XNamespace> também implementam os operadores de igualdade e desigualdade de, para determinar se dois objetos que estão sendo comparados são referências para a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="bac3d-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bac3d-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bac3d-115">Example</span></span>  
 <span data-ttu-id="bac3d-116">O código a seguir cria alguns objetos de <xref:System.Xml.Linq.XElement> e demonstrar-los que os nomes idênticos compartilham a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="bac3d-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
```vb  
Dim r1 As New XElement("Root", "data1")  
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")  
  
If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
  
Dim n As XName = "Root"  
  
If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
```  
  
 <span data-ttu-id="bac3d-117">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="bac3d-117">This example produces the following output:</span></span>  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="bac3d-118">Como mencionado anteriormente, a vantagem de objetos atomizados é que quando você usa um dos métodos do eixo que recebem <xref:System.Xml.Linq.XName> como um parâmetro, o método do eixo só precisa determinar que dois nomes referenciam a mesma instância para selecionar os elementos desejados.</span><span class="sxs-lookup"><span data-stu-id="bac3d-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="bac3d-119">O exemplo a seguir <xref:System.Xml.Linq.XName> passa a chamada de método <xref:System.Xml.Linq.XContainer.Descendants%2A> , que tem em melhor desempenho devido ao padrão de atomização.</span><span class="sxs-lookup"><span data-stu-id="bac3d-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
```vb  
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))  
  
Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e  
  
For Each z As var In query  
    Console.WriteLine(z)  
Next  
```  
  
 <span data-ttu-id="bac3d-120">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="bac3d-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bac3d-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bac3d-121">See also</span></span>
- [<span data-ttu-id="bac3d-122">Desempenho (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bac3d-122">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
