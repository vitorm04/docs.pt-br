---
title: Instrução Imports-namespace XML
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 52864e4d1c8183b6243025e72368d23627049c84
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351059"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="3e83c-102">Instrução Imports (namespace XML)</span><span class="sxs-lookup"><span data-stu-id="3e83c-102">Imports Statement (XML Namespace)</span></span>

<span data-ttu-id="3e83c-103">Importa prefixos de namespace XML para uso em literais XML e propriedades de eixo XML.</span><span class="sxs-lookup"><span data-stu-id="3e83c-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="3e83c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e83c-104">Syntax</span></span>

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a><span data-ttu-id="3e83c-105">Partes</span><span class="sxs-lookup"><span data-stu-id="3e83c-105">Parts</span></span>

`xmlNamespacePrefix`  
<span data-ttu-id="3e83c-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3e83c-106">Optional.</span></span> <span data-ttu-id="3e83c-107">A cadeia de caracteres pela qual os elementos e atributos XML podem se referir a `xmlNamespaceName`.</span><span class="sxs-lookup"><span data-stu-id="3e83c-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="3e83c-108">Se nenhum `xmlNamespacePrefix` for fornecido, o namespace XML importado será o namespace XML padrão.</span><span class="sxs-lookup"><span data-stu-id="3e83c-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="3e83c-109">Deve ser um identificador XML válido.</span><span class="sxs-lookup"><span data-stu-id="3e83c-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="3e83c-110">Para obter mais informações, consulte [nomes de elementos XML declarados e atributos](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="3e83c-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>

`xmlNamespaceName`  
<span data-ttu-id="3e83c-111">Necessária.</span><span class="sxs-lookup"><span data-stu-id="3e83c-111">Required.</span></span> <span data-ttu-id="3e83c-112">A cadeia de caracteres que identifica o namespace XML que está sendo importado.</span><span class="sxs-lookup"><span data-stu-id="3e83c-112">The string identifying the XML namespace being imported.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e83c-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e83c-113">Remarks</span></span>

<span data-ttu-id="3e83c-114">Você pode usar a instrução `Imports` para definir namespaces XML globais que você pode usar com literais XML e propriedades de eixo XML, ou como parâmetros passados para o operador `GetXmlNamespace`.</span><span class="sxs-lookup"><span data-stu-id="3e83c-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="3e83c-115">(Para obter informações sobre como usar a instrução `Imports` para importar um alias que pode ser usado onde os nomes de tipos são usados em seu código, consulte a [instrução Imports (namespace e tipo do .net)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) A sintaxe para declarar um namespace XML usando a instrução `Imports` é idêntica à sintaxe usada em XML.</span><span class="sxs-lookup"><span data-stu-id="3e83c-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="3e83c-116">Portanto, você pode copiar uma declaração de namespace de um arquivo XML e usá-la em uma instrução `Imports`.</span><span class="sxs-lookup"><span data-stu-id="3e83c-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>

<span data-ttu-id="3e83c-117">Os prefixos de namespace XML são úteis quando você deseja criar repetidamente elementos XML que são do mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="3e83c-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="3e83c-118">O prefixo de namespace XML declarado com a instrução `Imports` é global no sentido de que está disponível para todo o código no arquivo.</span><span class="sxs-lookup"><span data-stu-id="3e83c-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="3e83c-119">Você pode usá-lo ao criar literais de elemento XML e ao acessar as propriedades do eixo XML.</span><span class="sxs-lookup"><span data-stu-id="3e83c-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="3e83c-120">Para obter mais informações, consulte [literal do elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) e [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/index.md).</span><span class="sxs-lookup"><span data-stu-id="3e83c-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/index.md).</span></span>

<span data-ttu-id="3e83c-121">Se você definir um namespace XML global sem um prefixo de namespace (por exemplo, `Imports <xmlns="http://SomeNameSpace>"`), esse namespace será considerado o namespace XML padrão.</span><span class="sxs-lookup"><span data-stu-id="3e83c-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="3e83c-122">O namespace XML padrão é usado para quaisquer literais de elemento XML ou propriedades de eixo de atributo XML que não especificam explicitamente um namespace.</span><span class="sxs-lookup"><span data-stu-id="3e83c-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="3e83c-123">O namespace padrão também será usado se o namespace especificado for o namespace vazio (ou seja, `xmlns=""`).</span><span class="sxs-lookup"><span data-stu-id="3e83c-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="3e83c-124">O namespace XML padrão não se aplica a atributos XML em literais XML ou a propriedades do eixo de atributo XML que não têm um namespace.</span><span class="sxs-lookup"><span data-stu-id="3e83c-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>

