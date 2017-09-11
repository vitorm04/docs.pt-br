---
title: Declarado como nomes de elemento (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declared elements, case sensitivity
- names, Visual Basic rules
- naming conventions
- element names
- declared elements, identifiers
- declarations, elements
- declared elements, valid names
- '[] escape characters [Visual Basic]'
- names, elements
- declaration statements, declared elements
- declaring elements
- identifiers, declared elements
- case sensitivity, declared element names
- escape characters
- names, declared elements
- declared elements, about declared elements
- escaped names
- declared elements, names
- names, naming conventions
- identifiers, elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: 27
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
ms.openlocfilehash: 899bcb2ecc8f5c07fdf4592e15827ff67f55c136
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="78fef-102">Nomes de elemento declarados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78fef-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="78fef-103">Cada elemento declarado tem um nome, também chamado de um *identificador*, que é o código que se usa para se referir a ele.</span><span class="sxs-lookup"><span data-stu-id="78fef-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="78fef-104">Regras</span><span class="sxs-lookup"><span data-stu-id="78fef-104">Rules</span></span>  
 <span data-ttu-id="78fef-105">Um nome de elemento em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve observar as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="78fef-105">An element name in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must observe the following rules:</span></span>  
  
-   <span data-ttu-id="78fef-106">Ele deve começar com um caractere alfabético ou sublinhado (`_`).</span><span class="sxs-lookup"><span data-stu-id="78fef-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="78fef-107">Ele deve conter apenas caracteres alfabéticos, dígitos decimais e sublinhados.</span><span class="sxs-lookup"><span data-stu-id="78fef-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
-   <span data-ttu-id="78fef-108">Ele deve conter pelo menos um caractere alfabético ou dígito decimal se ele começa com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="78fef-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
-   <span data-ttu-id="78fef-109">Ele não deve ter mais de 1023 caracteres.</span><span class="sxs-lookup"><span data-stu-id="78fef-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="78fef-110">O limite de 1023 caracteres também se aplica a cadeia de caracteres inteira de um nome totalmente qualificado, como `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="78fef-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="78fef-111">O exemplo a seguir mostra alguns nomes de elemento válido.</span><span class="sxs-lookup"><span data-stu-id="78fef-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="78fef-112">O exemplo a seguir mostra alguns nomes de elemento inválido.</span><span class="sxs-lookup"><span data-stu-id="78fef-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="78fef-113">O primeiro contém somente um sublinhado, o segundo começa com um dígito decimal e o terceiro contém um caractere inválido ($).</span><span class="sxs-lookup"><span data-stu-id="78fef-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  <span data-ttu-id="78fef-114">Nomes de elementos iniciados com um sublinhado (`_`) não fazem parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), então um código compatível com CLS não pode usar um componente que define tais nomes.</span><span class="sxs-lookup"><span data-stu-id="78fef-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="78fef-115">No entanto, um sublinhado em qualquer outra posição de um nome de elemento é compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="78fef-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="78fef-116">Diretrizes para comprimento de nome</span><span class="sxs-lookup"><span data-stu-id="78fef-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="78fef-117">Como uma questão prática, o nome deve ser tão curta quanto possível e ainda identificar claramente a natureza do elemento.</span><span class="sxs-lookup"><span data-stu-id="78fef-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="78fef-118">Isso melhora a legibilidade do código e reduz o tamanho de arquivo de origem e de comprimento de linha.</span><span class="sxs-lookup"><span data-stu-id="78fef-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="78fef-119">Por outro lado, o nome não deve ser tão curto que ele não descreve adequadamente o elemento que representa e como seu código usa.</span><span class="sxs-lookup"><span data-stu-id="78fef-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="78fef-120">Isso é importante para a legibilidade do código.</span><span class="sxs-lookup"><span data-stu-id="78fef-120">This is important for the readability of your code.</span></span> <span data-ttu-id="78fef-121">Se alguém está tentando compreendê-la, ou se você mesmo o está examinando muito tempo depois que você o escreveu, nomes de elementos adequados podem salvar uma quantidade considerável de tempo.</span><span class="sxs-lookup"><span data-stu-id="78fef-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="78fef-122">Nomes de escape</span><span class="sxs-lookup"><span data-stu-id="78fef-122">Escaped Names</span></span>  
 <span data-ttu-id="78fef-123">Geralmente, um nome de elemento não deve conter qualquer uma das palavras-chave reservadas pelo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], como `Case` ou `Friend`.</span><span class="sxs-lookup"><span data-stu-id="78fef-123">Generally, an element name must not match any of the keywords reserved by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], such as `Case` or `Friend`.</span></span> <span data-ttu-id="78fef-124">No entanto, você pode definir um *nome escapado*, que é colocado entre colchetes (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="78fef-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="78fef-125">Um nome escapado pode conter qualquer [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] palavra-chave, pois os colchetes removem qualquer ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="78fef-125">An escaped name can match any [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="78fef-126">Você também usa os colchetes quando você se referir ao nome posteriormente no seu código.</span><span class="sxs-lookup"><span data-stu-id="78fef-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="78fef-127">Em geral, você deve usar nomes escapados apenas quando:</span><span class="sxs-lookup"><span data-stu-id="78fef-127">In general, you should use escaped names only when:</span></span>  
  
-   <span data-ttu-id="78fef-128">Seu código migrou de uma versão anterior do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] que não reservar a palavra-chave que está sendo usada como um nome; ou</span><span class="sxs-lookup"><span data-stu-id="78fef-128">Your code has migrated from a previous version of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] that did not reserve the keyword being used as a name; or</span></span>  
  
