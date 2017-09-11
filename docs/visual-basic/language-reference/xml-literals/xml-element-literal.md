---
title: Literal do elemento XML (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralElement
dev_langs:
- VB
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: 32
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
ms.openlocfilehash: d5cf769a1e3f668652d1eb4551058deba38a8acf
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="5c2e9-102">Literal do elemento XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c2e9-102">XML Element Literal (Visual Basic)</span></span>
<span data-ttu-id="5c2e9-103">Um literal que representa um <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="5c2e9-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c2e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c2e9-104">Syntax</span></span>  
  
```  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a><span data-ttu-id="5c2e9-105">Partes</span><span class="sxs-lookup"><span data-stu-id="5c2e9-105">Parts</span></span>  
  
-   `<`  
  
     <span data-ttu-id="5c2e9-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-106">Required.</span></span> <span data-ttu-id="5c2e9-107">Abre a marca do elemento inicial.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-107">Opens the starting element tag.</span></span>  
  
-   `name`  
  
     <span data-ttu-id="5c2e9-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-108">Required.</span></span> <span data-ttu-id="5c2e9-109">Nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-109">Name of the element.</span></span> <span data-ttu-id="5c2e9-110">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="5c2e9-110">The format is one of the following:</span></span>  
  
    -   <span data-ttu-id="5c2e9-111">Texto literal para o nome do elemento do formulário [`ePrefix``:`]`eName`, onde:</span><span class="sxs-lookup"><span data-stu-id="5c2e9-111">Literal text for the element name, of the form [`ePrefix``:`]`eName`, where:</span></span>  
  
        |<span data-ttu-id="5c2e9-112">Parte</span><span class="sxs-lookup"><span data-stu-id="5c2e9-112">Part</span></span>|<span data-ttu-id="5c2e9-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c2e9-113">Description</span></span>|  
        |---|---|  
        |`ePrefix`|<span data-ttu-id="5c2e9-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-114">Optional.</span></span> <span data-ttu-id="5c2e9-115">Prefixo de namespace XML para o elemento.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="5c2e9-116">Deve ser um namespace XML global que é definido com um `Imports` instrução no arquivo ou no nível do projeto, ou um namespace XML local que está definido nesse elemento ou um elemento pai.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`eName`|<span data-ttu-id="5c2e9-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-117">Required.</span></span> <span data-ttu-id="5c2e9-118">Nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-118">Name of the element.</span></span> <span data-ttu-id="5c2e9-119">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="5c2e9-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="5c2e9-120">-Texto literal.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-120">-   Literal text.</span></span> <span data-ttu-id="5c2e9-121">Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5c2e9-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="5c2e9-122">-Expressão incorporada do formulário `<%=` e`NameExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-122">-   Embedded expression of the form `<%=` e`NameExp` `%>`.</span></span> <span data-ttu-id="5c2e9-123">O tipo de `eNameExp` deve ser `String` ou um tipo que é implicitamente conversível para <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="5c2e9-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
  
    -   <span data-ttu-id="5c2e9-124">Expressão incorporada do formulário `<%=` `nameExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-124">Embedded expression of the form `<%=` `nameExp` `%>`.</span></span> <span data-ttu-id="5c2e9-125">O tipo de `nameExp` deve ser `String` ou um tipo implicitamente conversível para <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="5c2e9-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="5c2e9-126">Uma expressão inserida não é permitida em uma marca de fechamento de um elemento.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-126">An embedded expression is not allowed in a closing tag of an element.</span></span>  
  
-   `attributeList`  
  
     <span data-ttu-id="5c2e9-127">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-127">Optional.</span></span> <span data-ttu-id="5c2e9-128">Lista de atributos declarados no literal.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-128">List of attributes declared in the literal.</span></span>  
  
     `attribute [ attribute ... ]`  
  
     <span data-ttu-id="5c2e9-129">Cada `attribute` tem uma das seguintes sintaxes:</span><span class="sxs-lookup"><span data-stu-id="5c2e9-129">Each `attribute` has one of the following syntaxes:</span></span>  
  
    -   <span data-ttu-id="5c2e9-130">Atribuição de atributos, do formulário [`aPrefix``:`]`aName``=``aValue`, onde:</span><span class="sxs-lookup"><span data-stu-id="5c2e9-130">Attribute assignment, of the form [`aPrefix``:`]`aName``=``aValue`, where:</span></span>  
  
        |<span data-ttu-id="5c2e9-131">Parte</span><span class="sxs-lookup"><span data-stu-id="5c2e9-131">Part</span></span>|<span data-ttu-id="5c2e9-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c2e9-132">Description</span></span>|  
        |---|---|  
        |`aPrefix`|<span data-ttu-id="5c2e9-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-133">Optional.</span></span> <span data-ttu-id="5c2e9-134">Prefixo de namespace XML para o atributo.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="5c2e9-135">Deve ser um namespace XML global que é definido com um `Imports` instrução ou um namespace XML local que está definido nesse elemento ou um elemento pai.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`aName`|<span data-ttu-id="5c2e9-136">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-136">Required.</span></span> <span data-ttu-id="5c2e9-137">Nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-137">Name of the attribute.</span></span> <span data-ttu-id="5c2e9-138">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="5c2e9-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="5c2e9-139">-Texto literal.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-139">-   Literal text.</span></span> <span data-ttu-id="5c2e9-140">Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5c2e9-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="5c2e9-141">-Expressão incorporada do formulário `<%=` `aNameExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-141">-   Embedded expression of the form `<%=` `aNameExp` `%>`.</span></span> <span data-ttu-id="5c2e9-142">O tipo de `aNameExp` deve ser `String` ou um tipo que é implicitamente conversível para <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="5c2e9-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
        |`aValue`|<span data-ttu-id="5c2e9-143">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-143">Optional.</span></span> <span data-ttu-id="5c2e9-144">Valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-144">Value of the attribute.</span></span> <span data-ttu-id="5c2e9-145">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="5c2e9-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="5c2e9-146">-Texto literal, entre aspas.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-146">-   Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="5c2e9-147">-Expressão incorporada do formulário `<%=` `aValueExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-147">-   Embedded expression of the form `<%=` `aValueExp` `%>`.</span></span> <span data-ttu-id="5c2e9-148">Qualquer tipo é permitido.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-148">Any type is allowed.</span></span>|  
  
    -   <span data-ttu-id="5c2e9-149">Expressão incorporada do formulário `<%=` `aExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-149">Embedded expression of the form `<%=` `aExp` `%>`.</span></span>  
  
-   `/>`  
  
     <span data-ttu-id="5c2e9-150">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-150">Optional.</span></span> <span data-ttu-id="5c2e9-151">Indica que o elemento é um elemento vazio, sem conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-151">Indicates that the element is an empty element, without content.</span></span>  
  
-   `>`  
  
     <span data-ttu-id="5c2e9-152">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-152">Required.</span></span> <span data-ttu-id="5c2e9-153">Finaliza a marca do elemento iniciante ou vazio.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-153">Ends the beginning or empty element tag.</span></span>  
  
-   `elementContents`  
  
     <span data-ttu-id="5c2e9-154">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-154">Optional.</span></span> <span data-ttu-id="5c2e9-155">Conteúdo do elemento.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-155">Content of the element.</span></span>  
  
     `content [ content ... ]`  
  
     <span data-ttu-id="5c2e9-156">Cada `content` pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="5c2e9-156">Each `content` can be one of the following:</span></span>  
  
    -   <span data-ttu-id="5c2e9-157">Texto literal.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-157">Literal text.</span></span> <span data-ttu-id="5c2e9-158">Todo o espaço em branco em `elementContents` torna-se significativos se houver qualquer texto literal.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>  
  
    -   <span data-ttu-id="5c2e9-159">Expressão incorporada do formulário `<%=` `contentExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-159">Embedded expression of the form `<%=` `contentExp` `%>`.</span></span>  
  
    -   <span data-ttu-id="5c2e9-160">Elemento XML literal.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-160">XML element literal.</span></span>  
  
    -   <span data-ttu-id="5c2e9-161">Literal de comentário XML.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-161">XML comment literal.</span></span> <span data-ttu-id="5c2e9-162">Consulte [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5c2e9-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>  
  
    -   <span data-ttu-id="5c2e9-163">Instrução de processamento XML literal.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-163">XML processing instruction literal.</span></span> <span data-ttu-id="5c2e9-164">Consulte [Literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5c2e9-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>  
  
    -   <span data-ttu-id="5c2e9-165">Literal XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-165">XML CDATA literal.</span></span> <span data-ttu-id="5c2e9-166">Consulte [Literal CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5c2e9-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>  
  
-   <span data-ttu-id="5c2e9-167">`</`[`name`]`>`</span><span class="sxs-lookup"><span data-stu-id="5c2e9-167">`</`[`name`]`>`</span></span>  
  
     <span data-ttu-id="5c2e9-168">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-168">Optional.</span></span> <span data-ttu-id="5c2e9-169">Representa a marca de fechamento do elemento.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-169">Represents the closing tag for the element.</span></span> <span data-ttu-id="5c2e9-170">Opcional `name` parâmetro não é permitido quando ele é o resultado de uma expressão inserida.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-170">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c2e9-171">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5c2e9-171">Return Value</span></span>  
 <span data-ttu-id="5c2e9-172">Um <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="5c2e9-172">An <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c2e9-173">Comentários</span><span class="sxs-lookup"><span data-stu-id="5c2e9-173">Remarks</span></span>  
 <span data-ttu-id="5c2e9-174">Você pode usar a sintaxe de literal de elemento XML para criar <xref:System.Xml.Linq.XElement>objetos no seu código.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="5c2e9-174">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c2e9-175">Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-175">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="5c2e9-176">Esse recurso permite que você copiar o conteúdo de um documento XML e colá-lo diretamente em um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-176">This feature enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="5c2e9-177">Expressões inseridas do formulário `<%=` `exp` `%>` permitem que você adicione informações dinâmicas a um literal de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-177">Embedded expressions of the form `<%=` `exp` `%>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="5c2e9-178">Para obter mais informações, consulte [expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5c2e9-178">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="5c2e9-179">O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte o literal de elemento XML em chamadas para o <xref:System.Xml.Linq.XElement.%23ctor%2A>construtor e, se necessário, o <xref:System.Xml.Linq.XAttribute.%23ctor%2A>construtor.</xref:System.Xml.Linq.XAttribute.%23ctor%2A> </xref:System.Xml.Linq.XElement.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="5c2e9-179">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="5c2e9-180">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="5c2e9-180">XML Namespaces</span></span>  
 <span data-ttu-id="5c2e9-181">Prefixos de namespace XML são úteis quando você tem que criar literais XML com elementos do mesmo namespace muitas vezes no código.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-181">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="5c2e9-182">Você pode usar prefixos de namespace XML global, que você define usando a `Imports` instrução ou prefixos locais, que você define usando a `xmlns:``xmlPrefix`= "`xmlNamespace`" sintaxe de atributo.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-182">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:``xmlPrefix`="`xmlNamespace`" attribute syntax.</span></span> <span data-ttu-id="5c2e9-183">Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="5c2e9-183">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
 <span data-ttu-id="5c2e9-184">De acordo com as regras de escopo para namespaces XML, prefixos locais têm precedência sobre prefixos globais.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-184">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="5c2e9-185">No entanto, se um literal XML define um namespace XML, esse namespace não está disponível para expressões que aparecem em uma expressão inserida.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-185">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="5c2e9-186">A expressão inserida pode acessar somente o namespace XML global.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-186">The embedded expression can access only the global XML namespace.</span></span>  
  
 <span data-ttu-id="5c2e9-187">O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte cada namespace XML global que é usado por um XML literal em uma definição de namespace local no código gerado.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-187">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="5c2e9-188">Namespaces XML globais que não são usados não aparecem no código gerado.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-188">Global XML namespaces that are not used do not appear in the generated code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c2e9-189">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c2e9-189">Example</span></span>  
 <span data-ttu-id="5c2e9-190">O exemplo a seguir mostra como criar um elemento XML simples que tem dois elementos aninhados vazios.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-190">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>  
  
 <span data-ttu-id="5c2e9-191">[!code-vb[20 VbXMLSamples](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5c2e9-191">[!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]</span></span>  
  
 <span data-ttu-id="5c2e9-192">O exemplo exibe o texto a seguir.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-192">The example displays the following text.</span></span> <span data-ttu-id="5c2e9-193">Observe que o literal preserva a estrutura dos elementos vazios.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-193">Notice that the literal preserves the structure of the empty elements.</span></span>  
  
```  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a><span data-ttu-id="5c2e9-194">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c2e9-194">Example</span></span>  
 <span data-ttu-id="5c2e9-195">O exemplo a seguir mostra como usar expressões inseridas para nomear um elemento e criar atributos.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-195">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>  
  
 <span data-ttu-id="5c2e9-196">[!code-vb[VbXMLSamples&#21;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5c2e9-196">[!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]</span></span>  
  
 <span data-ttu-id="5c2e9-197">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="5c2e9-197">This code displays the following text:</span></span>  
  
```  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a><span data-ttu-id="5c2e9-198">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c2e9-198">Example</span></span>  
 <span data-ttu-id="5c2e9-199">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-199">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="5c2e9-200">Em seguida, ele usa o prefixo de namespace para criar um literal XML e exibe o formulário final do elemento.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-200">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>  
  
 <span data-ttu-id="5c2e9-201">[!code-vb[VbXMLSamples&#22;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="5c2e9-201">[!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]</span></span>  
  
 <span data-ttu-id="5c2e9-202">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="5c2e9-202">This code displays the following text:</span></span>  
  
```  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="5c2e9-203">Observe que o compilador converteu o prefixo de namespace XML global em uma definição de prefixo para o namespace XML.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-203">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="5c2e9-204">O \<ns:middle > elemento redefine o prefixo de namespace XML para o \<ns:inner1 > elemento.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-204">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="5c2e9-205">No entanto, o \<ns:inner2 > elemento usa o namespace definido pelo `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="5c2e9-205">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c2e9-206">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c2e9-206">See Also</span></span>  
 <span data-ttu-id="5c2e9-207"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="5c2e9-207"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="5c2e9-208"> [Nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="5c2e9-208"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md) </span></span>  
<span data-ttu-id="5c2e9-209"> [Literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span><span class="sxs-lookup"><span data-stu-id="5c2e9-209"> [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span></span>  
<span data-ttu-id="5c2e9-210"> [Literal CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md) </span><span class="sxs-lookup"><span data-stu-id="5c2e9-210"> [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md) </span></span>  
<span data-ttu-id="5c2e9-211"> [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="5c2e9-211"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="5c2e9-212"> [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="5c2e9-212"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="5c2e9-213"> [Expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span><span class="sxs-lookup"><span data-stu-id="5c2e9-213"> [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span></span>  
<span data-ttu-id="5c2e9-214"> [Instrução Imports (Namespace de XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)</span><span class="sxs-lookup"><span data-stu-id="5c2e9-214"> [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)</span></span>
