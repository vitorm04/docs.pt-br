---
title: Como recuperar o valor de um elemento (LINQ para XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 17a7dac464e1ec40db357194000f5745cdf2f3a8
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249201"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="b8532-102">Como recuperar o valor de um elemento (LINQ para XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b8532-102">How to retrieve the value of an element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b8532-103">Este tópico mostra como obter o valor de elementos.</span><span class="sxs-lookup"><span data-stu-id="b8532-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="b8532-104">Há duas maneiras principais de fazer isso.</span><span class="sxs-lookup"><span data-stu-id="b8532-104">There are two main ways to do this.</span></span> <span data-ttu-id="b8532-105">Uma maneira é converter <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> para o tipo desejado.</span><span class="sxs-lookup"><span data-stu-id="b8532-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="b8532-106">O operador de conversão explícita converte o conteúdo do elemento ou do atributo no tipo especificado e o atribui à sua variável.</span><span class="sxs-lookup"><span data-stu-id="b8532-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="b8532-107">Outra opção é usar a propriedade <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> ou a propriedade <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8532-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="b8532-108">Entretanto, com C#, a conversão geralmente é a melhor abordagem.</span><span class="sxs-lookup"><span data-stu-id="b8532-108">With C#, however, casting is generally the better approach.</span></span> <span data-ttu-id="b8532-109">Se você lançar o elemento ou atributo a um tipo de valor anulado, o código é mais simples de escrever ao recuperar o valor de um elemento (ou atributo) que pode ou não existir.</span><span class="sxs-lookup"><span data-stu-id="b8532-109">If you cast the element or attribute to a nullable value type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="b8532-110">O último exemplo deste tópico demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="b8532-110">The last example in this topic demonstrates this.</span></span> <span data-ttu-id="b8532-111">No entanto, você não pode definir o conteúdo de um elemento por meio de conversão, como faria usando a propriedade <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8532-111">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8532-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8532-112">Example</span></span>  
 <span data-ttu-id="b8532-113">Para recuperar o valor de um elemento, basta converter o objeto <xref:System.Xml.Linq.XElement> no tipo desejado.</span><span class="sxs-lookup"><span data-stu-id="b8532-113">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="b8532-114">Você sempre pode converter um elemento em uma cadeia de caracteres, como a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8532-114">You can always cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="b8532-115">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8532-115">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="b8532-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8532-116">Example</span></span>  
 <span data-ttu-id="b8532-117">Você também pode converter elementos em tipos que não sejam cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b8532-117">You can also cast elements to types other than string.</span></span> <span data-ttu-id="b8532-118">Por exemplo, se você tiver um elemento que contenha um número inteiro, poderá convertê-lo em `int`, como mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8532-118">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="b8532-119">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8532-119">This example produces the following output:</span></span>  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="b8532-120">fornece operadores de conversão explícita para os seguintes tipos de dados: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` e `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="b8532-120">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 <span data-ttu-id="b8532-121">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fornece os mesmos operadores de conversão para objetos <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b8532-121">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8532-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8532-122">Example</span></span>  
 <span data-ttu-id="b8532-123">É possível usar a propriedade <xref:System.Xml.Linq.XElement.Value%2A> para recuperar o conteúdo de um elemento:</span><span class="sxs-lookup"><span data-stu-id="b8532-123">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="b8532-124">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8532-124">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="b8532-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8532-125">Example</span></span>  
 <span data-ttu-id="b8532-126">Às vezes, você tenta recuperar o valor de um elemento mesmo quando não tem certeza de que ele existe.</span><span class="sxs-lookup"><span data-stu-id="b8532-126">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="b8532-127">Neste caso, quando você atribui o elemento lançado a um tipo de referência anulado ou tipo de valor anulado, `null`se o elemento não existir, a variável atribuída será definida apenas para .</span><span class="sxs-lookup"><span data-stu-id="b8532-127">In this case, when you assign the casted element to a nullable reference type, or nullable value type, if the element does not exist the assigned variable is just set to `null`.</span></span> <span data-ttu-id="b8532-128">O código a seguir mostra que quando o elemento pode ou não existir, é mais fácil de usar a conversão do que usar a propriedade <xref:System.Xml.Linq.XElement.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8532-128">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="b8532-129">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="b8532-129">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="b8532-130">Em geral, você pode criar um código mais simples ao usar a conversão para recuperar o conteúdo de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="b8532-130">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8532-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="b8532-131">See also</span></span>

- [<span data-ttu-id="b8532-132">Eixos do LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b8532-132">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
