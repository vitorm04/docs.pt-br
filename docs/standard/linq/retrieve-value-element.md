---
title: Como recuperar o valor de um elemento-LINQ to XML
description: 'Conheça as duas maneiras principais de obter o valor de um elemento ou atributo: Converta para o tipo desejado ou use as propriedades XElement. Value e XAttribute. Value.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 010af5db9ec991bfe0345c93def3241150aa15e2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552055"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml"></a><span data-ttu-id="f832c-103">Como recuperar o valor de um elemento (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f832c-103">How to retrieve the value of an element (LINQ to XML)</span></span>

<span data-ttu-id="f832c-104">Este artigo mostra como obter o valor dos elementos.</span><span class="sxs-lookup"><span data-stu-id="f832c-104">This article shows how to get the value of elements.</span></span> <span data-ttu-id="f832c-105">Há duas maneiras principais de obter o valor:</span><span class="sxs-lookup"><span data-stu-id="f832c-105">There are two main ways to get the value:</span></span>

- <span data-ttu-id="f832c-106">Converta um <xref:System.Xml.Linq.XElement> ou um <xref:System.Xml.Linq.XAttribute> para o tipo desejado.</span><span class="sxs-lookup"><span data-stu-id="f832c-106">Cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="f832c-107">O operador de conversão explícita converte o conteúdo do elemento ou do atributo no tipo especificado e o atribui à sua variável.</span><span class="sxs-lookup"><span data-stu-id="f832c-107">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span>

- <span data-ttu-id="f832c-108">Use as <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> Propriedades ou.</span><span class="sxs-lookup"><span data-stu-id="f832c-108">Use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> or <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="f832c-109">Você também pode definir o valor usando essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="f832c-109">You can also set the value using these properties.</span></span>

<span data-ttu-id="f832c-110">Com o C#, a conversão é geralmente a melhor abordagem.</span><span class="sxs-lookup"><span data-stu-id="f832c-110">With C#, casting is generally the better approach.</span></span> <span data-ttu-id="f832c-111">Se você converter o elemento ou atributo em um tipo de valor anulável, o código será mais simples de escrever ao recuperar o valor de um elemento (ou atributo) que pode não existir.</span><span class="sxs-lookup"><span data-stu-id="f832c-111">If you cast the element or attribute to a nullable value type, the code is simpler to write when retrieving the value of an element (or attribute) that may not exist.</span></span> <span data-ttu-id="f832c-112">O último exemplo neste artigo demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="f832c-112">The last example in this article demonstrates this.</span></span> <span data-ttu-id="f832c-113">No entanto, você não pode definir o conteúdo de um elemento por meio de conversão, como é possível através da <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="f832c-113">However, you can't set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="f832c-114">Com Visual Basic, a melhor abordagem é usar a <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="f832c-114">With Visual Basic, the better approach is to use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>

## <a name="string-cast-example"></a><span data-ttu-id="f832c-115">Exemplo de conversão de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f832c-115">String cast example</span></span>  

<span data-ttu-id="f832c-116">Para recuperar o valor de um elemento, converta o <xref:System.Xml.Linq.XElement> objeto para o tipo desejado.</span><span class="sxs-lookup"><span data-stu-id="f832c-116">To retrieve the value of an element, cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="f832c-117">Você pode converter um elemento em uma cadeia de caracteres da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f832c-117">You can cast an element to a string, as follows:</span></span>

```csharp
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);
Console.WriteLine("Value of e:" + (string)e);
```

```vb
Dim e As XElement = <StringElement>abcde</StringElement>
Console.WriteLine(e)
Console.WriteLine("Value of e:" & e.Value)
```

<span data-ttu-id="f832c-118">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="f832c-118">This example produces the following output:</span></span>

```output
<StringElement>abcde</StringElement>
Value of e:abcde
```

## <a name="integer-cast-example"></a><span data-ttu-id="f832c-119">Exemplo de conversão de inteiro</span><span class="sxs-lookup"><span data-stu-id="f832c-119">Integer cast example</span></span>  

<span data-ttu-id="f832c-120">Você também pode converter elementos em tipos que não sejam cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f832c-120">You can also cast elements to types other than string.</span></span> <span data-ttu-id="f832c-121">Por exemplo, se você tiver um elemento que contenha um número inteiro, poderá convertê-lo em `int`, como mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="f832c-121">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  

```csharp
XElement e = new XElement("Age", "44");
Console.WriteLine(e);
Console.WriteLine("Value of e:" + (int)e);
```

```vb
Dim e As XElement = <Age>44</Age>
Console.WriteLine(e)
Console.WriteLine("Value of e:" & CInt(e))
```

<span data-ttu-id="f832c-122">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="f832c-122">This example produces the following output:</span></span>

```output
<Age>44</Age>
Value of e:44
```

<span data-ttu-id="f832c-123">LINQ to XML fornece operadores de conversão explícitos para os seguintes tipos de dados:,,,,,,, `string` `bool` `bool?` `int` `int?` `uint` `uint?` `long` , `long?` , `ulong` , `ulong?` , `float` , `float?` , `double` , `double?` , `decimal` , `decimal?` , `DateTime` , `DateTime?` , `TimeSpan` , `TimeSpan?` , `GUID` e `GUID?` .</span><span class="sxs-lookup"><span data-stu-id="f832c-123">LINQ to XML provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>

<span data-ttu-id="f832c-124">LINQ to XML fornece os mesmos operadores de conversão para <xref:System.Xml.Linq.XAttribute> objetos.</span><span class="sxs-lookup"><span data-stu-id="f832c-124">LINQ to XML provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>

## <a name="value-property-example"></a><span data-ttu-id="f832c-125">Exemplo da propriedade Value</span><span class="sxs-lookup"><span data-stu-id="f832c-125">Value property example</span></span>

