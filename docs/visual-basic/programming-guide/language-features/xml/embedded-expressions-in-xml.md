---
title: Expressões inseridas no XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: f99735df2512fd4b1477bab9126e18f5afbbfa8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653514"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="47025-102">Expressões inseridas no XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47025-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="47025-103">Expressões inseridas permitem criar literais XML que contêm expressões que são avaliadas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="47025-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="47025-104">A sintaxe para uma expressão inserida é `<%=` `expression` `%>`, que é o mesmo que a sintaxe usada no [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="47025-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="47025-105">Por exemplo, você pode criar um elemento XML literal, combinando expressões inseridas com conteúdo de texto literal.</span><span class="sxs-lookup"><span data-stu-id="47025-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 <span data-ttu-id="47025-106">Se `isbnNumber` contém o número inteiro 12345 e `modifiedDate` contém a data 3/5/2006, quando esse código é executado, o valor de `book` é:</span><span class="sxs-lookup"><span data-stu-id="47025-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="47025-107">Validação e o local de expressão inserida</span><span class="sxs-lookup"><span data-stu-id="47025-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="47025-108">Expressões inseridas podem aparecer somente em determinados locais dentro de expressões literais de XML.</span><span class="sxs-lookup"><span data-stu-id="47025-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="47025-109">Os controles de localização de expressão que tipos de expressão podem retornar e como `Nothing` é tratado.</span><span class="sxs-lookup"><span data-stu-id="47025-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="47025-110">A tabela a seguir descreve os locais permitidos e tipos de expressões inseridas.</span><span class="sxs-lookup"><span data-stu-id="47025-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="47025-111">Local em literal</span><span class="sxs-lookup"><span data-stu-id="47025-111">Location in literal</span></span>|<span data-ttu-id="47025-112">Tipo de expressão</span><span class="sxs-lookup"><span data-stu-id="47025-112">Type of expression</span></span>|<span data-ttu-id="47025-113">Manipulação de `Nothing`</span><span class="sxs-lookup"><span data-stu-id="47025-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="47025-114">Nome do elemento XML</span><span class="sxs-lookup"><span data-stu-id="47025-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="47025-115">Erro</span><span class="sxs-lookup"><span data-stu-id="47025-115">Error</span></span>|  
|<span data-ttu-id="47025-116">Conteúdo de elemento XML</span><span class="sxs-lookup"><span data-stu-id="47025-116">XML element content</span></span>|<span data-ttu-id="47025-117">`Object` ou uma matriz de `Object`</span><span class="sxs-lookup"><span data-stu-id="47025-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="47025-118">Ignorado</span><span class="sxs-lookup"><span data-stu-id="47025-118">Ignored</span></span>|  
|<span data-ttu-id="47025-119">Nome do atributo de elemento XML</span><span class="sxs-lookup"><span data-stu-id="47025-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="47025-120">Erro, a menos que o valor do atributo também é `Nothing`</span><span class="sxs-lookup"><span data-stu-id="47025-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="47025-121">Valor de atributo do elemento XML</span><span class="sxs-lookup"><span data-stu-id="47025-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="47025-122">Declaração de atributo ignorada</span><span class="sxs-lookup"><span data-stu-id="47025-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="47025-123">Atributo de elemento XML</span><span class="sxs-lookup"><span data-stu-id="47025-123">XML element attribute</span></span>|<span data-ttu-id="47025-124"><xref:System.Xml.Linq.XAttribute> ou uma coleção de <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="47025-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="47025-125">Ignorado</span><span class="sxs-lookup"><span data-stu-id="47025-125">Ignored</span></span>|  
|<span data-ttu-id="47025-126">Elemento de raiz do documento XML</span><span class="sxs-lookup"><span data-stu-id="47025-126">XML document root element</span></span>|<span data-ttu-id="47025-127"><xref:System.Xml.Linq.XElement> ou uma coleção de um <xref:System.Xml.Linq.XElement> objeto e um número arbitrário de <xref:System.Xml.Linq.XProcessingInstruction> e <xref:System.Xml.Linq.XComment> objetos</span><span class="sxs-lookup"><span data-stu-id="47025-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="47025-128">Ignorado</span><span class="sxs-lookup"><span data-stu-id="47025-128">Ignored</span></span>|  
  
-   <span data-ttu-id="47025-129">Exemplo de uma expressão inserida em um nome de elemento XML:</span><span class="sxs-lookup"><span data-stu-id="47025-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   <span data-ttu-id="47025-130">Exemplo de uma expressão inserida no conteúdo de um elemento XML:</span><span class="sxs-lookup"><span data-stu-id="47025-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   <span data-ttu-id="47025-131">Exemplo de uma expressão inserida em um nome de atributo do elemento XML:</span><span class="sxs-lookup"><span data-stu-id="47025-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   <span data-ttu-id="47025-132">Exemplo de uma expressão inserida em um valor de atributo do elemento XML:</span><span class="sxs-lookup"><span data-stu-id="47025-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   <span data-ttu-id="47025-133">Exemplo de uma expressão inserida em um atributo de elemento XML:</span><span class="sxs-lookup"><span data-stu-id="47025-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   <span data-ttu-id="47025-134">Exemplo de uma expressão inserida em um elemento raiz do documento XML:</span><span class="sxs-lookup"><span data-stu-id="47025-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 <span data-ttu-id="47025-135">Se você habilitar `Option Strict`, o compilador verifica se o tipo de cada expressão inserida será ampliada para o tipo exigido.</span><span class="sxs-lookup"><span data-stu-id="47025-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="47025-136">A única exceção é para o elemento raiz de um documento XML, que é verificado quando o código é executado.</span><span class="sxs-lookup"><span data-stu-id="47025-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="47025-137">Se você compilar sem `Option Strict`, você pode inserir expressões do tipo `Object` e seu tipo é verificado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="47025-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="47025-138">Em locais onde o conteúdo é opcional, que contêm expressões incorporadas `Nothing` são ignorados.</span><span class="sxs-lookup"><span data-stu-id="47025-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="47025-139">Isso significa que você não precisa verificar esse conteúdo de elemento, valores de atributo, e os elementos de matriz não são `Nothing` antes de você usar um literal XML.</span><span class="sxs-lookup"><span data-stu-id="47025-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="47025-140">Necessário valores, como nomes de elemento e atributo, não podem ser `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="47025-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="47025-141">Para obter mais informações sobre como usar uma expressão inserida em um determinado tipo de literal, consulte [Literal de documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [o Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="47025-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="47025-142">Regras de escopo</span><span class="sxs-lookup"><span data-stu-id="47025-142">Scoping Rules</span></span>  
 <span data-ttu-id="47025-143">O compilador converte cada XML literal em uma chamada de construtor para o tipo de literal apropriado.</span><span class="sxs-lookup"><span data-stu-id="47025-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="47025-144">O conteúdo literal e expressões inseridas em um literal XML são passadas como argumentos para o construtor.</span><span class="sxs-lookup"><span data-stu-id="47025-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="47025-145">Isso significa que todos os elementos programação do Visual Basic disponíveis para um literal XML também estão disponíveis para suas expressões incorporadas.</span><span class="sxs-lookup"><span data-stu-id="47025-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="47025-146">Um literal XML, você pode acessar o namespace XML prefixos declarados com o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="47025-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="47025-147">Você pode declarar um novo prefixo de namespace XML, ou um prefixo de namespace XML existente, em um elemento por meio de sombra de `xmlns` atributo.</span><span class="sxs-lookup"><span data-stu-id="47025-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="47025-148">O novo namespace está disponível para os nós filho do elemento, mas não para literais XML em expressões inseridas.</span><span class="sxs-lookup"><span data-stu-id="47025-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47025-149">Quando você declara um prefixo de namespace XML usando o `xmlns` atributo de namespace, o valor do atributo deve ser uma cadeia de caracteres constante.</span><span class="sxs-lookup"><span data-stu-id="47025-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="47025-150">Nesse sentido, usando o `xmlns` atributo é como usar o `Imports` instrução para declarar um namespace XML.</span><span class="sxs-lookup"><span data-stu-id="47025-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="47025-151">Você não pode usar uma expressão inserida para especificar o valor do namespace XML.</span><span class="sxs-lookup"><span data-stu-id="47025-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47025-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47025-152">See Also</span></span>  
 [<span data-ttu-id="47025-153">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47025-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="47025-154">Literal de Documento XML</span><span class="sxs-lookup"><span data-stu-id="47025-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [<span data-ttu-id="47025-155">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="47025-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="47025-156">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="47025-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="47025-157">Instrução Imports (Tipo e Namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="47025-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="47025-158">Visão Geral dos Literais XML</span><span class="sxs-lookup"><span data-stu-id="47025-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