-   <span data-ttu-id="78fef-129">Você está trabalhando com código escrito em outra linguagem na qual a palavra-chave fornecida não está reservada.</span><span class="sxs-lookup"><span data-stu-id="78fef-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="78fef-130">Caso contrário, considere renomear o elemento se seu nome está em conflito com uma palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="78fef-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="78fef-131">O ambiente de desenvolvimento integrado (IDE) fornece uma maneira fácil de fazer isso.</span><span class="sxs-lookup"><span data-stu-id="78fef-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="78fef-132">Para obter mais informações, consulte [refatoração](https://docs.microsoft.com/visualstudio/vb-ide/refactoring-vb).</span><span class="sxs-lookup"><span data-stu-id="78fef-132">For more information, see [Refactoring](https://docs.microsoft.com/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="78fef-133">Diferenciação de maiusculas e minúsculas em nomes</span><span class="sxs-lookup"><span data-stu-id="78fef-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="78fef-134">Nomes de elementos em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="78fef-134">Element names in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] are case-insensitive.</span></span> <span data-ttu-id="78fef-135">Isso significa que quando o compilador compara dois nomes que diferem somente no caso alfabético, ele interpreta como o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="78fef-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="78fef-136">Por exemplo, ele considera `ABC` e `abc` para referir-se ao mesmo elemento declarado.</span><span class="sxs-lookup"><span data-stu-id="78fef-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="78fef-137">No entanto, o common language runtime (CLR) usa associação diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="78fef-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="78fef-138">Portanto, quando você gerar um assembly ou uma DLL e disponibilizá-lo para outros assemblies, seus nomes não diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="78fef-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="78fef-139">Por exemplo, se você definir uma classe com um elemento chamado `ABC`, e outros assemblies fazer uso de sua classe por meio do common language runtime, eles devem se referir ao elemento como `ABC`.</span><span class="sxs-lookup"><span data-stu-id="78fef-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="78fef-140">Se você posteriormente recompilar sua classe e alterar o nome do elemento para `abc`, os outros assemblies usando sua classe não podem acessar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="78fef-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="78fef-141">Portanto, quando você lançar uma versão atualizada de um assembly, você não deve alterar maiusculas e minúsculas em quaisquer elementos públicos.</span><span class="sxs-lookup"><span data-stu-id="78fef-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="78fef-142">Nomes e locais</span><span class="sxs-lookup"><span data-stu-id="78fef-142">Names and Locales</span></span>  
 <span data-ttu-id="78fef-143">Comparação de nomes é independente da localidade.</span><span class="sxs-lookup"><span data-stu-id="78fef-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="78fef-144">Se dois nomes correspondem em uma localidade, eles são garantidos para corresponder em todas as localidades.</span><span class="sxs-lookup"><span data-stu-id="78fef-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78fef-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78fef-145">See Also</span></span>  
 <span data-ttu-id="78fef-146">[Elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md) </span><span class="sxs-lookup"><span data-stu-id="78fef-146">[Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md) </span></span>  
<span data-ttu-id="78fef-147"> [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="78fef-147"> [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span></span>  
<span data-ttu-id="78fef-148"> [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="78fef-148"> [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="78fef-149"> [Instruções](../../../../visual-basic/language-reference/statements/index.md)</span><span class="sxs-lookup"><span data-stu-id="78fef-149"> [Statements](../../../../visual-basic/language-reference/statements/index.md)</span></span>