<span data-ttu-id="f832c-126">É possível usar a propriedade <xref:System.Xml.Linq.XElement.Value%2A> para recuperar o conteúdo de um elemento:</span><span class="sxs-lookup"><span data-stu-id="f832c-126">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>

```csharp
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);
Console.WriteLine("Value of e:" + e.Value);
```

```vb
Dim e As XElement = <StringElement>abcde</StringElement>
Console.WriteLine(e)
Console.WriteLine("Value of e:" & e.Value)
```

<span data-ttu-id="f832c-127">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="f832c-127">This example produces the following output:</span></span>

```output
<StringElement>abcde</StringElement>
Value of e:abcde
```

## <a name="element-might-not-exist-example"></a><span data-ttu-id="f832c-128">O elemento pode não existir exemplo</span><span class="sxs-lookup"><span data-stu-id="f832c-128">Element might not exist example</span></span>

<span data-ttu-id="f832c-129">Às vezes você tenta recuperar o valor de um elemento, mesmo que não tenha certeza se ele existe.</span><span class="sxs-lookup"><span data-stu-id="f832c-129">Sometimes you try to retrieve the value of an element even though you're not sure if it exists.</span></span> <span data-ttu-id="f832c-130">Nesse caso, quando você atribui o elemento convertido a um tipo de referência anulável ou tipo de valor anulável, se o elemento não existir, a variável atribuída será definida como `null` (C#) ou `nothing` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f832c-130">In this case, when you assign the casted element to a nullable reference type or nullable value type, if the element doesn't exist, the assigned variable is set to `null` (C#) or `nothing` (Visual Basic).</span></span> <span data-ttu-id="f832c-131">O código a seguir mostra que, quando o elemento pode não existir, é mais fácil usar a conversão do que usar a <xref:System.Xml.Linq.XElement.Value%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="f832c-131">The following code shows that when the element may not exist, it's easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("Child1", "child 1 content"),
    new XElement("Child2", "2")
);

// The following assignments show why it's easier to use
// casting when the element might or might not exist.

string c1 = (string)root.Element("Child1");
Console.WriteLine("c1:{0}", c1 == null ? "element doesn't exist" : c1);

int? c2 = (int?)root.Element("Child2");
Console.WriteLine("c2:{0}", c2 == null ? "element doesn't exist" : c2.ToString());

string c3 = (string)root.Element("Child3");
Console.WriteLine("c3:{0}", c3 == null ? "element doesn't exist" : c3);

int? c4 = (int?)root.Element("Child4");
Console.WriteLine("c4:{0}", c4 == null ? "element doesn't exist" : c4.ToString());

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
Console.WriteLine("v1:{0}", v1 == null ? "element doesn't exist" : v1);

XElement e2 = root.Element("Child2");
int? v2;
if (e2 == null)
    v2 = null;
else
    v2 = Int32.Parse(e2.Value);
Console.WriteLine("v2:{0}", v2 == null ? "element doesn't exist" : v2.ToString());

XElement e3 = root.Element("Child3");
string v3;
if (e3 == null)
    v3 = null;
else
    v3 = e3.Value;
Console.WriteLine("v3:{0}", v3 == null ? "element doesn't exist" : v3);

XElement e4 = root.Element("Child4");
int? v4;
if (e4 == null)
    v4 = null;
else
    v4 = Int32.Parse(e4.Value);
Console.WriteLine("v4:{0}", v4 == null ? "element doesn't exist" : v4.ToString());
```

```vb
Dim root As XElement = <Root>
                           <Child1>child 1 content</Child1>
                           <Child2>2</Child2>
                       </Root>

' The following assignments show why it's easier to use
' casting when the element might or might not exist.

Dim c1 As String = CStr(root.Element("Child1"))
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element doesn't exist", c1))

Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element doesn't exist", c2.ToString()))

Dim c3 As String = CStr(root.Element("Child3"))
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element doesn't exist", c3))

Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element doesn't exist", c4.ToString()))

Console.WriteLine()

' The following assignments show the required code when using
' the Value property when the attribute might or might not exist.
' Notice that this is more difficult than the casting approach.

Dim e1 As XElement = root.Element("Child1")
Dim v1 As String
If (e1 Is Nothing) Then
    v1 = Nothing
Else
    v1 = e1.Value
End If
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element doesn't exist", v1))

Dim e2 As XElement = root.Element("Child2")
Dim v2 As Nullable(Of Integer)
If (e2 Is Nothing) Then
    v2 = Nothing
Else
    v2 = e2.Value
End If
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element doesn't exist", v2))

Dim e3 As XElement = root.Element("Child3")
Dim v3 As String
If (e3 Is Nothing) Then
    v3 = Nothing
Else
    v3 = e3.Value
End If
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element doesn't exist", v3))

Dim e4 As XElement = root.Element("Child4")
Dim v4 As Nullable(Of Integer)
If (e4 Is Nothing) Then
    v4 = Nothing
Else
    v4 = e4.Value
End If
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element doesn't exist", v4))
```

<span data-ttu-id="f832c-132">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="f832c-132">This example produces the following output:</span></span>

```output
c1:child 1 content
c2:2
c3:element doesn't exist
c4:element doesn't exist

v1:child 1 content
v2:2
v3:element doesn't exist
v4:element doesn't exist
```

<span data-ttu-id="f832c-133">Em geral, você pode escrever um código mais simples por meio da conversão para recuperar o conteúdo de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="f832c-133">In general, you can write simpler code by casting to retrieve the contents of elements and attributes.</span></span>

## <a name="see-also"></a><span data-ttu-id="f832c-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="f832c-134">See also</span></span>

- [<span data-ttu-id="f832c-135">Visão geral dos eixos de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="f832c-135">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
