---
title: Nomes de elementos e atributos XML declarados (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 2221f2677183cf360fa82a4d73a679a8b68927d1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819678"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="baaa3-102">Nomes de elementos e atributos XML declarados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="baaa3-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="baaa3-103">Este tópico fornece diretrizes de Visual Basic para nomear elementos XML e atributos em literais XML.</span><span class="sxs-lookup"><span data-stu-id="baaa3-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="baaa3-104">Em um literal XML, você pode especificar um nome local ou um nome qualificado.</span><span class="sxs-lookup"><span data-stu-id="baaa3-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="baaa3-105">Um nome qualificado consiste em um prefixo de namespace XML, dois-pontos e um nome local.</span><span class="sxs-lookup"><span data-stu-id="baaa3-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="baaa3-106">Para obter mais informações sobre prefixos de namespace XML, consulte [Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="baaa3-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="baaa3-107">Regras</span><span class="sxs-lookup"><span data-stu-id="baaa3-107">Rules</span></span>  
 <span data-ttu-id="baaa3-108">Um nome local de um elemento ou atributo no Visual Basic deve seguir as regras a seguir.</span><span class="sxs-lookup"><span data-stu-id="baaa3-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
-   <span data-ttu-id="baaa3-109">Ele pode começar com um namespace.</span><span class="sxs-lookup"><span data-stu-id="baaa3-109">It can begin with a namespace.</span></span> <span data-ttu-id="baaa3-110">Ele deve começar com um caractere alfabético ou sublinhado (`_`).</span><span class="sxs-lookup"><span data-stu-id="baaa3-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="baaa3-111">Ele deve conter apenas caracteres alfabéticos, dígitos decimais, sublinhados, pontos (.) e hifens (-).</span><span class="sxs-lookup"><span data-stu-id="baaa3-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
-   <span data-ttu-id="baaa3-112">Ele não deve ter mais de 1.024 caracteres.</span><span class="sxs-lookup"><span data-stu-id="baaa3-112">It must not be more than 1,024 characters long.</span></span>  
  
-   <span data-ttu-id="baaa3-113">Dois-pontos que aparecem em nomes indicam demarcação de namespace.</span><span class="sxs-lookup"><span data-stu-id="baaa3-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="baaa3-114">Portanto, você pode usar dois-pontos somente para especificar um namespace de XML para um determinado nome.</span><span class="sxs-lookup"><span data-stu-id="baaa3-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="baaa3-115">Além disso, você deve seguir as diretrizes a seguir.</span><span class="sxs-lookup"><span data-stu-id="baaa3-115">In addition, you should adhere to the following guideline.</span></span>  
  
-   <span data-ttu-id="baaa3-116">A especificação XML 1.0 se reserva todos os nomes que começam com a cadeia de caracteres "xml", de qualquer variação de maiusculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="baaa3-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="baaa3-117">Portanto, não use esses nomes para o elemento e nomes de atributo.</span><span class="sxs-lookup"><span data-stu-id="baaa3-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="baaa3-118">Diretrizes de comprimento de nome</span><span class="sxs-lookup"><span data-stu-id="baaa3-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="baaa3-119">Como uma questão de prática, um nome deve ser tão curto quanto possível e ainda identificar claramente a natureza do elemento.</span><span class="sxs-lookup"><span data-stu-id="baaa3-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="baaa3-120">Isso melhora a legibilidade do código e reduz o tamanho da linha de comprimento e o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="baaa3-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="baaa3-121">No entanto, seu nome não deve ser tão curto para que ele não descreve adequadamente o elemento ou como seu código usa.</span><span class="sxs-lookup"><span data-stu-id="baaa3-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="baaa3-122">Isso é importante para fins de legibilidade do código.</span><span class="sxs-lookup"><span data-stu-id="baaa3-122">This is important for the readability of your code.</span></span> <span data-ttu-id="baaa3-123">Se alguém está tentando compreendê-lo, ou se você mesmo o está examinando um longo tempo depois que você o escreveu, nomes de elemento apropriado podem economizar tempo.</span><span class="sxs-lookup"><span data-stu-id="baaa3-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="baaa3-124">Maiusculas e minúsculas em nomes</span><span class="sxs-lookup"><span data-stu-id="baaa3-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="baaa3-125">Nomes de elemento XML diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="baaa3-125">XML element names are case sensitive.</span></span> <span data-ttu-id="baaa3-126">Isso significa que quando o compilador do Visual Basic compara dois nomes que diferem somente caso alfabética, ele interpreta como nomes diferentes.</span><span class="sxs-lookup"><span data-stu-id="baaa3-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="baaa3-127">Por exemplo, ele interpreta `ABC` e `abc` como uma referência para separar elementos.</span><span class="sxs-lookup"><span data-stu-id="baaa3-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="baaa3-128">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="baaa3-128">XML Namespaces</span></span>  
 <span data-ttu-id="baaa3-129">Ao criar um elemento XML literal, você pode especificar o prefixo de namespace XML para o nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="baaa3-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="baaa3-130">Para obter mais informações, consulte [Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="baaa3-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baaa3-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baaa3-131">See also</span></span>

- [<span data-ttu-id="baaa3-132">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="baaa3-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="baaa3-133">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="baaa3-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
