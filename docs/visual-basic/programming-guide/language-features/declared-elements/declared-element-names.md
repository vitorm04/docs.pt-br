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
ms.openlocfilehash: 5b1f8ccc402f7f5928a33f434664b0f28d108e6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61828608"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="dcc9c-102">Nomes de elemento declarados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcc9c-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="dcc9c-103">Cada elemento declarado tem um nome, também chamado de um *identificador*, que é o código que se usa para se referir a ele.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="dcc9c-104">Regras</span><span class="sxs-lookup"><span data-stu-id="dcc9c-104">Rules</span></span>  
 <span data-ttu-id="dcc9c-105">Um nome de elemento no Visual Basic deve observar as regras a seguir:</span><span class="sxs-lookup"><span data-stu-id="dcc9c-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
- <span data-ttu-id="dcc9c-106">Ele deve começar com um caractere alfabético ou sublinhado (`_`).</span><span class="sxs-lookup"><span data-stu-id="dcc9c-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="dcc9c-107">Ele deve conter apenas caracteres alfabéticos, dígitos decimais e sublinhados.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
- <span data-ttu-id="dcc9c-108">Ele deve conter pelo menos um caractere alfabético ou dígito decimal se ele começa com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
- <span data-ttu-id="dcc9c-109">Ele não deve ter mais de 1023 caracteres.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="dcc9c-110">O limite de tamanho de 1023 caracteres também se aplica a toda a cadeia de caracteres de um nome totalmente qualificado, como `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="dcc9c-111">O exemplo a seguir mostra alguns nomes de elemento válido.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="dcc9c-112">O exemplo a seguir mostra alguns nomes de elemento inválido.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="dcc9c-113">O primeiro contém somente um caractere de sublinhado, a segunda começa com um dígito decimal e o terceiro contém um caractere inválido ($).</span><span class="sxs-lookup"><span data-stu-id="dcc9c-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  <span data-ttu-id="dcc9c-114">Nomes de elementos, começando com um caractere de sublinhado (`_`) não fazem parte dos [independência de linguagem e componentes independentes de linguagem](../../../../standard/language-independence-and-language-independent-components.md) (CLS), então um código compatível com CLS não é possível usar um componente que define tais nomes.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="dcc9c-115">No entanto, um sublinhado em qualquer outra posição de um nome de elemento é compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="dcc9c-116">Diretrizes de comprimento de nome</span><span class="sxs-lookup"><span data-stu-id="dcc9c-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="dcc9c-117">Como uma questão de prática, o nome deve ser tão curto quanto possível e ainda identificar claramente a natureza do elemento.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="dcc9c-118">Isso melhora a legibilidade do código e reduz o tamanho da linha de comprimento e o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="dcc9c-119">Por outro lado, o nome não deve ser tão curto para que ele não descreve adequadamente o elemento que representa e como seu código usa.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="dcc9c-120">Isso é importante para fins de legibilidade do código.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-120">This is important for the readability of your code.</span></span> <span data-ttu-id="dcc9c-121">Se alguém está tentando compreendê-lo, ou se você mesmo o está examinando um longo tempo depois que você o escreveu, nomes de elemento adequado podem salvar uma quantidade considerável de tempo.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="dcc9c-122">Nomes de escape</span><span class="sxs-lookup"><span data-stu-id="dcc9c-122">Escaped Names</span></span>  
 <span data-ttu-id="dcc9c-123">Geralmente, um nome de elemento não deve conter qualquer uma das palavras-chave reservadas pelo Visual Basic, como `Case` ou `Friend`.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="dcc9c-124">No entanto, você pode definir um *nome escapado*, que é colocado entre colchetes (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="dcc9c-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="dcc9c-125">Um nome escapado pode conter qualquer palavra-chave do Visual Basic, desde que os colchetes removem qualquer ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="dcc9c-126">Também é possível usar colchetes quando você se referir ao nome posteriormente no seu código.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="dcc9c-127">Em geral, você deve usar nomes escapados apenas quando:</span><span class="sxs-lookup"><span data-stu-id="dcc9c-127">In general, you should use escaped names only when:</span></span>  
  
- <span data-ttu-id="dcc9c-128">Seu código migrou de uma versão anterior do Visual Basic não reservar a palavra-chave que está sendo usada como um nome; ou</span><span class="sxs-lookup"><span data-stu-id="dcc9c-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
- <span data-ttu-id="dcc9c-129">Você está trabalhando com código escrito em outra linguagem na qual a palavra-chave fornecida não está reservada.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="dcc9c-130">Caso contrário, você deve considerar renomeando o elemento se seu nome está em conflito com uma palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="dcc9c-131">O ambiente de desenvolvimento integrado (IDE) fornece uma maneira fácil de fazer isso.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="dcc9c-132">Para obter mais informações, consulte [refatoração](/visualstudio/vb-ide/refactoring-vb).</span><span class="sxs-lookup"><span data-stu-id="dcc9c-132">For more information, see [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="dcc9c-133">Maiusculas e minúsculas em nomes</span><span class="sxs-lookup"><span data-stu-id="dcc9c-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="dcc9c-134">Nomes de elementos no Visual Basic diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="dcc9c-135">Isso significa que quando o compilador compara dois nomes que diferem somente no caso alfabético, ele interpreta como o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="dcc9c-136">Por exemplo, ele considera `ABC` e `abc` para se referir ao mesmo elemento declarado.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="dcc9c-137">No entanto, o common language runtime (CLR) usa a associação diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="dcc9c-138">Portanto, quando você produzir um assembly ou uma DLL e disponibilizá-lo para outros assemblies, seus nomes não diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="dcc9c-139">Por exemplo, se você definir uma classe com um elemento chamado `ABC`, e outros assemblies fazer uso de sua classe por meio do common language runtime, eles devem se referir ao elemento como `ABC`.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="dcc9c-140">Se você posteriormente recompilar sua classe e alterar o nome do elemento para `abc`, os outros assemblies usando a classe não foi possível acessar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="dcc9c-141">Portanto, quando você liberar uma versão atualizada de um assembly, você não deve alterar maiusculas e minúsculas em qualquer elemento público.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="dcc9c-142">Nomes e locais</span><span class="sxs-lookup"><span data-stu-id="dcc9c-142">Names and Locales</span></span>  
 <span data-ttu-id="dcc9c-143">Comparação de nomes é independente da localidade.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="dcc9c-144">Se dois nomes correspondem em uma localidade, eles são garantidos para corresponder em todas as localidades.</span><span class="sxs-lookup"><span data-stu-id="dcc9c-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc9c-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcc9c-145">See also</span></span>

- [<span data-ttu-id="dcc9c-146">Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="dcc9c-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [<span data-ttu-id="dcc9c-147">Características do Elemento Declarado</span><span class="sxs-lookup"><span data-stu-id="dcc9c-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="dcc9c-148">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="dcc9c-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="dcc9c-149">Instruções</span><span class="sxs-lookup"><span data-stu-id="dcc9c-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
