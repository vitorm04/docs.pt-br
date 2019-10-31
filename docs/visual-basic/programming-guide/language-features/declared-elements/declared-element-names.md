---
title: Nomes de elemento declarados (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 0ace2b13473db30a4500648a67f6ce34edf3e587
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197551"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="d39d8-102">Nomes de elemento declarados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d39d8-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="d39d8-103">Cada elemento declarado tem um nome, também chamado de *identificador*, que é o que o código usa para se referir a ele.</span><span class="sxs-lookup"><span data-stu-id="d39d8-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d39d8-104">Regras</span><span class="sxs-lookup"><span data-stu-id="d39d8-104">Rules</span></span>  
 <span data-ttu-id="d39d8-105">Um nome de elemento em Visual Basic deve observar as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="d39d8-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
- <span data-ttu-id="d39d8-106">Ele deve começar com um caractere alfabético ou um sublinhado (`_`).</span><span class="sxs-lookup"><span data-stu-id="d39d8-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="d39d8-107">Ele deve conter apenas caracteres alfabéticos, dígitos decimais e sublinhados.</span><span class="sxs-lookup"><span data-stu-id="d39d8-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
- <span data-ttu-id="d39d8-108">Ele deve conter pelo menos um caractere alfabético ou dígito decimal se começar com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="d39d8-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
- <span data-ttu-id="d39d8-109">Ele não deve ter mais de 1023 caracteres.</span><span class="sxs-lookup"><span data-stu-id="d39d8-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="d39d8-110">O limite de comprimento de 1023 caracteres também se aplica à cadeia de caracteres inteira de um nome totalmente qualificado, como `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="d39d8-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="d39d8-111">O exemplo a seguir mostra alguns nomes de elemento válidos.</span><span class="sxs-lookup"><span data-stu-id="d39d8-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="d39d8-112">O exemplo a seguir mostra alguns nomes de elemento inválidos.</span><span class="sxs-lookup"><span data-stu-id="d39d8-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="d39d8-113">O primeiro contém apenas um sublinhado, o segundo começa com um dígito decimal e o terceiro contém um caractere inválido ($).</span><span class="sxs-lookup"><span data-stu-id="d39d8-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> <span data-ttu-id="d39d8-114">Nomes de elementos que começam com um sublinhado (`_`) não fazem parte da [independência de linguagem e dos componentes independentes de linguagem](../../../../standard/language-independence-and-language-independent-components.md) (CLS), portanto, o código em conformidade com CLS não pode usar um componente que define tais nomes.</span><span class="sxs-lookup"><span data-stu-id="d39d8-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="d39d8-115">No entanto, um sublinhado em qualquer outra posição em um nome de elemento é compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="d39d8-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="d39d8-116">Diretrizes de comprimento do nome</span><span class="sxs-lookup"><span data-stu-id="d39d8-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="d39d8-117">Como uma questão prática, seu nome deve ser o mais curto possível e, ao mesmo tempo, identificar claramente a natureza do elemento.</span><span class="sxs-lookup"><span data-stu-id="d39d8-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="d39d8-118">Isso melhora a legibilidade do seu código e reduz a duração da linha e o tamanho do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="d39d8-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="d39d8-119">Por outro lado, seu nome não deve ser tão curto que não Descreva adequadamente o que o elemento representa e como seu código o utiliza.</span><span class="sxs-lookup"><span data-stu-id="d39d8-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="d39d8-120">Isso é importante para a legibilidade do seu código.</span><span class="sxs-lookup"><span data-stu-id="d39d8-120">This is important for the readability of your code.</span></span> <span data-ttu-id="d39d8-121">Se alguém estiver tentando entender isso, ou se você mesmo estiver olhando para ele um longo tempo depois de ter escrito, nomes de elemento adequados podem economizar um tempo considerável.</span><span class="sxs-lookup"><span data-stu-id="d39d8-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="d39d8-122">Nomes com escape</span><span class="sxs-lookup"><span data-stu-id="d39d8-122">Escaped Names</span></span>  
 <span data-ttu-id="d39d8-123">Em geral, um nome de elemento não deve corresponder a nenhuma das palavras-chave reservadas por Visual Basic, como `Case` ou `Friend`.</span><span class="sxs-lookup"><span data-stu-id="d39d8-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="d39d8-124">No entanto, você pode definir um *nome de escape*, que é colocado entre colchetes (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="d39d8-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="d39d8-125">Um nome de escape pode corresponder a qualquer palavra-chave Visual Basic, já que os colchetes removem qualquer ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="d39d8-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="d39d8-126">Você também usará os colchetes quando se referir ao nome posteriormente em seu código.</span><span class="sxs-lookup"><span data-stu-id="d39d8-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="d39d8-127">Em geral, você deve usar nomes com escape somente quando:</span><span class="sxs-lookup"><span data-stu-id="d39d8-127">In general, you should use escaped names only when:</span></span>  
  
- <span data-ttu-id="d39d8-128">Seu código foi migrado de uma versão anterior do Visual Basic que não reservava a palavra-chave que está sendo usada como um nome; or</span><span class="sxs-lookup"><span data-stu-id="d39d8-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
- <span data-ttu-id="d39d8-129">Você está trabalhando com código escrito em outro idioma no qual a palavra-chave fornecida não está reservada.</span><span class="sxs-lookup"><span data-stu-id="d39d8-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="d39d8-130">Caso contrário, você deve considerar renomear o elemento se seu nome entrar em conflito com uma palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="d39d8-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="d39d8-131">O IDE (ambiente de desenvolvimento integrado) fornece uma maneira fácil de fazer isso.</span><span class="sxs-lookup"><span data-stu-id="d39d8-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="d39d8-132">Para obter mais informações, consulte [refatoração](/visualstudio/ide/refactoring-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="d39d8-132">For more information, see [Refactoring](/visualstudio/ide/refactoring-in-visual-studio).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="d39d8-133">Distinção de maiúsculas e minúsculas em nomes</span><span class="sxs-lookup"><span data-stu-id="d39d8-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="d39d8-134">Os nomes de elementos em Visual Basic não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="d39d8-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="d39d8-135">Isso significa que, quando o compilador compara dois nomes que diferem somente em maiúsculas e minúsculas, ele os interpreta como o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="d39d8-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="d39d8-136">Por exemplo, ele considera `ABC` e `abc` para fazer referência ao mesmo elemento declarado.</span><span class="sxs-lookup"><span data-stu-id="d39d8-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="d39d8-137">No entanto, o Common Language Runtime (CLR) usa a associação que diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="d39d8-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="d39d8-138">Portanto, quando você produz um assembly ou uma DLL e o disponibiliza para outros assemblies, seus nomes não são mais sensíveis a maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="d39d8-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="d39d8-139">Por exemplo, se você definir uma classe com um elemento chamado `ABC`e outros assemblies fizerem uso de sua classe por meio da Common Language Runtime, eles deverão se referir ao elemento como `ABC`.</span><span class="sxs-lookup"><span data-stu-id="d39d8-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="d39d8-140">Se, posteriormente, você recompilar sua classe e alterar o nome do elemento para `abc`, os outros assemblies que usam sua classe não poderão mais acessar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="d39d8-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="d39d8-141">Portanto, quando você libera uma versão atualizada de um assembly, não deve alterar o caso alfabético de quaisquer elementos públicos.</span><span class="sxs-lookup"><span data-stu-id="d39d8-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="d39d8-142">Nomes e localidades</span><span class="sxs-lookup"><span data-stu-id="d39d8-142">Names and Locales</span></span>  
 <span data-ttu-id="d39d8-143">A comparação de nomes é independente da localidade.</span><span class="sxs-lookup"><span data-stu-id="d39d8-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="d39d8-144">Se dois nomes corresponderem em uma localidade, eles terão a garantia de corresponder em todas as localidades.</span><span class="sxs-lookup"><span data-stu-id="d39d8-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d39d8-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d39d8-145">See also</span></span>

- [<span data-ttu-id="d39d8-146">Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="d39d8-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [<span data-ttu-id="d39d8-147">Características do Elemento Declarado</span><span class="sxs-lookup"><span data-stu-id="d39d8-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="d39d8-148">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="d39d8-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="d39d8-149">Instruções</span><span class="sxs-lookup"><span data-stu-id="d39d8-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