<span data-ttu-id="3e83c-125">Namespaces XML que são definidos em um literal XML, que são chamados de *namespaces XML locais*, têm precedência sobre namespaces XML que são definidos pela instrução `Imports` como global.</span><span class="sxs-lookup"><span data-stu-id="3e83c-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="3e83c-126">Namespaces XML que são definidos pela instrução `Imports` têm precedência sobre namespaces XML importados para um projeto Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3e83c-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="3e83c-127">Se um literal XML definir um namespace XML, esse namespace local não se aplicará a expressões inseridas.</span><span class="sxs-lookup"><span data-stu-id="3e83c-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>

<span data-ttu-id="3e83c-128">Namespaces XML globais seguem as mesmas regras de escopo e definição que .NET Framework namespaces.</span><span class="sxs-lookup"><span data-stu-id="3e83c-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="3e83c-129">Como resultado, você pode incluir uma instrução `Imports` para definir um namespace XML global em qualquer lugar em que você possa importar um namespace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e83c-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="3e83c-130">Isso inclui arquivos de código e namespaces importados no nível do projeto.</span><span class="sxs-lookup"><span data-stu-id="3e83c-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="3e83c-131">Para obter informações sobre namespaces importados no nível do projeto, consulte [página de referências, designer de projeto (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3e83c-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="3e83c-132">Cada arquivo de origem pode conter qualquer número de instruções `Imports`.</span><span class="sxs-lookup"><span data-stu-id="3e83c-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="3e83c-133">Eles devem seguir as declarações de opção, como a instrução `Option Strict`, e devem preceder as declarações de elemento de programação, como `Module` ou `Class` instruções.</span><span class="sxs-lookup"><span data-stu-id="3e83c-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>

## <a name="example"></a><span data-ttu-id="3e83c-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e83c-134">Example</span></span>

<span data-ttu-id="3e83c-135">O exemplo a seguir importa um namespace XML padrão e um namespace XML identificado com o prefixo `ns`.</span><span class="sxs-lookup"><span data-stu-id="3e83c-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="3e83c-136">Em seguida, ele cria literais XML que usam ambos os namespaces.</span><span class="sxs-lookup"><span data-stu-id="3e83c-136">It then creates XML literals that use both namespaces.</span></span>

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

<span data-ttu-id="3e83c-137">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="3e83c-137">This code displays the following text:</span></span>

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a><span data-ttu-id="3e83c-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e83c-138">Example</span></span>

<span data-ttu-id="3e83c-139">O exemplo a seguir importa o prefixo do namespace XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="3e83c-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="3e83c-140">Em seguida, ele cria um literal XML que usa o prefixo do namespace e exibe a forma final do elemento.</span><span class="sxs-lookup"><span data-stu-id="3e83c-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="3e83c-141">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="3e83c-141">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="3e83c-142">Observe que o compilador converteu o prefixo de namespace XML de um prefixo global em uma definição de prefixo local.</span><span class="sxs-lookup"><span data-stu-id="3e83c-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>

## <a name="example"></a><span data-ttu-id="3e83c-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e83c-143">Example</span></span>

<span data-ttu-id="3e83c-144">O exemplo a seguir importa o prefixo do namespace XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="3e83c-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="3e83c-145">Em seguida, ele usa o prefixo do namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="3e83c-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

<span data-ttu-id="3e83c-146">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="3e83c-146">This code displays the following text:</span></span>

`Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="3e83c-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e83c-147">See also</span></span>

- [<span data-ttu-id="3e83c-148">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="3e83c-148">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="3e83c-149">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="3e83c-149">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="3e83c-150">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="3e83c-150">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="3e83c-151">Operador GetXmlNamespace</span><span class="sxs-lookup"><span data-stu-id="3e83c-151">GetXmlNamespace Operator</span></span>](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
