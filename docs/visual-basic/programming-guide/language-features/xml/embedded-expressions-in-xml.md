---
title: "Expressões incorporadas no XML (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
dev_langs:
- VB
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d24a49f2fa6fd66fe6e4c7724bd4298d65fb7a59
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="ae8de-102">Expressões inseridas no XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae8de-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="ae8de-103">Expressões inseridas permitem criar literais XML que contêm expressões que são avaliadas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae8de-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="ae8de-104">A sintaxe para uma expressão inserida é `<%=` `expression` `%>`, que é a mesma que a sintaxe utilizada no [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae8de-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)].</span></span>  
  
 <span data-ttu-id="ae8de-105">Por exemplo, você pode criar um elemento XML literal, combinar expressões inseridas com conteúdo de texto literal.</span><span class="sxs-lookup"><span data-stu-id="ae8de-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 <span data-ttu-id="ae8de-106">[!code-vb[VbXMLSamples&#27;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae8de-106">[!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]</span></span>  
  
 <span data-ttu-id="ae8de-107">Se `isbnNumber` contém o número inteiro 12345 e `modifiedDate` contém a data 3/5/2006, quando esse código é executado, o valor de `book` é:</span><span class="sxs-lookup"><span data-stu-id="ae8de-107">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="ae8de-108">Validação e o local de expressão inserida</span><span class="sxs-lookup"><span data-stu-id="ae8de-108">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="ae8de-109">Expressões inseridas podem aparecer somente em determinados locais dentro de expressões literais XML.</span><span class="sxs-lookup"><span data-stu-id="ae8de-109">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="ae8de-110">Os controles de local de expressão que tipos de expressão podem retornar e como `Nothing` é tratado.</span><span class="sxs-lookup"><span data-stu-id="ae8de-110">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="ae8de-111">A tabela a seguir descreve os locais permitidos e tipos de expressões inseridas.</span><span class="sxs-lookup"><span data-stu-id="ae8de-111">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="ae8de-112">Local no literal</span><span class="sxs-lookup"><span data-stu-id="ae8de-112">Location in literal</span></span>|<span data-ttu-id="ae8de-113">Tipo de expressão</span><span class="sxs-lookup"><span data-stu-id="ae8de-113">Type of expression</span></span>|<span data-ttu-id="ae8de-114">Tratamento de`Nothing`</span><span class="sxs-lookup"><span data-stu-id="ae8de-114">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="ae8de-115">Nome do elemento XML</span><span class="sxs-lookup"><span data-stu-id="ae8de-115">XML element name</span></span>|<span data-ttu-id="ae8de-116"><xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="ae8de-116"><xref:System.Xml.Linq.XName></span></span>|<span data-ttu-id="ae8de-117">Erro</span><span class="sxs-lookup"><span data-stu-id="ae8de-117">Error</span></span>|  
|<span data-ttu-id="ae8de-118">Conteúdo de elemento XML</span><span class="sxs-lookup"><span data-stu-id="ae8de-118">XML element content</span></span>|<span data-ttu-id="ae8de-119">`Object`ou uma matriz de`Object`</span><span class="sxs-lookup"><span data-stu-id="ae8de-119">`Object` or array of `Object`</span></span>|<span data-ttu-id="ae8de-120">Ignorado</span><span class="sxs-lookup"><span data-stu-id="ae8de-120">Ignored</span></span>|  
|<span data-ttu-id="ae8de-121">Nome do atributo de elemento XML</span><span class="sxs-lookup"><span data-stu-id="ae8de-121">XML element attribute name</span></span>|<span data-ttu-id="ae8de-122"><xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="ae8de-122"><xref:System.Xml.Linq.XName></span></span>|<span data-ttu-id="ae8de-123">Erro, a menos que o valor do atributo também é`Nothing`</span><span class="sxs-lookup"><span data-stu-id="ae8de-123">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="ae8de-124">Valor de atributo do elemento XML</span><span class="sxs-lookup"><span data-stu-id="ae8de-124">XML element attribute value</span></span>|`Object`|<span data-ttu-id="ae8de-125">Declaração de atributo ignorada</span><span class="sxs-lookup"><span data-stu-id="ae8de-125">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="ae8de-126">Atributo de elemento XML</span><span class="sxs-lookup"><span data-stu-id="ae8de-126">XML element attribute</span></span>|<span data-ttu-id="ae8de-127"><xref:System.Xml.Linq.XAttribute>ou uma coleção de<xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="ae8de-127"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="ae8de-128">Ignorado</span><span class="sxs-lookup"><span data-stu-id="ae8de-128">Ignored</span></span>|  
|<span data-ttu-id="ae8de-129">Elemento de raiz do documento XML</span><span class="sxs-lookup"><span data-stu-id="ae8de-129">XML document root element</span></span>|<span data-ttu-id="ae8de-130"><xref:System.Xml.Linq.XElement>ou uma coleção de um <xref:System.Xml.Linq.XElement>objeto e um número arbitrário de <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment>objetos</xref:System.Xml.Linq.XComment> e</xref:System.Xml.Linq.XProcessingInstruction> </xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="ae8de-130"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="ae8de-131">Ignorado</span><span class="sxs-lookup"><span data-stu-id="ae8de-131">Ignored</span></span>|  
  
