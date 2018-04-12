---
title: Literal do elemento XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: 32
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de5825a6af1dd1b93c3c85651125cf817dc564f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="5ff26-102">Literal do elemento XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ff26-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="5ff26-103">Um literal que representa um <xref:System.Xml.Linq.XElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="5ff26-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ff26-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ff26-104">Syntax</span></span>  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a><span data-ttu-id="5ff26-105">Partes</span><span class="sxs-lookup"><span data-stu-id="5ff26-105">Parts</span></span>  
  
-   `<`  
  
     <span data-ttu-id="5ff26-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5ff26-106">Required.</span></span> <span data-ttu-id="5ff26-107">Abre a marca do elemento inicial.</span><span class="sxs-lookup"><span data-stu-id="5ff26-107">Opens the starting element tag.</span></span>  
  
-   `name`  
  
     <span data-ttu-id="5ff26-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5ff26-108">Required.</span></span> <span data-ttu-id="5ff26-109">Nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="5ff26-109">Name of the element.</span></span> <span data-ttu-id="5ff26-110">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="5ff26-110">The format is one of the following:</span></span>  
  
    -   <span data-ttu-id="5ff26-111">Texto literal para o nome do elemento do formulário `[ePrefix:]eName`, onde:</span><span class="sxs-lookup"><span data-stu-id="5ff26-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>  
  
        |<span data-ttu-id="5ff26-112">Parte</span><span class="sxs-lookup"><span data-stu-id="5ff26-112">Part</span></span>|<span data-ttu-id="5ff26-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ff26-113">Description</span></span>|  
        |---|---|  
        |`ePrefix`|<span data-ttu-id="5ff26-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5ff26-114">Optional.</span></span> <span data-ttu-id="5ff26-115">Prefixo de namespace XML para o elemento.</span><span class="sxs-lookup"><span data-stu-id="5ff26-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="5ff26-116">Deve ser um namespace XML global que é definido com um `Imports` instrução no arquivo ou no nível de projeto, ou um namespace XML local que está definido nesse elemento ou um elemento pai.</span><span class="sxs-lookup"><span data-stu-id="5ff26-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`eName`|<span data-ttu-id="5ff26-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5ff26-117">Required.</span></span> <span data-ttu-id="5ff26-118">Nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="5ff26-118">Name of the element.</span></span> <span data-ttu-id="5ff26-119">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="5ff26-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="5ff26-120">-Texto literal.</span><span class="sxs-lookup"><span data-stu-id="5ff26-120">-   Literal text.</span></span> <span data-ttu-id="5ff26-121">Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5ff26-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="5ff26-122">-Expressão inserida do formulário `<%= eNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5ff26-122">-   Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="5ff26-123">O tipo de `eNameExp` devem ser `String` ou um tipo que é implicitamente conversível em <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="5ff26-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
  
    -   <span data-ttu-id="5ff26-124">Expressão inserida do formulário `<%= nameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5ff26-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="5ff26-125">O tipo de `nameExp` devem ser `String` ou um tipo implicitamente conversível para <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="5ff26-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="5ff26-126">Uma expressão inserida não é permitida em uma marca de fechamento de um elemento.</span><span class="sxs-lookup"><span data-stu-id="5ff26-126">An embedded expression is not allowed in a closing tag of an element.</span></span>  
  
-   `attributeList`  
  
     <span data-ttu-id="5ff26-127">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5ff26-127">Optional.</span></span> <span data-ttu-id="5ff26-128">Lista de atributos declarados no literal.</span><span class="sxs-lookup"><span data-stu-id="5ff26-128">List of attributes declared in the literal.</span></span>  
  
     `attribute [ attribute ... ]`  
  
     <span data-ttu-id="5ff26-129">Cada `attribute` tem uma das seguintes sintaxes:</span><span class="sxs-lookup"><span data-stu-id="5ff26-129">Each `attribute` has one of the following syntaxes:</span></span>  
  
    -   <span data-ttu-id="5ff26-130">Atribuição de atributos, do formulário `[aPrefix:]aName=aValue`, onde:</span><span class="sxs-lookup"><span data-stu-id="5ff26-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>  
  
        |<span data-ttu-id="5ff26-131">Parte</span><span class="sxs-lookup"><span data-stu-id="5ff26-131">Part</span></span>|<span data-ttu-id="5ff26-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ff26-132">Description</span></span>|  
        |---|---|  
        |`aPrefix`|<span data-ttu-id="5ff26-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5ff26-133">Optional.</span></span> <span data-ttu-id="5ff26-134">Prefixo de namespace XML para o atributo.</span><span class="sxs-lookup"><span data-stu-id="5ff26-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="5ff26-135">Deve ser um namespace XML global que é definido com um `Imports` instrução ou um namespace XML local que está definido nesse elemento ou um elemento pai.</span><span class="sxs-lookup"><span data-stu-id="5ff26-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`aName`|<span data-ttu-id="5ff26-136">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5ff26-136">Required.</span></span> <span data-ttu-id="5ff26-137">Nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="5ff26-137">Name of the attribute.</span></span> <span data-ttu-id="5ff26-138">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="5ff26-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="5ff26-139">-Texto literal.</span><span class="sxs-lookup"><span data-stu-id="5ff26-139">-   Literal text.</span></span> <span data-ttu-id="5ff26-140">Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5ff26-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="5ff26-141">-Expressão inserida do formulário `<%= aNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5ff26-141">-   Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="5ff26-142">O tipo de `aNameExp` devem ser `String` ou um tipo que é implicitamente conversível em <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="5ff26-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
        |`aValue`|<span data-ttu-id="5ff26-143">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5ff26-143">Optional.</span></span> <span data-ttu-id="5ff26-144">Valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="5ff26-144">Value of the attribute.</span></span> <span data-ttu-id="5ff26-145">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="5ff26-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="5ff26-146">-Texto literal, entre aspas.</span><span class="sxs-lookup"><span data-stu-id="5ff26-146">-   Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="5ff26-147">-Expressão inserida do formulário `<%= aValueExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5ff26-147">-   Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="5ff26-148">Qualquer tipo é permitido.</span><span class="sxs-lookup"><span data-stu-id="5ff26-148">Any type is allowed.</span></span>|  
  
    -   <span data-ttu-id="5ff26-149">Expressão inserida do formulário `<%= aExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5ff26-149">Embedded expression of the form `<%= aExp %>`.</span></span>  
  
