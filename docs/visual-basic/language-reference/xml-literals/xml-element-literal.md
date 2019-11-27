---
title: Literal do elemento XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6d900ca6868cfffe6b0e5b349321a79c5716c46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347024"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="8b703-102">Literal do elemento XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b703-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="8b703-103">Um literal que representa um objeto <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="8b703-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="8b703-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b703-104">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="8b703-105">Partes</span><span class="sxs-lookup"><span data-stu-id="8b703-105">Parts</span></span>

- `<`

  <span data-ttu-id="8b703-106">Necessária.</span><span class="sxs-lookup"><span data-stu-id="8b703-106">Required.</span></span> <span data-ttu-id="8b703-107">Abre a marca do elemento inicial.</span><span class="sxs-lookup"><span data-stu-id="8b703-107">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="8b703-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="8b703-108">Required.</span></span> <span data-ttu-id="8b703-109">Nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="8b703-109">Name of the element.</span></span> <span data-ttu-id="8b703-110">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="8b703-110">The format is one of the following:</span></span>

  - <span data-ttu-id="8b703-111">Texto literal para o nome do elemento, no formato `[ePrefix:]eName`, em que:</span><span class="sxs-lookup"><span data-stu-id="8b703-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="8b703-112">Parte</span><span class="sxs-lookup"><span data-stu-id="8b703-112">Part</span></span>|<span data-ttu-id="8b703-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b703-113">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="8b703-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8b703-114">Optional.</span></span> <span data-ttu-id="8b703-115">Prefixo do namespace XML para o elemento.</span><span class="sxs-lookup"><span data-stu-id="8b703-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="8b703-116">Deve ser um namespace XML global que é definido com uma instrução `Imports` no arquivo ou no nível do projeto, ou um namespace XML local que é definido neste elemento ou um elemento pai.</span><span class="sxs-lookup"><span data-stu-id="8b703-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="8b703-117">Necessária.</span><span class="sxs-lookup"><span data-stu-id="8b703-117">Required.</span></span> <span data-ttu-id="8b703-118">Nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="8b703-118">Name of the element.</span></span> <span data-ttu-id="8b703-119">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="8b703-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="8b703-120">-Texto literal.</span><span class="sxs-lookup"><span data-stu-id="8b703-120">- Literal text.</span></span> <span data-ttu-id="8b703-121">Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="8b703-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="8b703-122">-Expressão inserida do formulário `<%= eNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="8b703-122">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="8b703-123">O tipo de `eNameExp` deve ser `String` ou um tipo que seja implicitamente conversível para <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="8b703-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="8b703-124">Expressão inserida do formulário `<%= nameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="8b703-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="8b703-125">O tipo de `nameExp` deve ser `String` ou um tipo implicitamente conversível para <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="8b703-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="8b703-126">Uma expressão inserida não é permitida em uma marca de fechamento de um elemento.</span><span class="sxs-lookup"><span data-stu-id="8b703-126">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="8b703-127">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8b703-127">Optional.</span></span> <span data-ttu-id="8b703-128">Lista de atributos declarados no literal.</span><span class="sxs-lookup"><span data-stu-id="8b703-128">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="8b703-129">Cada `attribute` tem uma das seguintes sintaxes:</span><span class="sxs-lookup"><span data-stu-id="8b703-129">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="8b703-130">Atribuição de atributo, do formulário `[aPrefix:]aName=aValue`, em que:</span><span class="sxs-lookup"><span data-stu-id="8b703-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="8b703-131">Parte</span><span class="sxs-lookup"><span data-stu-id="8b703-131">Part</span></span>|<span data-ttu-id="8b703-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b703-132">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="8b703-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8b703-133">Optional.</span></span> <span data-ttu-id="8b703-134">Prefixo do namespace XML para o atributo.</span><span class="sxs-lookup"><span data-stu-id="8b703-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="8b703-135">Deve ser um namespace XML global que é definido com uma instrução `Imports` ou um namespace XML local que é definido neste elemento ou em um elemento pai.</span><span class="sxs-lookup"><span data-stu-id="8b703-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="8b703-136">Necessária.</span><span class="sxs-lookup"><span data-stu-id="8b703-136">Required.</span></span> <span data-ttu-id="8b703-137">Nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="8b703-137">Name of the attribute.</span></span> <span data-ttu-id="8b703-138">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="8b703-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="8b703-139">-Texto literal.</span><span class="sxs-lookup"><span data-stu-id="8b703-139">- Literal text.</span></span> <span data-ttu-id="8b703-140">Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="8b703-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="8b703-141">-Expressão inserida do formulário `<%= aNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="8b703-141">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="8b703-142">O tipo de `aNameExp` deve ser `String` ou um tipo que seja implicitamente conversível para <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="8b703-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="8b703-143">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8b703-143">Optional.</span></span> <span data-ttu-id="8b703-144">Valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="8b703-144">Value of the attribute.</span></span> <span data-ttu-id="8b703-145">O formato é um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="8b703-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="8b703-146">-Texto literal, entre aspas.</span><span class="sxs-lookup"><span data-stu-id="8b703-146">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="8b703-147">-Expressão inserida do formulário `<%= aValueExp %>`.</span><span class="sxs-lookup"><span data-stu-id="8b703-147">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="8b703-148">Qualquer tipo é permitido.</span><span class="sxs-lookup"><span data-stu-id="8b703-148">Any type is allowed.</span></span>|

  - <span data-ttu-id="8b703-149">Expressão inserida do formulário `<%= aExp %>`.</span><span class="sxs-lookup"><span data-stu-id="8b703-149">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="8b703-150">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8b703-150">Optional.</span></span> <span data-ttu-id="8b703-151">Indica que o elemento é um elemento vazio, sem conteúdo.</span><span class="sxs-lookup"><span data-stu-id="8b703-151">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="8b703-152">Necessária.</span><span class="sxs-lookup"><span data-stu-id="8b703-152">Required.</span></span> <span data-ttu-id="8b703-153">Termina a marca de elemento inicial ou vazia.</span><span class="sxs-lookup"><span data-stu-id="8b703-153">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="8b703-154">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8b703-154">Optional.</span></span> <span data-ttu-id="8b703-155">Conteúdo do elemento.</span><span class="sxs-lookup"><span data-stu-id="8b703-155">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="8b703-156">Cada `content` pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="8b703-156">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="8b703-157">Texto literal.</span><span class="sxs-lookup"><span data-stu-id="8b703-157">Literal text.</span></span> <span data-ttu-id="8b703-158">Todo o espaço em branco no `elementContents` se torna significativo se houver qualquer texto literal.</span><span class="sxs-lookup"><span data-stu-id="8b703-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="8b703-159">Expressão inserida do formulário `<%= contentExp %>`.</span><span class="sxs-lookup"><span data-stu-id="8b703-159">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="8b703-160">Literal de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="8b703-160">XML element literal.</span></span>

  - <span data-ttu-id="8b703-161">Literal de comentário XML.</span><span class="sxs-lookup"><span data-stu-id="8b703-161">XML comment literal.</span></span> <span data-ttu-id="8b703-162">Consulte [literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="8b703-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>

  - <span data-ttu-id="8b703-163">Literal de instrução de processamento XML.</span><span class="sxs-lookup"><span data-stu-id="8b703-163">XML processing instruction literal.</span></span> <span data-ttu-id="8b703-164">Consulte [literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="8b703-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="8b703-165">Literal XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="8b703-165">XML CDATA literal.</span></span> <span data-ttu-id="8b703-166">Consulte [literal XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="8b703-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="8b703-167">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8b703-167">Optional.</span></span> <span data-ttu-id="8b703-168">Representa a marca de fechamento do elemento.</span><span class="sxs-lookup"><span data-stu-id="8b703-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="8b703-169">O parâmetro opcional `name` não é permitido quando é o resultado de uma expressão inserida.</span><span class="sxs-lookup"><span data-stu-id="8b703-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="8b703-170">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8b703-170">Return Value</span></span>

<span data-ttu-id="8b703-171">Um objeto <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="8b703-171">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b703-172">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b703-172">Remarks</span></span>

<span data-ttu-id="8b703-173">Você pode usar a sintaxe literal do elemento XML para criar <xref:System.Xml.Linq.XElement> objetos em seu código.</span><span class="sxs-lookup"><span data-stu-id="8b703-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="8b703-174">Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="8b703-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="8b703-175">Esse recurso permite que você copie o conteúdo de um documento XML e cole-o diretamente em um programa Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8b703-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="8b703-176">Expressões inseridas do formulário `<%= exp %>` permitem que você adicione informações dinâmicas a um literal de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="8b703-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="8b703-177">Para obter mais informações, consulte [expressões inseridas em XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8b703-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="8b703-178">O compilador Visual Basic converte o literal do elemento XML em chamadas para o Construtor <xref:System.Xml.Linq.XElement.%23ctor%2A> e, se necessário, o Construtor <xref:System.Xml.Linq.XAttribute.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b703-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="8b703-179">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="8b703-179">XML Namespaces</span></span>

<span data-ttu-id="8b703-180">Os prefixos de namespace XML são úteis quando você precisa criar literais XML com elementos do mesmo namespace muitas vezes no código.</span><span class="sxs-lookup"><span data-stu-id="8b703-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="8b703-181">Você pode usar prefixos de namespace XML globais, que você define usando a instrução `Imports` ou prefixos locais, que você define usando a sintaxe de atributo `xmlns:xmlPrefix="xmlNamespace"`.</span><span class="sxs-lookup"><span data-stu-id="8b703-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="8b703-182">Para obter mais informações, consulte [instrução Imports (namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="8b703-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="8b703-183">De acordo com as regras de escopo para namespaces XML, os prefixos locais têm precedência sobre prefixos globais.</span><span class="sxs-lookup"><span data-stu-id="8b703-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="8b703-184">No entanto, se um literal XML definir um namespace XML, esse namespace não estará disponível para expressões que aparecem em uma expressão inserida.</span><span class="sxs-lookup"><span data-stu-id="8b703-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="8b703-185">A expressão inserida pode acessar apenas o namespace XML global.</span><span class="sxs-lookup"><span data-stu-id="8b703-185">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="8b703-186">O compilador Visual Basic converte cada namespace XML global que é usado por um literal XML em uma definição de namespace local no código gerado.</span><span class="sxs-lookup"><span data-stu-id="8b703-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="8b703-187">Namespaces XML globais que não são usados não aparecem no código gerado.</span><span class="sxs-lookup"><span data-stu-id="8b703-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="8b703-188">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b703-188">Example</span></span>

<span data-ttu-id="8b703-189">O exemplo a seguir mostra como criar um elemento XML simples que tem dois elementos vazios aninhados.</span><span class="sxs-lookup"><span data-stu-id="8b703-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="8b703-190">O exemplo exibe o texto a seguir.</span><span class="sxs-lookup"><span data-stu-id="8b703-190">The example displays the following text.</span></span> <span data-ttu-id="8b703-191">Observe que o literal preserva a estrutura dos elementos vazios.</span><span class="sxs-lookup"><span data-stu-id="8b703-191">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="8b703-192">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b703-192">Example</span></span>

<span data-ttu-id="8b703-193">O exemplo a seguir mostra como usar expressões inseridas para nomear um elemento e criar atributos.</span><span class="sxs-lookup"><span data-stu-id="8b703-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="8b703-194">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="8b703-194">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="8b703-195">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b703-195">Example</span></span>

<span data-ttu-id="8b703-196">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="8b703-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="8b703-197">Em seguida, ele usa o prefixo do namespace para criar um literal XML e exibe a forma final do elemento.</span><span class="sxs-lookup"><span data-stu-id="8b703-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="8b703-198">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="8b703-198">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="8b703-199">Observe que o compilador converteu o prefixo do namespace XML global em uma definição de prefixo para o namespace XML.</span><span class="sxs-lookup"><span data-stu-id="8b703-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="8b703-200">O elemento \<NS: Middle > redefine o prefixo do namespace XML para o elemento \<NS: inner1 >.</span><span class="sxs-lookup"><span data-stu-id="8b703-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="8b703-201">No entanto, o elemento \<NS: inner2 > usa o namespace definido pela instrução `Imports`.</span><span class="sxs-lookup"><span data-stu-id="8b703-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b703-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b703-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="8b703-203">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="8b703-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="8b703-204">Literal de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="8b703-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="8b703-205">Literal CDATA XML</span><span class="sxs-lookup"><span data-stu-id="8b703-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [<span data-ttu-id="8b703-206">Literais XML</span><span class="sxs-lookup"><span data-stu-id="8b703-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="8b703-207">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b703-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="8b703-208">Expressões Inseridas no XML</span><span class="sxs-lookup"><span data-stu-id="8b703-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="8b703-209">Instrução Imports (Namespace de XML)</span><span class="sxs-lookup"><span data-stu-id="8b703-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