-   <span data-ttu-id="ae8de-132">Exemplo de uma expressão inserida em um nome de elemento XML:</span><span class="sxs-lookup"><span data-stu-id="ae8de-132">Example of an embedded expression in an XML element name:</span></span>  
  
     <span data-ttu-id="ae8de-133">[!code-vb[32 VbXMLSamples](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae8de-133">[!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]</span></span>  
  
-   <span data-ttu-id="ae8de-134">Exemplo de uma expressão inserida no conteúdo de um elemento XML:</span><span class="sxs-lookup"><span data-stu-id="ae8de-134">Example of an embedded expression in the content of an XML element:</span></span>  
  
     <span data-ttu-id="ae8de-135">[!code-vb[33 VbXMLSamples](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae8de-135">[!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]</span></span>  
  
-   <span data-ttu-id="ae8de-136">Exemplo de uma expressão inserida em um nome de atributo do elemento XML:</span><span class="sxs-lookup"><span data-stu-id="ae8de-136">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     <span data-ttu-id="ae8de-137">[!code-vb[VbXMLSamples&#34;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae8de-137">[!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]</span></span>  
  
-   <span data-ttu-id="ae8de-138">Exemplo de uma expressão inserida em um valor de atributo do elemento XML:</span><span class="sxs-lookup"><span data-stu-id="ae8de-138">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     <span data-ttu-id="ae8de-139">[!code-vb[VbXMLSamples&#35;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae8de-139">[!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]</span></span>  
  
-   <span data-ttu-id="ae8de-140">Exemplo de uma expressão inserida em um atributo de elemento XML:</span><span class="sxs-lookup"><span data-stu-id="ae8de-140">Example of an embedded expression in an XML element attribute:</span></span>  
  
     <span data-ttu-id="ae8de-141">[!code-vb[VbXMLSamples&#36;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae8de-141">[!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]</span></span>  
  
-   <span data-ttu-id="ae8de-142">Exemplo de uma expressão inserida em um elemento raiz do documento XML:</span><span class="sxs-lookup"><span data-stu-id="ae8de-142">Example of an embedded expression in an XML document root element:</span></span>  
  
     <span data-ttu-id="ae8de-143">[!code-vb[VbXMLSamples&#37;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae8de-143">[!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]</span></span>  
  
 <span data-ttu-id="ae8de-144">Se você habilitar `Option Strict`, o compilador verifica se o tipo de cada expressão inserida se expande para o tipo solicitado.</span><span class="sxs-lookup"><span data-stu-id="ae8de-144">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="ae8de-145">A única exceção é para o elemento raiz de um documento XML, que é verificado quando o código é executado.</span><span class="sxs-lookup"><span data-stu-id="ae8de-145">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="ae8de-146">Se você compilar sem `Option Strict`, você pode inserir expressões do tipo `Object` e seu tipo é verificado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae8de-146">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="ae8de-147">Em locais onde o conteúdo é opcional, que contêm expressões incorporadas `Nothing` são ignorados.</span><span class="sxs-lookup"><span data-stu-id="ae8de-147">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="ae8de-148">Isso significa que você não precise verificar esse conteúdo de elemento, valores de atributos e elementos de matriz não são `Nothing` antes de usar um literal XML.</span><span class="sxs-lookup"><span data-stu-id="ae8de-148">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="ae8de-149">Necessário valores, como nomes de elementos e atributos, não podem ser `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ae8de-149">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="ae8de-150">Para obter mais informações sobre como usar uma expressão inserida em um determinado tipo de literal, consulte [Literal de documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [o Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="ae8de-150">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="ae8de-151">Regras de escopo</span><span class="sxs-lookup"><span data-stu-id="ae8de-151">Scoping Rules</span></span>  
 <span data-ttu-id="ae8de-152">O compilador converte cada XML literal em uma chamada de construtor para o tipo de literal apropriado.</span><span class="sxs-lookup"><span data-stu-id="ae8de-152">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="ae8de-153">O conteúdo literal e expressões incorporadas em um literal XML são passadas como argumentos para o construtor.</span><span class="sxs-lookup"><span data-stu-id="ae8de-153">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="ae8de-154">Isso significa que todos os [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] elementos de programação disponíveis para um literal XML também estão disponíveis para suas expressões inseridas.</span><span class="sxs-lookup"><span data-stu-id="ae8de-154">This means that all [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="ae8de-155">Um literal XML, você pode acessar o namespace XML prefixos declarados com o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="ae8de-155">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="ae8de-156">Você pode declarar um novo prefixo de namespace XML ou um prefixo de namespace XML existente, em um elemento por meio de sombra a `xmlns` atributo.</span><span class="sxs-lookup"><span data-stu-id="ae8de-156">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="ae8de-157">O novo namespace está disponível para os nós filho do elemento, mas não para literais XML em expressões inseridas.</span><span class="sxs-lookup"><span data-stu-id="ae8de-157">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae8de-158">Quando você declarar um prefixo de namespace XML usando o `xmlns` atributo namespace, o valor do atributo deve ser uma cadeia de caracteres constante.</span><span class="sxs-lookup"><span data-stu-id="ae8de-158">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="ae8de-159">Nesse sentido, usando o `xmlns` atributo é como usar o `Imports` declaração para declarar um namespace XML.</span><span class="sxs-lookup"><span data-stu-id="ae8de-159">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="ae8de-160">Você não pode usar uma expressão inserida para especificar o valor de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="ae8de-160">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae8de-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae8de-161">See Also</span></span>  
 <span data-ttu-id="ae8de-162">[Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="ae8de-162">[Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="ae8de-163"> [Literal de documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span><span class="sxs-lookup"><span data-stu-id="ae8de-163"> [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span></span>  
<span data-ttu-id="ae8de-164"> [Literal do elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="ae8de-164"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="ae8de-165"> [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ae8de-165"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="ae8de-166"> [Instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="ae8de-166"> [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="ae8de-167"> [Visão Geral dos Literais XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)</span><span class="sxs-lookup"><span data-stu-id="ae8de-167"> [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)</span></span>
