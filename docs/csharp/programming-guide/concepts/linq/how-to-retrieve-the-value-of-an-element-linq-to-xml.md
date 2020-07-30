---
title: Como recuperar o valor de um elemento (LINQ to XML) (C#)
description: Saiba como obter o valor dos elementos. Veja exemplos usando a conversão de cadeia de caracteres, a conversão de inteiros e a propriedade Value.
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: eb750927d74c3068d7ab06caba9835110bd77a09
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301535"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="7395e-104">Como recuperar o valor de um elemento (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7395e-104">How to retrieve the value of an element (LINQ to XML) (C#)</span></span>

<span data-ttu-id="7395e-105">Este artigo mostra como obter o valor dos elementos.</span><span class="sxs-lookup"><span data-stu-id="7395e-105">This article shows how to get the value of elements.</span></span> <span data-ttu-id="7395e-106">Há duas maneiras principais de obter o valor:</span><span class="sxs-lookup"><span data-stu-id="7395e-106">There are two main ways to get the value:</span></span>

- <span data-ttu-id="7395e-107">Converta um <xref:System.Xml.Linq.XElement> ou um <xref:System.Xml.Linq.XAttribute> para o tipo desejado.</span><span class="sxs-lookup"><span data-stu-id="7395e-107">Cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="7395e-108">O operador de conversão explícita converte o conteúdo do elemento ou do atributo no tipo especificado e o atribui à sua variável.</span><span class="sxs-lookup"><span data-stu-id="7395e-108">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span>

- <span data-ttu-id="7395e-109">Use as <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> Propriedades ou.</span><span class="sxs-lookup"><span data-stu-id="7395e-109">Use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> or <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="7395e-110">Você também pode definir o valor usando essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="7395e-110">You can also set the value using these properties.</span></span>

<span data-ttu-id="7395e-111">Com o C#, a conversão é geralmente a melhor abordagem.</span><span class="sxs-lookup"><span data-stu-id="7395e-111">With C#, casting is generally the better approach.</span></span> <span data-ttu-id="7395e-112">Se você converter o elemento ou atributo em um tipo de valor anulável, o código será mais simples de escrever ao recuperar o valor de um elemento (ou atributo) que pode ou não existir.</span><span class="sxs-lookup"><span data-stu-id="7395e-112">If you cast the element or attribute to a nullable value type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="7395e-113">O [último exemplo](#element-might-not-exist-example) neste artigo demonstra que a conversão é mais simples no caso em que o elemento pode não existir.</span><span class="sxs-lookup"><span data-stu-id="7395e-113">The [last example](#element-might-not-exist-example) in this article demonstrates that casting is simpler in the case where the element might not exist.</span></span> <span data-ttu-id="7395e-114">No entanto, você não pode definir o conteúdo de um elemento por meio de conversão, como faria usando a propriedade <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7395e-114">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="string-cast-example"></a><span data-ttu-id="7395e-115">Exemplo de conversão de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7395e-115">String cast example</span></span>  
 <span data-ttu-id="7395e-116">Para recuperar o valor de um elemento, converta o <xref:System.Xml.Linq.XElement> objeto para o tipo desejado.</span><span class="sxs-lookup"><span data-stu-id="7395e-116">To retrieve the value of an element, cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="7395e-117">Você pode converter um elemento em uma cadeia de caracteres da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="7395e-117">You can cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="7395e-118">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="7395e-118">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a><span data-ttu-id="7395e-119">Exemplo de conversão de inteiro</span><span class="sxs-lookup"><span data-stu-id="7395e-119">Integer cast example</span></span>  
 <span data-ttu-id="7395e-120">Você também pode converter elementos em tipos que não sejam cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7395e-120">You can also cast elements to types other than string.</span></span> <span data-ttu-id="7395e-121">Por exemplo, se você tiver um elemento que contenha um número inteiro, poderá convertê-lo em `int`, como mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="7395e-121">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="7395e-122">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="7395e-122">This example produces the following output:</span></span>  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="7395e-123">fornece operadores de conversão explícita para os seguintes tipos de dados: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` e `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="7395e-123">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 <span data-ttu-id="7395e-124">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fornece os mesmos operadores de conversão para objetos <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7395e-124">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="value-property-example"></a><span data-ttu-id="7395e-125">Exemplo da propriedade Value</span><span class="sxs-lookup"><span data-stu-id="7395e-125">Value property example</span></span>  
 <span data-ttu-id="7395e-126">É possível usar a propriedade <xref:System.Xml.Linq.XElement.Value%2A> para recuperar o conteúdo de um elemento:</span><span class="sxs-lookup"><span data-stu-id="7395e-126">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="7395e-127">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="7395e-127">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a><span data-ttu-id="7395e-128">O elemento pode não existir exemplo</span><span class="sxs-lookup"><span data-stu-id="7395e-128">Element might not exist example</span></span>
 <span data-ttu-id="7395e-129">Às vezes você tenta recuperar o valor de um elemento, mesmo que não tenha certeza se ele existe.</span><span class="sxs-lookup"><span data-stu-id="7395e-129">Sometimes you try to retrieve the value of an element even though you're not sure if it exists.</span></span> <span data-ttu-id="7395e-130">Nesse caso, quando você atribui o elemento convertido a um tipo de referência anulável ou tipo de valor anulável, se o elemento não existir, a variável atribuída será definida como `null` .</span><span class="sxs-lookup"><span data-stu-id="7395e-130">In this case, when you assign the casted element to a nullable reference type or nullable value type, if the element does not exist, the assigned variable is set to `null`.</span></span> <span data-ttu-id="7395e-131">O código a seguir mostra que quando o elemento pode ou não existir, é mais fácil de usar a conversão do que usar a propriedade <xref:System.Xml.Linq.XElement.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="7395e-131">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 <span data-ttu-id="7395e-132">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="7395e-132">This code produces the following output:</span></span>  
  
```output  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 <span data-ttu-id="7395e-133">Em geral, você pode criar um código mais simples ao usar a conversão para recuperar o conteúdo de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="7395e-133">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7395e-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="7395e-134">See also</span></span>

- [<span data-ttu-id="7395e-135">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7395e-135">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
