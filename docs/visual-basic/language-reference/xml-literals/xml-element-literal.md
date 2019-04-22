---
title: Literal do elemento XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: 7bd47d2461ba86dfbd1d5ff5993382914116f9ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842246"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="306d6-102">Literal do elemento XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="306d6-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="306d6-103">Um literal que representa um <xref:System.Xml.Linq.XElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="306d6-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="306d6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="306d6-104">Syntax</span></span>  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a><span data-ttu-id="306d6-105">Partes</span><span class="sxs-lookup"><span data-stu-id="306d6-105">Parts</span></span>  
  
-   `<`  
  
     <span data-ttu-id="306d6-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="306d6-106">Required.</span></span> <span data-ttu-id="306d6-107">Abre a marca do elemento inicial.</span><span class="sxs-lookup"><span data-stu-id="306d6-107">Opens the starting element tag.</span></span>  
  
-   `name`  
  
     <span data-ttu-id="306d6-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="306d6-108">Required.</span></span> <span data-ttu-id="306d6-109">Nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="306d6-109">Name of the element.</span></span> <span data-ttu-id="306d6-110">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="306d6-110">The format is one of the following:</span></span>  
  
    -   <span data-ttu-id="306d6-111">Texto literal para o nome do elemento do formulário `[ePrefix:]eName`, onde:</span><span class="sxs-lookup"><span data-stu-id="306d6-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>  
  
        |<span data-ttu-id="306d6-112">Parte</span><span class="sxs-lookup"><span data-stu-id="306d6-112">Part</span></span>|<span data-ttu-id="306d6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="306d6-113">Description</span></span>|  
        |---|---|  
        |`ePrefix`|<span data-ttu-id="306d6-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="306d6-114">Optional.</span></span> <span data-ttu-id="306d6-115">Prefixo de namespace XML para o elemento.</span><span class="sxs-lookup"><span data-stu-id="306d6-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="306d6-116">Deve ser um namespace XML global que é definido com um `Imports` instrução no arquivo ou no nível do projeto, ou um namespace XML local que está definido nesse elemento ou um elemento pai.</span><span class="sxs-lookup"><span data-stu-id="306d6-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`eName`|<span data-ttu-id="306d6-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="306d6-117">Required.</span></span> <span data-ttu-id="306d6-118">Nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="306d6-118">Name of the element.</span></span> <span data-ttu-id="306d6-119">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="306d6-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="306d6-120">-Texto literal.</span><span class="sxs-lookup"><span data-stu-id="306d6-120">-   Literal text.</span></span> <span data-ttu-id="306d6-121">Ver [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="306d6-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="306d6-122">-Expressão inserida do formulário `<%= eNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="306d6-122">-   Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="306d6-123">O tipo de `eNameExp` deve ser `String` ou um tipo que é implicitamente conversível para <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="306d6-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
  
    -   <span data-ttu-id="306d6-124">Expressão incorporada do formulário `<%= nameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="306d6-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="306d6-125">O tipo de `nameExp` deve ser `String` ou um tipo implicitamente conversível em <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="306d6-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="306d6-126">Uma expressão inserida não é permitida em uma marca de fechamento de um elemento.</span><span class="sxs-lookup"><span data-stu-id="306d6-126">An embedded expression is not allowed in a closing tag of an element.</span></span>  
  
