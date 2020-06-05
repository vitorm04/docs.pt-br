---
title: Nomes de elementos e atributos XML declarados
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 043243eeee7c24d8c63105047fa3e7e0ed58c7b0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374662"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="3a7f0-102">Nomes de elementos e atributos XML declarados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a7f0-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="3a7f0-103">Este tópico fornece diretrizes de Visual Basic para nomear elementos XML e atributos em literais XML.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="3a7f0-104">Em um literal XML, você pode especificar um nome local ou um nome qualificado.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="3a7f0-105">Um nome qualificado consiste em um prefixo de namespace XML, dois-pontos e um nome local.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="3a7f0-106">Para obter mais informações sobre prefixos de namespace XML, consulte [XML Element literal](../../../language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="3a7f0-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3a7f0-107">Regras</span><span class="sxs-lookup"><span data-stu-id="3a7f0-107">Rules</span></span>  
 <span data-ttu-id="3a7f0-108">Um nome local de um elemento ou atributo em Visual Basic deve aderir às regras a seguir.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
- <span data-ttu-id="3a7f0-109">Ele pode começar com um namespace.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-109">It can begin with a namespace.</span></span> <span data-ttu-id="3a7f0-110">Ele deve começar com um caractere alfabético ou um sublinhado ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="3a7f0-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="3a7f0-111">Ele deve conter apenas caracteres alfabéticos, dígitos decimais, sublinhados, pontos (.) e hifens (-).</span><span class="sxs-lookup"><span data-stu-id="3a7f0-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
- <span data-ttu-id="3a7f0-112">Ele não deve ter mais de 1.024 caracteres.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-112">It must not be more than 1,024 characters long.</span></span>  
  
- <span data-ttu-id="3a7f0-113">Dois pontos que aparecem em nomes indicam a demarcação do namespace.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="3a7f0-114">Portanto, você pode usar somente dois-pontos para especificar um namespace XML para um nome específico.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="3a7f0-115">Além disso, você deve aderir à seguinte diretriz.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-115">In addition, you should adhere to the following guideline.</span></span>  
  
- <span data-ttu-id="3a7f0-116">A especificação XML 1,0 reserva todos os nomes que começam com a cadeia de caracteres "XML", de qualquer variação de capitalização.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="3a7f0-117">Portanto, não use esses nomes para seus nomes de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="3a7f0-118">Diretrizes de comprimento do nome</span><span class="sxs-lookup"><span data-stu-id="3a7f0-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="3a7f0-119">Como uma questão prática, um nome deve ser o mais curto possível e, ao mesmo tempo, identificar claramente a natureza do elemento.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="3a7f0-120">Isso melhora a legibilidade do seu código e reduz a duração da linha e o tamanho do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="3a7f0-121">No entanto, seu nome não deve ser tão curto que não Descreva adequadamente o elemento ou como seu código o utiliza.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="3a7f0-122">Isso é importante para a legibilidade do seu código.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-122">This is important for the readability of your code.</span></span> <span data-ttu-id="3a7f0-123">Se outra pessoa estiver tentando entender isso, ou se você mesmo estiver olhando para ele um longo tempo depois de ter escrito, os nomes de elemento apropriados poderão economizar tempo.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="3a7f0-124">Distinção de maiúsculas e minúsculas em nomes</span><span class="sxs-lookup"><span data-stu-id="3a7f0-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="3a7f0-125">Os nomes de elementos XML diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-125">XML element names are case sensitive.</span></span> <span data-ttu-id="3a7f0-126">Isso significa que, quando o compilador de Visual Basic compara dois nomes que diferem apenas em maiúsculas e minúsculas, ele os interpreta como nomes diferentes.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="3a7f0-127">Por exemplo, ele interpreta `ABC` e `abc` como se referir a elementos separados.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="3a7f0-128">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="3a7f0-128">XML Namespaces</span></span>  
 <span data-ttu-id="3a7f0-129">Ao criar um literal de elemento XML, você pode especificar o prefixo do namespace XML para o nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="3a7f0-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="3a7f0-130">Para obter mais informações, consulte [literal de elemento XML](../../../language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="3a7f0-130">For more information, see [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a7f0-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a7f0-131">See also</span></span>

- [<span data-ttu-id="3a7f0-132">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a7f0-132">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="3a7f0-133">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="3a7f0-133">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
