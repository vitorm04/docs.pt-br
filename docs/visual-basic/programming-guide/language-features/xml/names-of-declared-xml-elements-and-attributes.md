---
title: Nomes de elementos e atributos XML declarados (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 846a028e076873d1978f751fdb70e93c7c6a81af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="8eed9-102">Nomes de elementos e atributos XML declarados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8eed9-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="8eed9-103">Este tópico fornece [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] diretrizes para nomes de elementos XML e atributos em literais XML.</span><span class="sxs-lookup"><span data-stu-id="8eed9-103">This topic provides [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="8eed9-104">Em um literal XML, você pode especificar um nome local ou um nome qualificado.</span><span class="sxs-lookup"><span data-stu-id="8eed9-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="8eed9-105">Um nome qualificado consiste de um prefixo de namespace XML, dois-pontos e um nome local.</span><span class="sxs-lookup"><span data-stu-id="8eed9-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="8eed9-106">Para obter mais informações sobre prefixos de namespace XML, consulte [o Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="8eed9-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="8eed9-107">Regras</span><span class="sxs-lookup"><span data-stu-id="8eed9-107">Rules</span></span>  
 <span data-ttu-id="8eed9-108">Um nome de local de um elemento ou atributo em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] devem seguir as regras a seguir.</span><span class="sxs-lookup"><span data-stu-id="8eed9-108">A local name of an element or attribute in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must adhere to the following rules.</span></span>  
  
-   <span data-ttu-id="8eed9-109">Ele pode começar com um namespace.</span><span class="sxs-lookup"><span data-stu-id="8eed9-109">It can begin with a namespace.</span></span> <span data-ttu-id="8eed9-110">Ele deve começar com um caractere alfabético ou sublinhado (`_`).</span><span class="sxs-lookup"><span data-stu-id="8eed9-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="8eed9-111">Ela deve conter apenas caracteres alfabéticos, dígitos decimais, sublinhados, pontos (.) e hifens (-).</span><span class="sxs-lookup"><span data-stu-id="8eed9-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
-   <span data-ttu-id="8eed9-112">Ele não deve ter mais de 1.024 caracteres.</span><span class="sxs-lookup"><span data-stu-id="8eed9-112">It must not be more than 1,024 characters long.</span></span>  
  
-   <span data-ttu-id="8eed9-113">Dois-pontos aparecem em nomes indicam demarcação de namespace.</span><span class="sxs-lookup"><span data-stu-id="8eed9-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="8eed9-114">Portanto, você pode usar dois-pontos somente para especificar um namespace XML para um determinado nome.</span><span class="sxs-lookup"><span data-stu-id="8eed9-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="8eed9-115">Além disso, você deve seguir as diretrizes a seguir.</span><span class="sxs-lookup"><span data-stu-id="8eed9-115">In addition, you should adhere to the following guideline.</span></span>  
  
-   <span data-ttu-id="8eed9-116">A especificação XML 1.0 se reserva todos os nomes que começam com a cadeia de caracteres "xml", de qualquer variação de maiusculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8eed9-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="8eed9-117">Portanto, não use esses nomes para o elemento e nomes de atributo.</span><span class="sxs-lookup"><span data-stu-id="8eed9-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="8eed9-118">Diretrizes para comprimento de nome</span><span class="sxs-lookup"><span data-stu-id="8eed9-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="8eed9-119">De forma prática, um nome deve ser tão curto quanto possível e ainda identificar claramente a natureza do elemento.</span><span class="sxs-lookup"><span data-stu-id="8eed9-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="8eed9-120">Isso melhora a legibilidade do código e reduz o tamanho de arquivo de origem e de comprimento de linha.</span><span class="sxs-lookup"><span data-stu-id="8eed9-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="8eed9-121">No entanto, o nome não deve ser tão curto que ele não descreve adequadamente o elemento ou como seu código usa.</span><span class="sxs-lookup"><span data-stu-id="8eed9-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="8eed9-122">Isso é importante para a legibilidade do código.</span><span class="sxs-lookup"><span data-stu-id="8eed9-122">This is important for the readability of your code.</span></span> <span data-ttu-id="8eed9-123">Se alguém está tentando compreendê-la, ou se você mesmo o está examinando muito tempo depois que você o escreveu, nomes de elemento apropriado podem economizar tempo.</span><span class="sxs-lookup"><span data-stu-id="8eed9-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="8eed9-124">Diferenciação de maiusculas e minúsculas em nomes</span><span class="sxs-lookup"><span data-stu-id="8eed9-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="8eed9-125">Nomes de elemento XML diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8eed9-125">XML element names are case sensitive.</span></span> <span data-ttu-id="8eed9-126">Isso significa que, quando o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador compara dois nomes que diferem apenas caso alfabética, ele interpreta como diferentes nomes.</span><span class="sxs-lookup"><span data-stu-id="8eed9-126">This means that when the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="8eed9-127">Por exemplo, ele interpreta `ABC` e `abc` como referência para separar elementos.</span><span class="sxs-lookup"><span data-stu-id="8eed9-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="8eed9-128">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="8eed9-128">XML Namespaces</span></span>  
 <span data-ttu-id="8eed9-129">Ao criar um elemento XML literal, você pode especificar o prefixo de namespace XML para o nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="8eed9-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="8eed9-130">Para obter mais informações, consulte [o Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="8eed9-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eed9-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8eed9-131">See Also</span></span>  
 [<span data-ttu-id="8eed9-132">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8eed9-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="8eed9-133">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="8eed9-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