-   `attributeList`  
  
     <span data-ttu-id="306d6-127">Opcional.</span><span class="sxs-lookup"><span data-stu-id="306d6-127">Optional.</span></span> <span data-ttu-id="306d6-128">Lista de atributos declarados no literal.</span><span class="sxs-lookup"><span data-stu-id="306d6-128">List of attributes declared in the literal.</span></span>  
  
     `attribute [ attribute ... ]`  
  
     <span data-ttu-id="306d6-129">Cada `attribute` tem uma das seguintes sintaxes:</span><span class="sxs-lookup"><span data-stu-id="306d6-129">Each `attribute` has one of the following syntaxes:</span></span>  
  
    -   <span data-ttu-id="306d6-130">Atribuição de atributos, do formulário `[aPrefix:]aName=aValue`, onde:</span><span class="sxs-lookup"><span data-stu-id="306d6-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>  
  
        |<span data-ttu-id="306d6-131">Parte</span><span class="sxs-lookup"><span data-stu-id="306d6-131">Part</span></span>|<span data-ttu-id="306d6-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="306d6-132">Description</span></span>|  
        |---|---|  
        |`aPrefix`|<span data-ttu-id="306d6-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="306d6-133">Optional.</span></span> <span data-ttu-id="306d6-134">Prefixo de namespace XML para o atributo.</span><span class="sxs-lookup"><span data-stu-id="306d6-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="306d6-135">Deve ser um namespace XML global que é definido com um `Imports` instrução ou um namespace XML local que está definido nesse elemento ou um elemento pai.</span><span class="sxs-lookup"><span data-stu-id="306d6-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`aName`|<span data-ttu-id="306d6-136">Necessário.</span><span class="sxs-lookup"><span data-stu-id="306d6-136">Required.</span></span> <span data-ttu-id="306d6-137">Nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="306d6-137">Name of the attribute.</span></span> <span data-ttu-id="306d6-138">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="306d6-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="306d6-139">-Texto literal.</span><span class="sxs-lookup"><span data-stu-id="306d6-139">-   Literal text.</span></span> <span data-ttu-id="306d6-140">Ver [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="306d6-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="306d6-141">-Expressão inserida do formulário `<%= aNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="306d6-141">-   Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="306d6-142">O tipo de `aNameExp` deve ser `String` ou um tipo que é implicitamente conversível para <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="306d6-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
        |`aValue`|<span data-ttu-id="306d6-143">Opcional.</span><span class="sxs-lookup"><span data-stu-id="306d6-143">Optional.</span></span> <span data-ttu-id="306d6-144">Valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="306d6-144">Value of the attribute.</span></span> <span data-ttu-id="306d6-145">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="306d6-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="306d6-146">-Texto literal entre aspas.</span><span class="sxs-lookup"><span data-stu-id="306d6-146">-   Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="306d6-147">-Expressão inserida do formulário `<%= aValueExp %>`.</span><span class="sxs-lookup"><span data-stu-id="306d6-147">-   Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="306d6-148">Qualquer tipo é permitido.</span><span class="sxs-lookup"><span data-stu-id="306d6-148">Any type is allowed.</span></span>|  
  
    -   <span data-ttu-id="306d6-149">Expressão incorporada do formulário `<%= aExp %>`.</span><span class="sxs-lookup"><span data-stu-id="306d6-149">Embedded expression of the form `<%= aExp %>`.</span></span>  
  
-   `/>`  
  
     <span data-ttu-id="306d6-150">Opcional.</span><span class="sxs-lookup"><span data-stu-id="306d6-150">Optional.</span></span> <span data-ttu-id="306d6-151">Indica que o elemento é um elemento vazio, sem conteúdo.</span><span class="sxs-lookup"><span data-stu-id="306d6-151">Indicates that the element is an empty element, without content.</span></span>  
  
-   `>`  
  
     <span data-ttu-id="306d6-152">Necessário.</span><span class="sxs-lookup"><span data-stu-id="306d6-152">Required.</span></span> <span data-ttu-id="306d6-153">Termina a marca do elemento iniciante ou vazio.</span><span class="sxs-lookup"><span data-stu-id="306d6-153">Ends the beginning or empty element tag.</span></span>  
  
-   `elementContents`  
  
     <span data-ttu-id="306d6-154">Opcional.</span><span class="sxs-lookup"><span data-stu-id="306d6-154">Optional.</span></span> <span data-ttu-id="306d6-155">Conteúdo do elemento.</span><span class="sxs-lookup"><span data-stu-id="306d6-155">Content of the element.</span></span>  
  
     `content [ content ... ]`  
  
     <span data-ttu-id="306d6-156">Cada `content` pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="306d6-156">Each `content` can be one of the following:</span></span>  
  
    -   <span data-ttu-id="306d6-157">Texto literal.</span><span class="sxs-lookup"><span data-stu-id="306d6-157">Literal text.</span></span> <span data-ttu-id="306d6-158">Todo o espaço em branco no `elementContents` torna-se significativos se houver qualquer texto literal.</span><span class="sxs-lookup"><span data-stu-id="306d6-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>  
  
    -   <span data-ttu-id="306d6-159">Expressão incorporada do formulário `<%= contentExp %>`.</span><span class="sxs-lookup"><span data-stu-id="306d6-159">Embedded expression of the form `<%= contentExp %>`.</span></span>  
  
    -   <span data-ttu-id="306d6-160">Elemento XML literal.</span><span class="sxs-lookup"><span data-stu-id="306d6-160">XML element literal.</span></span>  
  
    -   <span data-ttu-id="306d6-161">Literal de comentário XML.</span><span class="sxs-lookup"><span data-stu-id="306d6-161">XML comment literal.</span></span> <span data-ttu-id="306d6-162">Ver [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="306d6-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>  
  
    -   <span data-ttu-id="306d6-163">Instrução de processamento XML literal.</span><span class="sxs-lookup"><span data-stu-id="306d6-163">XML processing instruction literal.</span></span> <span data-ttu-id="306d6-164">Ver [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="306d6-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>  
  
    -   <span data-ttu-id="306d6-165">Literal XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="306d6-165">XML CDATA literal.</span></span> <span data-ttu-id="306d6-166">Ver [Literal CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="306d6-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>  
  
-   `</[name]>`  
  
     <span data-ttu-id="306d6-167">Opcional.</span><span class="sxs-lookup"><span data-stu-id="306d6-167">Optional.</span></span> <span data-ttu-id="306d6-168">Representa a marca de fechamento do elemento.</span><span class="sxs-lookup"><span data-stu-id="306d6-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="306d6-169">Opcional `name` parâmetro não é permitido quando ele é o resultado de uma expressão inserida.</span><span class="sxs-lookup"><span data-stu-id="306d6-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="306d6-170">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="306d6-170">Return Value</span></span>  
 <span data-ttu-id="306d6-171">Um objeto <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="306d6-171">An <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="306d6-172">Comentários</span><span class="sxs-lookup"><span data-stu-id="306d6-172">Remarks</span></span>  
 <span data-ttu-id="306d6-173">Você pode usar a sintaxe de literal do elemento XML para criar <xref:System.Xml.Linq.XElement> objetos em seu código.</span><span class="sxs-lookup"><span data-stu-id="306d6-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="306d6-174">Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="306d6-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="306d6-175">Esse recurso permite que você copie o conteúdo de um documento XML e colá-lo diretamente em um programa Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="306d6-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="306d6-176">Expressões inseridas do formulário `<%= exp %>` permitem que você adicione informações dinâmicas a um elemento XML literal.</span><span class="sxs-lookup"><span data-stu-id="306d6-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="306d6-177">Para obter mais informações, consulte [expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="306d6-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="306d6-178">O compilador do Visual Basic converte o literal de elemento XML em chamadas para o <xref:System.Xml.Linq.XElement.%23ctor%2A> construtor e, se necessário, o <xref:System.Xml.Linq.XAttribute.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="306d6-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="306d6-179">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="306d6-179">XML Namespaces</span></span>  
 <span data-ttu-id="306d6-180">Prefixos de namespace XML são úteis quando você tem que criar literais XML com elementos do mesmo namespace várias vezes em código.</span><span class="sxs-lookup"><span data-stu-id="306d6-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="306d6-181">Você pode usar prefixos de namespace XML globais, que você define usando a `Imports` instrução ou prefixos locais, que você define usando a `xmlns:xmlPrefix="xmlNamespace"` sintaxe de atributo.</span><span class="sxs-lookup"><span data-stu-id="306d6-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="306d6-182">Para obter mais informações, consulte [instrução Imports (Namespace de XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="306d6-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
 <span data-ttu-id="306d6-183">Acordo com as regras de escopo para namespaces XML, o prefixos locais têm precedência sobre os prefixos globais.</span><span class="sxs-lookup"><span data-stu-id="306d6-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="306d6-184">No entanto, se um literal XML define um namespace XML, esse namespace não está disponível para expressões que aparecem em uma expressão inserida.</span><span class="sxs-lookup"><span data-stu-id="306d6-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="306d6-185">A expressão inserida pode acessar somente o namespace XML global.</span><span class="sxs-lookup"><span data-stu-id="306d6-185">The embedded expression can access only the global XML namespace.</span></span>  
  
 <span data-ttu-id="306d6-186">O compilador do Visual Basic converte cada namespace XML global que é usado por um literal XML em uma definição de namespace local no código gerado.</span><span class="sxs-lookup"><span data-stu-id="306d6-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="306d6-187">Namespaces XML globais que não são usados não aparecem no código gerado.</span><span class="sxs-lookup"><span data-stu-id="306d6-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="306d6-188">Exemplo</span><span class="sxs-lookup"><span data-stu-id="306d6-188">Example</span></span>  
 <span data-ttu-id="306d6-189">O exemplo a seguir mostra como criar um elemento XML simples que tem dois elementos aninhados vazios.</span><span class="sxs-lookup"><span data-stu-id="306d6-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>  
  
 [!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]  
  
 <span data-ttu-id="306d6-190">O exemplo exibe o texto a seguir.</span><span class="sxs-lookup"><span data-stu-id="306d6-190">The example displays the following text.</span></span> <span data-ttu-id="306d6-191">Observe que o literal preserva a estrutura dos elementos vazios.</span><span class="sxs-lookup"><span data-stu-id="306d6-191">Notice that the literal preserves the structure of the empty elements.</span></span>  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a><span data-ttu-id="306d6-192">Exemplo</span><span class="sxs-lookup"><span data-stu-id="306d6-192">Example</span></span>  
 <span data-ttu-id="306d6-193">O exemplo a seguir mostra como usar expressões inseridas para nomear um elemento e criar atributos.</span><span class="sxs-lookup"><span data-stu-id="306d6-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>  
  
 [!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]  
  
 <span data-ttu-id="306d6-194">Esse código exibe o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="306d6-194">This code displays the following text:</span></span>  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a><span data-ttu-id="306d6-195">Exemplo</span><span class="sxs-lookup"><span data-stu-id="306d6-195">Example</span></span>  
 <span data-ttu-id="306d6-196">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="306d6-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="306d6-197">Em seguida, ele usa o prefixo do namespace para criar um literal XML e exibe o formulário final do elemento.</span><span class="sxs-lookup"><span data-stu-id="306d6-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]  
  
 <span data-ttu-id="306d6-198">Esse código exibe o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="306d6-198">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="306d6-199">Observe que o compilador converteu o prefixo do namespace XML global em uma definição de prefixo para o namespace XML.</span><span class="sxs-lookup"><span data-stu-id="306d6-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="306d6-200">O \<ns:middle > elemento redefine o prefixo de namespace XML para o \<ns:inner1 > elemento.</span><span class="sxs-lookup"><span data-stu-id="306d6-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="306d6-201">No entanto, o \<ns:inner2 > elemento usa o namespace definido pelo `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="306d6-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="306d6-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="306d6-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="306d6-203">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="306d6-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="306d6-204">Literal de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="306d6-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="306d6-205">Literal CDATA XML</span><span class="sxs-lookup"><span data-stu-id="306d6-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [<span data-ttu-id="306d6-206">Literais XML</span><span class="sxs-lookup"><span data-stu-id="306d6-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="306d6-207">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="306d6-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="306d6-208">Expressões Inseridas no XML</span><span class="sxs-lookup"><span data-stu-id="306d6-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="306d6-209">Instrução Imports (Namespace de XML)</span><span class="sxs-lookup"><span data-stu-id="306d6-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