-   `/>`  
  
     <span data-ttu-id="5ff26-150">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5ff26-150">Optional.</span></span> <span data-ttu-id="5ff26-151">Indica que o elemento é um elemento vazio, sem conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5ff26-151">Indicates that the element is an empty element, without content.</span></span>  
  
-   `>`  
  
     <span data-ttu-id="5ff26-152">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5ff26-152">Required.</span></span> <span data-ttu-id="5ff26-153">Termina a marca do elemento iniciante ou vazio.</span><span class="sxs-lookup"><span data-stu-id="5ff26-153">Ends the beginning or empty element tag.</span></span>  
  
-   `elementContents`  
  
     <span data-ttu-id="5ff26-154">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5ff26-154">Optional.</span></span> <span data-ttu-id="5ff26-155">Conteúdo do elemento.</span><span class="sxs-lookup"><span data-stu-id="5ff26-155">Content of the element.</span></span>  
  
     `content [ content ... ]`  
  
     <span data-ttu-id="5ff26-156">Cada `content` pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="5ff26-156">Each `content` can be one of the following:</span></span>  
  
    -   <span data-ttu-id="5ff26-157">Texto literal.</span><span class="sxs-lookup"><span data-stu-id="5ff26-157">Literal text.</span></span> <span data-ttu-id="5ff26-158">Todo o espaço em branco em `elementContents` se tornar significativo se houver qualquer texto literal.</span><span class="sxs-lookup"><span data-stu-id="5ff26-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>  
  
    -   <span data-ttu-id="5ff26-159">Expressão inserida do formulário `<%= contentExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5ff26-159">Embedded expression of the form `<%= contentExp %>`.</span></span>  
  
    -   <span data-ttu-id="5ff26-160">Elemento XML literal.</span><span class="sxs-lookup"><span data-stu-id="5ff26-160">XML element literal.</span></span>  
  
    -   <span data-ttu-id="5ff26-161">Literal de comentário XML.</span><span class="sxs-lookup"><span data-stu-id="5ff26-161">XML comment literal.</span></span> <span data-ttu-id="5ff26-162">Consulte [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5ff26-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>  
  
    -   <span data-ttu-id="5ff26-163">Instrução de processamento XML literal.</span><span class="sxs-lookup"><span data-stu-id="5ff26-163">XML processing instruction literal.</span></span> <span data-ttu-id="5ff26-164">Consulte [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5ff26-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>  
  
    -   <span data-ttu-id="5ff26-165">Literal XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="5ff26-165">XML CDATA literal.</span></span> <span data-ttu-id="5ff26-166">Consulte [Literal CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5ff26-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>  
  
-   `</[name]>`  
  
     <span data-ttu-id="5ff26-167">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5ff26-167">Optional.</span></span> <span data-ttu-id="5ff26-168">Representa a marca de fechamento para o elemento.</span><span class="sxs-lookup"><span data-stu-id="5ff26-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="5ff26-169">Opcional `name` parâmetro não é permitido quando ele é o resultado de uma expressão inserida.</span><span class="sxs-lookup"><span data-stu-id="5ff26-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ff26-170">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5ff26-170">Return Value</span></span>  
 <span data-ttu-id="5ff26-171">Um objeto <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5ff26-171">An <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ff26-172">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ff26-172">Remarks</span></span>  
 <span data-ttu-id="5ff26-173">Você pode usar a sintaxe de literais de elemento XML para criar <xref:System.Xml.Linq.XElement> objetos no seu código.</span><span class="sxs-lookup"><span data-stu-id="5ff26-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ff26-174">Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="5ff26-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="5ff26-175">Esse recurso permite que você copiar o conteúdo de um documento XML e cole-o diretamente em um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programa.</span><span class="sxs-lookup"><span data-stu-id="5ff26-175">This feature enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 <span data-ttu-id="5ff26-176">Expressões inseridas do formulário `<%= exp %>` permitem que você adicione informações dinâmicas a um literal de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="5ff26-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="5ff26-177">Para obter mais informações, consulte [expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5ff26-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="5ff26-178">O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador converte o literal de elemento XML em chamadas para o <xref:System.Xml.Linq.XElement.%23ctor%2A> construtor e, se necessário, o <xref:System.Xml.Linq.XAttribute.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="5ff26-178">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="5ff26-179">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="5ff26-179">XML Namespaces</span></span>  
 <span data-ttu-id="5ff26-180">Prefixos de namespace XML são úteis quando você tem que criar literais XML com elementos do mesmo namespace muitas vezes no código.</span><span class="sxs-lookup"><span data-stu-id="5ff26-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="5ff26-181">Você pode usar prefixos de namespace XML global, que você define usando a `Imports` instrução ou prefixos locais, que você define usando a `xmlns:xmlPrefix="xmlNamespace"` sintaxe de atributo.</span><span class="sxs-lookup"><span data-stu-id="5ff26-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="5ff26-182">Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="5ff26-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
 <span data-ttu-id="5ff26-183">Conformidade com as regras de escopo para namespaces XML, prefixos locais têm precedência sobre prefixos globais.</span><span class="sxs-lookup"><span data-stu-id="5ff26-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="5ff26-184">No entanto, se um literal XML define um namespace XML, esse namespace não está disponível para expressões que aparecem em uma expressão inserida.</span><span class="sxs-lookup"><span data-stu-id="5ff26-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="5ff26-185">A expressão inserida pode acessar somente o namespace XML global.</span><span class="sxs-lookup"><span data-stu-id="5ff26-185">The embedded expression can access only the global XML namespace.</span></span>  
  
 <span data-ttu-id="5ff26-186">O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador converte cada namespace XML global que é usado por um XML literal em uma definição de namespace local no código gerado.</span><span class="sxs-lookup"><span data-stu-id="5ff26-186">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="5ff26-187">Namespaces XML globais que não são usados não aparecem no código gerado.</span><span class="sxs-lookup"><span data-stu-id="5ff26-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ff26-188">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ff26-188">Example</span></span>  
 <span data-ttu-id="5ff26-189">O exemplo a seguir mostra como criar um elemento XML simples que tem dois elementos aninhados vazios.</span><span class="sxs-lookup"><span data-stu-id="5ff26-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>  
  
 [!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 <span data-ttu-id="5ff26-190">O exemplo exibe o texto a seguir.</span><span class="sxs-lookup"><span data-stu-id="5ff26-190">The example displays the following text.</span></span> <span data-ttu-id="5ff26-191">Observe que o literal preserva a estrutura dos elementos vazios.</span><span class="sxs-lookup"><span data-stu-id="5ff26-191">Notice that the literal preserves the structure of the empty elements.</span></span>  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a><span data-ttu-id="5ff26-192">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ff26-192">Example</span></span>  
 <span data-ttu-id="5ff26-193">O exemplo a seguir mostra como usar expressões inseridas para nomear um elemento e criar atributos.</span><span class="sxs-lookup"><span data-stu-id="5ff26-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>  
  
 [!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 <span data-ttu-id="5ff26-194">Este código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="5ff26-194">This code displays the following text:</span></span>  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a><span data-ttu-id="5ff26-195">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ff26-195">Example</span></span>  
 <span data-ttu-id="5ff26-196">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="5ff26-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="5ff26-197">Em seguida, ele usa o prefixo de namespace para criar um literal XML e exibe a forma final do elemento.</span><span class="sxs-lookup"><span data-stu-id="5ff26-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]  
  
 <span data-ttu-id="5ff26-198">Este código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="5ff26-198">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="5ff26-199">Observe que o compilador converteu o prefixo do namespace XML global em uma definição de prefixo para o namespace XML.</span><span class="sxs-lookup"><span data-stu-id="5ff26-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="5ff26-200">O \<ns:middle > elemento redefine o prefixo de namespace XML para o \<ns:inner1 > elemento.</span><span class="sxs-lookup"><span data-stu-id="5ff26-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="5ff26-201">No entanto, o \<ns:inner2 > elemento usa o namespace definido pelo `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="5ff26-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff26-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ff26-202">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="5ff26-203">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="5ff26-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [<span data-ttu-id="5ff26-204">Literal de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="5ff26-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [<span data-ttu-id="5ff26-205">Literal CDATA XML</span><span class="sxs-lookup"><span data-stu-id="5ff26-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)  
 [<span data-ttu-id="5ff26-206">Literais XML</span><span class="sxs-lookup"><span data-stu-id="5ff26-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="5ff26-207">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ff26-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="5ff26-208">Expressões Inseridas no XML</span><span class="sxs-lookup"><span data-stu-id="5ff26-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [<span data-ttu-id="5ff26-209">Instrução Imports (Namespace de XML)</span><span class="sxs-lookup"><span data-stu-id="5ff26-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
