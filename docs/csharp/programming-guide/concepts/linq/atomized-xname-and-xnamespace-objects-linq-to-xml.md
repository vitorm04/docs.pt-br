---
title: Objetos XName e XNamespace atomizados (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: bc5066440d87f5485ae9099d7a7f4f5e9e66b4ec
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204275"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a><span data-ttu-id="50a33-102">Objetos XName e XNamespace atomizados (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="50a33-102">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="50a33-103">Os objetos <xref:System.Xml.Linq.XName> e <xref:System.Xml.Linq.XNamespace> são *atomizados*, isto é, se eles contêm o mesmo nome qualificado, referem-se ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="50a33-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="50a33-104">Isso resulta em benefícios de desempenho para consultas: Quando você compara dois nomes atomizados quanto à igualdade, a linguagem intermediária subjacente só precisa determinar se as duas referências apontam para o mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="50a33-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="50a33-105">O código subjacente não tem que fazer as comparações de cadeias de caracteres, que poderiam demoradas.</span><span class="sxs-lookup"><span data-stu-id="50a33-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="50a33-106">Semântica de atomização</span><span class="sxs-lookup"><span data-stu-id="50a33-106">Atomization Semantics</span></span>  
 <span data-ttu-id="50a33-107">A atomização significa que se dois objetos de <xref:System.Xml.Linq.XName> têm o mesmo nome local, e estão no mesmo namespace, compartilham a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="50a33-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="50a33-108">Da mesma forma, se dois objetos de <xref:System.Xml.Linq.XNamespace> têm o mesmo URI de namespace, compartilham a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="50a33-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="50a33-109">Para que uma classe permite objetos atomizados, o construtor para a classe deve ser particular, não público.</span><span class="sxs-lookup"><span data-stu-id="50a33-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="50a33-110">Isso ocorre porque se foi o construtor público, você pode criar um objeto não atomizado.</span><span class="sxs-lookup"><span data-stu-id="50a33-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="50a33-111">As classes de <xref:System.Xml.Linq.XName> e de <xref:System.Xml.Linq.XNamespace> implementam um operador de conversão implícita para converter uma cadeia de caracteres em <xref:System.Xml.Linq.XName> ou em <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="50a33-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="50a33-112">Isso é como você obtém uma instância desses objetos.</span><span class="sxs-lookup"><span data-stu-id="50a33-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="50a33-113">Você não pode obter uma instância usando um construtor, porque o construtor é inacessível.</span><span class="sxs-lookup"><span data-stu-id="50a33-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="50a33-114"><xref:System.Xml.Linq.XName> e <xref:System.Xml.Linq.XNamespace> também implementam os operadores de igualdade e desigualdade de, para determinar se dois objetos que estão sendo comparados são referências para a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="50a33-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50a33-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50a33-115">Example</span></span>  
 <span data-ttu-id="50a33-116">O código a seguir cria alguns objetos de <xref:System.Xml.Linq.XElement> e demonstrar-los que os nomes idênticos compartilham a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="50a33-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
```csharp  
XElement r1 = new XElement("Root", "data1");  
XElement r2 = XElement.Parse("<Root>data2</Root>");  
  
if ((object)r1.Name == (object)r2.Name)  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");  
else  
    Console.WriteLine("Different");  
  
XName n = "Root";  
  
if ((object)n == (object)r1.Name)  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");  
else  
    Console.WriteLine("Different");  
```  
  
 <span data-ttu-id="50a33-117">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="50a33-117">This example produces the following output:</span></span>  
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="50a33-118">Como mencionado anteriormente, a vantagem de objetos atomizados é que quando você usa um dos métodos do eixo que recebem <xref:System.Xml.Linq.XName> como um parâmetro, o método do eixo só precisa determinar que dois nomes referenciam a mesma instância para selecionar os elementos desejados.</span><span class="sxs-lookup"><span data-stu-id="50a33-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="50a33-119">O exemplo a seguir <xref:System.Xml.Linq.XName> passa a chamada de método <xref:System.Xml.Linq.XContainer.Descendants%2A> , que tem em melhor desempenho devido ao padrão de atomização.</span><span class="sxs-lookup"><span data-stu-id="50a33-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("C1", 1),  
    new XElement("Z1",  
        new XElement("C1", 2),  
        new XElement("C1", 1)  
    )  
);  
  
var query = from e in root.Descendants("C1")  
            where (int)e == 1  
            select e;  
  
foreach (var z in query)  
    Console.WriteLine(z);  
```  
  
 <span data-ttu-id="50a33-120">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="50a33-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
