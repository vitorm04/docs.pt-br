---
title: Como localizar um elemento com um elemento filho específico-LINQ to XML
description: Localizar um elemento cujo elemento filho tenha um valor específico
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 2f97f920ce09222858a0a51eb52ffe0d58dba960
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678634"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-linq-to-xml"></a><span data-ttu-id="f26b4-103">Como localizar um elemento com um elemento filho específico (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f26b4-103">How to find an element with a specific child element (LINQ to XML)</span></span>

<span data-ttu-id="f26b4-104">Este artigo mostra como localizar um elemento cujo elemento filho tem um valor específico.</span><span class="sxs-lookup"><span data-stu-id="f26b4-104">This article shows how to find an element whose child element has a specific value.</span></span>

## <a name="example-find-an-element-whose-child-element-has-a-specific-value"></a><span data-ttu-id="f26b4-105">Exemplo: localizar um elemento cujo elemento filho tem um valor específico</span><span class="sxs-lookup"><span data-stu-id="f26b4-105">Example: Find an element whose child element has a specific value</span></span>

<span data-ttu-id="f26b4-106">O exemplo localiza o `Test` elemento cujo `CommandLine` elemento filho tem um valor de "Examp2.EXE".</span><span class="sxs-lookup"><span data-stu-id="f26b4-106">The example finds the `Test` element whose `CommandLine` child element has a value of "Examp2.EXE".</span></span> <span data-ttu-id="f26b4-107">O exemplo usa arquivo XML de exemplo de documento XML [: configuração de teste](sample-xml-file-test-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="f26b4-107">The example uses XML document [Sample XML file: Test configuration](sample-xml-file-test-configuration.md).</span></span>

```csharp
XElement root = XElement.Load("TestConfig.xml");
IEnumerable<XElement> tests =
    from el in root.Elements("Test")
    where (string)el.Element("CommandLine") == "Examp2.EXE"
    select el;
foreach (XElement el in tests)
    Console.WriteLine((string)el.Attribute("TestId"));
```

```vb
Dim root As XElement = XElement.Load("TestConfig.xml")
Dim tests As IEnumerable(Of XElement) = _
    From el In root.<Test> _
    Where el.<CommandLine>.Value = "Examp2.EXE" _
    Select el
For Each el as XElement In tests
    Console.WriteLine(el.@TestId)
Next
```

<span data-ttu-id="f26b4-108">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="f26b4-108">This example produces the following output:</span></span>

```output
0002
0006
```

<span data-ttu-id="f26b4-109">Observe que a versão Visual Basic do código usa a [Propriedade eixo filho XML](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), a [Propriedade eixo de atributo XML](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)e a [propriedade valor XML](../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="f26b4-109">Note that the Visual Basic version of the code uses the [XML Child axis property](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), the [XML Attribute axis property](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md), and the [XML Value property](../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>

## <a name="example-find-when-the-xml-is-in-a-namespace"></a><span data-ttu-id="f26b4-110">Exemplo: localizar quando o XML está em um namespace</span><span class="sxs-lookup"><span data-stu-id="f26b4-110">Example: Find when the XML is in a namespace</span></span>

<span data-ttu-id="f26b4-111">O exemplo a seguir faz o mesmo que o anterior, mas para XML que está em um namespace.</span><span class="sxs-lookup"><span data-stu-id="f26b4-111">The following example does the same as the previous one, but for XML that's in a namespace.</span></span> <span data-ttu-id="f26b4-112">O exemplo usa [arquivo XML de exemplo de documento XML: configuração de teste em um namespace](sample-xml-file-test-configuration-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="f26b4-112">The example uses XML document [Sample XML file: Test configuration in a namespace](sample-xml-file-test-configuration-namespace.md).</span></span>

<span data-ttu-id="f26b4-113">Para obter mais informações, consulte [visão geral de namespaces](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f26b4-113">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Load("TestConfigInNamespace.xml");
XNamespace ad = "http://www.adatum.com";
IEnumerable<XElement> tests =
    from el in root.Elements(ad + "Test")
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"
    select el;
foreach (XElement el in tests)
    Console.WriteLine((string)el.Attribute("TestId"));
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")
        Dim tests As IEnumerable(Of XElement) = _
            From el In root.<Test> _
            Where el.<CommandLine>.Value = "Examp2.EXE" _
            Select el
        For Each el As XElement In tests
            Console.WriteLine(el.@TestId)
        Next
    End Sub
End Module
```

<span data-ttu-id="f26b4-114">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="f26b4-114">This example produces the following output:</span></span>

```output
0002
0006
```

## <a name="see-also"></a><span data-ttu-id="f26b4-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="f26b4-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="f26b4-116">Visão geral de operadores de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="f26b4-116">Standard Query Operators Overview</span></span>](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f26b4-117">Operações de projeção</span><span class="sxs-lookup"><span data-stu-id="f26b4-117">Projection Operations</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
