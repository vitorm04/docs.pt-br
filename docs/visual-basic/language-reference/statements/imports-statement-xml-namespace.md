---
title: Instrução Imports (namespace XML)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: ba7475416d8a4e2eb3c892d457c03eeb695045eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604556"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="271a3-102">Instrução Imports (namespace XML)</span><span class="sxs-lookup"><span data-stu-id="271a3-102">Imports Statement (XML Namespace)</span></span>
<span data-ttu-id="271a3-103">Importa os prefixos de namespace XML para uso em literais XML e propriedades de eixo XML.</span><span class="sxs-lookup"><span data-stu-id="271a3-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="271a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="271a3-104">Syntax</span></span>  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a><span data-ttu-id="271a3-105">Partes</span><span class="sxs-lookup"><span data-stu-id="271a3-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="271a3-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="271a3-106">Optional.</span></span> <span data-ttu-id="271a3-107">A cadeia de caracteres pelo qual XML elementos e atributos podem fazer referência a `xmlNamespaceName`.</span><span class="sxs-lookup"><span data-stu-id="271a3-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="271a3-108">Se nenhum `xmlNamespacePrefix` é fornecido, o namespace XML importado é o namespace XML padrão.</span><span class="sxs-lookup"><span data-stu-id="271a3-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="271a3-109">Deve ser um identificador XML válido.</span><span class="sxs-lookup"><span data-stu-id="271a3-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="271a3-110">Para obter mais informações, consulte [nomes de declarado elementos e atributos XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="271a3-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>  
  
 `xmlNamespaceName`  
 <span data-ttu-id="271a3-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="271a3-111">Required.</span></span> <span data-ttu-id="271a3-112">A cadeia de caracteres que identifica o namespace XML que está sendo importado.</span><span class="sxs-lookup"><span data-stu-id="271a3-112">The string identifying the XML namespace being imported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="271a3-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="271a3-113">Remarks</span></span>  
 <span data-ttu-id="271a3-114">Você pode usar o `Imports` instrução para definir namespaces XML globais que você pode usar com literais XML e propriedades de eixo XML, ou como parâmetros passados para o `GetXmlNamespace` operador.</span><span class="sxs-lookup"><span data-stu-id="271a3-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="271a3-115">(Para obter informações sobre como usar o `Imports` instrução para importar um alias que pode ser usado onde nomes de tipo são usados em seu código, consulte [instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) A sintaxe para declarar um namespace XML usando o `Imports` instrução é idêntica à sintaxe usada em XML.</span><span class="sxs-lookup"><span data-stu-id="271a3-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="271a3-116">Portanto, você pode copiar uma declaração de namespace de um arquivo XML e usá-lo em um `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="271a3-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>  
  
 <span data-ttu-id="271a3-117">Prefixos de namespace XML são úteis quando você deseja criar repetidamente elementos XML que são do mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="271a3-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="271a3-118">O prefixo de namespace XML declarado com o `Imports` instrução é global no sentido de que ele esteja disponível para todo o código no arquivo.</span><span class="sxs-lookup"><span data-stu-id="271a3-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="271a3-119">Você pode usá-lo quando você cria literais de elemento XML e quando você acessar propriedades do eixo XML.</span><span class="sxs-lookup"><span data-stu-id="271a3-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="271a3-120">Para obter mais informações, consulte [o Literal de elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) e [propriedades de eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).</span><span class="sxs-lookup"><span data-stu-id="271a3-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).</span></span>  
  
 <span data-ttu-id="271a3-121">Se você definir um namespace XML global sem um prefixo de namespace (por exemplo, `Imports <xmlns="http://SomeNameSpace>"`), esse namespace é considerado o namespace XML padrão.</span><span class="sxs-lookup"><span data-stu-id="271a3-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="271a3-122">O namespace XML padrão é usado para qualquer literais de elemento XML ou propriedades de eixo de atributo XML que não especificam explicitamente um namespace.</span><span class="sxs-lookup"><span data-stu-id="271a3-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="271a3-123">O namespace padrão também será usado se o namespace especificado for o namespace vazio (ou seja, `xmlns=""`).</span><span class="sxs-lookup"><span data-stu-id="271a3-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="271a3-124">O namespace XML padrão não se aplica aos atributos XML em literais XML ou propriedades de eixo de atributo XML que não têm um namespace.</span><span class="sxs-lookup"><span data-stu-id="271a3-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>  
  
 <span data-ttu-id="271a3-125">Namespaces XML são definidos em um literal XML, que são chamados *local namespaces XML*, têm precedência sobre namespaces XML que são definidos pelo `Imports` instrução como global.</span><span class="sxs-lookup"><span data-stu-id="271a3-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="271a3-126">Namespaces XML que são definidos pelo `Imports` instrução têm precedência sobre namespaces XML importados para um projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="271a3-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="271a3-127">Se um literal XML define um namespace XML, esse namespaces local não se aplicam a expressões inseridas.</span><span class="sxs-lookup"><span data-stu-id="271a3-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>  
  
 <span data-ttu-id="271a3-128">Namespaces XML globais seguem as mesmas regras de escopo e definição que namespaces do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="271a3-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="271a3-129">Como resultado, você pode incluir um `Imports` instrução para definir um namespace XML global em qualquer lugar, você pode importar um namespace do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="271a3-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="271a3-130">Isso inclui arquivos de código e namespaces importados no nível do projeto.</span><span class="sxs-lookup"><span data-stu-id="271a3-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="271a3-131">Para obter informações sobre namespaces importados no nível de projeto, consulte [referências de página, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="271a3-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="271a3-132">Cada arquivo de origem pode conter qualquer número de `Imports` instruções.</span><span class="sxs-lookup"><span data-stu-id="271a3-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="271a3-133">Eles devem seguir declarações de opção, como o `Option Strict` instrução e eles devem preceder declarações de elemento de programação, como `Module` ou `Class` instruções.</span><span class="sxs-lookup"><span data-stu-id="271a3-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="271a3-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="271a3-134">Example</span></span>  
 <span data-ttu-id="271a3-135">O exemplo a seguir importa um namespace XML padrão e um namespace XML identificado com o prefixo `ns`.</span><span class="sxs-lookup"><span data-stu-id="271a3-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="271a3-136">Em seguida, cria literais XML que usam os dois namespaces.</span><span class="sxs-lookup"><span data-stu-id="271a3-136">It then creates XML literals that use both namespaces.</span></span>  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
 <span data-ttu-id="271a3-137">Este código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="271a3-137">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a><span data-ttu-id="271a3-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="271a3-138">Example</span></span>  
 <span data-ttu-id="271a3-139">O exemplo a seguir importa o prefixo de namespace XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="271a3-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="271a3-140">Em seguida, cria um literal XML que usa o prefixo de namespace e exibe a forma final do elemento.</span><span class="sxs-lookup"><span data-stu-id="271a3-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 <span data-ttu-id="271a3-141">Este código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="271a3-141">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="271a3-142">Observe que o compilador converteu o prefixo de namespace XML de um prefixo global para uma definição de prefixo local.</span><span class="sxs-lookup"><span data-stu-id="271a3-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="271a3-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="271a3-143">Example</span></span>  
 <span data-ttu-id="271a3-144">O exemplo a seguir importa o prefixo de namespace XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="271a3-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="271a3-145">Ele usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="271a3-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 <span data-ttu-id="271a3-146">Este código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="271a3-146">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="271a3-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="271a3-147">See Also</span></span>  
 [<span data-ttu-id="271a3-148">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="271a3-148">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="271a3-149">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="271a3-149">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="271a3-150">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="271a3-150">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [<span data-ttu-id="271a3-151">Operador GetXmlNamespace</span><span class="sxs-lookup"><span data-stu-id="271a3-151">GetXmlNamespace Operator</span></span>](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
