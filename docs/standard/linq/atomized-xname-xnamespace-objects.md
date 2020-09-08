---
title: Objetos XName e XNamespace atomos-LINQ to XML
description: Saiba como objetos XName e XNamespace com o mesmo nome compartilham uma instância.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: bc2be4d408385936598d94d34f9b452d950516d3
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552030"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml"></a><span data-ttu-id="8202f-103">Objetos XName e XNamespace atomed (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8202f-103">Atomized XName and XNamespace objects (LINQ to XML)</span></span>

<span data-ttu-id="8202f-104">Os objetos <xref:System.Xml.Linq.XName> e <xref:System.Xml.Linq.XNamespace> são *atomizados*, isto é, se eles contêm o mesmo nome qualificado, referem-se ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="8202f-104"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="8202f-105">Isso produz benefícios de desempenho para consultas: quando você compara dois nomes atomos para igualdade, a linguagem intermediária subjacente só precisa determinar se as duas referências apontam para o mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="8202f-105">This yields performance benefits for queries: when you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="8202f-106">O código subjacente não precisa fazer comparações de cadeias de caracteres, o que levaria mais tempo.</span><span class="sxs-lookup"><span data-stu-id="8202f-106">The underlying code doesn't have to do string comparisons, which would take longer.</span></span>

## <a name="atomization-semantics"></a><span data-ttu-id="8202f-107">Semântica de atomização</span><span class="sxs-lookup"><span data-stu-id="8202f-107">Atomization semantics</span></span>

<span data-ttu-id="8202f-108">A atomização significa que, se dois <xref:System.Xml.Linq.XName> objetos tiverem o mesmo nome local e estiverem no mesmo namespace, eles compartilharão a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="8202f-108">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they're in the same namespace, they share the same instance.</span></span> <span data-ttu-id="8202f-109">Da mesma forma, se dois objetos de <xref:System.Xml.Linq.XNamespace> têm o mesmo URI de namespace, compartilham a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="8202f-109">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>

<span data-ttu-id="8202f-110">Para que uma classe permite objetos atomizados, o construtor para a classe deve ser particular, não público.</span><span class="sxs-lookup"><span data-stu-id="8202f-110">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="8202f-111">Isso ocorre porque se foi o construtor público, você pode criar um objeto não atomizado.</span><span class="sxs-lookup"><span data-stu-id="8202f-111">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="8202f-112">As classes de <xref:System.Xml.Linq.XName> e de <xref:System.Xml.Linq.XNamespace> implementam um operador de conversão implícita para converter uma cadeia de caracteres em <xref:System.Xml.Linq.XName> ou em <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="8202f-112">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="8202f-113">Isso é como você obtém uma instância desses objetos.</span><span class="sxs-lookup"><span data-stu-id="8202f-113">This is how you get an instance of these objects.</span></span> <span data-ttu-id="8202f-114">Você não pode obter uma instância usando um construtor, pois o Construtor está inacessível.</span><span class="sxs-lookup"><span data-stu-id="8202f-114">You can't get an instance by using a constructor, because the constructor is inaccessible.</span></span>

<span data-ttu-id="8202f-115"><xref:System.Xml.Linq.XName> Além <xref:System.Xml.Linq.XNamespace> disso, implemente os operadores de igualdade e desigualdade, que determinam se os dois objetos que estão sendo comparados são referências à mesma instância.</span><span class="sxs-lookup"><span data-stu-id="8202f-115"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, which determine whether the two objects being compared are references to the same instance.</span></span>

## <a name="example-create-objects-and-show-that-identical-names-share-an-instance"></a><span data-ttu-id="8202f-116">Exemplo: criar objetos e mostrar que nomes idênticos compartilham uma instância</span><span class="sxs-lookup"><span data-stu-id="8202f-116">Example: Create objects and show that identical names share an instance</span></span>

<span data-ttu-id="8202f-117">O código a seguir cria alguns objetos de <xref:System.Xml.Linq.XElement> e demonstrar-los que os nomes idênticos compartilham a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="8202f-117">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>

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

<span data-ttu-id="8202f-118">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="8202f-118">This example produces the following output:</span></span>

```output
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

<span data-ttu-id="8202f-119">Como mencionado anteriormente, a vantagem de objetos atomizados é que quando você usa um dos métodos do eixo que recebem <xref:System.Xml.Linq.XName> como um parâmetro, o método do eixo só precisa determinar que dois nomes referenciam a mesma instância para selecionar os elementos desejados.</span><span class="sxs-lookup"><span data-stu-id="8202f-119">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>

<span data-ttu-id="8202f-120">O exemplo a seguir <xref:System.Xml.Linq.XName> passa a chamada de método <xref:System.Xml.Linq.XContainer.Descendants%2A> , que tem em melhor desempenho devido ao padrão de atomização.</span><span class="sxs-lookup"><span data-stu-id="8202f-120">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>

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

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e

For Each z As var In query
    Console.WriteLine(z)
Next
```

<span data-ttu-id="8202f-121">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="8202f-121">This example produces the following output:</span></span>

```xml
<C1>1</C1>
<C1>1</C1>
```
