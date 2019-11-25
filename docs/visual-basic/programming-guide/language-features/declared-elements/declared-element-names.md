---
title: Nomes de elemento declarados
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
ms.openlocfilehash: e8620517b934a5f1a97ea25c5a94c8b932bb47b2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345425"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="e5b4d-102">Nomes de elemento declarados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5b4d-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="e5b4d-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e5b4d-104">Regras</span><span class="sxs-lookup"><span data-stu-id="e5b4d-104">Rules</span></span>  
 <span data-ttu-id="e5b4d-105">An element name in Visual Basic must observe the following rules:</span><span class="sxs-lookup"><span data-stu-id="e5b4d-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
- <span data-ttu-id="e5b4d-106">It must begin with an alphabetic character or an underscore (`_`).</span><span class="sxs-lookup"><span data-stu-id="e5b4d-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="e5b4d-107">It must only contain alphabetic characters, decimal digits, and underscores.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
- <span data-ttu-id="e5b4d-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
- <span data-ttu-id="e5b4d-109">It must not be more than 1023 characters long.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="e5b4d-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="e5b4d-111">The following example shows some valid element names.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="e5b4d-112">The following example shows some invalid element names.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="e5b4d-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span><span class="sxs-lookup"><span data-stu-id="e5b4d-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> <span data-ttu-id="e5b4d-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="e5b4d-115">However, an underscore in any other position in an element name is CLS-compliant.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="e5b4d-116">Name Length Guidelines</span><span class="sxs-lookup"><span data-stu-id="e5b4d-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="e5b4d-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="e5b4d-118">This improves the readability of your code and reduces line length and source-file size.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="e5b4d-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="e5b4d-120">This is important for the readability of your code.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-120">This is important for the readability of your code.</span></span> <span data-ttu-id="e5b4d-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="e5b4d-122">Escaped Names</span><span class="sxs-lookup"><span data-stu-id="e5b4d-122">Escaped Names</span></span>  
 <span data-ttu-id="e5b4d-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="e5b4d-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="e5b4d-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="e5b4d-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="e5b4d-126">You also use the brackets when you refer to the name later in your code.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="e5b4d-127">In general, you should use escaped names only when:</span><span class="sxs-lookup"><span data-stu-id="e5b4d-127">In general, you should use escaped names only when:</span></span>  
  
- <span data-ttu-id="e5b4d-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span><span class="sxs-lookup"><span data-stu-id="e5b4d-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
- <span data-ttu-id="e5b4d-129">You are working with code written in another language in which the given keyword is not reserved.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="e5b4d-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="e5b4d-131">The integrated development environment (IDE) provides an easy way to do this.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="e5b4d-132">For more information, see [Refactoring](/visualstudio/ide/refactoring-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="e5b4d-132">For more information, see [Refactoring](/visualstudio/ide/refactoring-in-visual-studio).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="e5b4d-133">Case Sensitivity in Names</span><span class="sxs-lookup"><span data-stu-id="e5b4d-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="e5b4d-134">Element names in Visual Basic are case-insensitive.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="e5b4d-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="e5b4d-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="e5b4d-137">However, the common language runtime (CLR) uses case-sensitive binding.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="e5b4d-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="e5b4d-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="e5b4d-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="e5b4d-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="e5b4d-142">Names and Locales</span><span class="sxs-lookup"><span data-stu-id="e5b4d-142">Names and Locales</span></span>  
 <span data-ttu-id="e5b4d-143">Comparison of names is independent of locale.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="e5b4d-144">If two names match in one locale, they are guaranteed to match in all locales.</span><span class="sxs-lookup"><span data-stu-id="e5b4d-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b4d-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5b4d-145">See also</span></span>

- [<span data-ttu-id="e5b4d-146">Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="e5b4d-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [<span data-ttu-id="e5b4d-147">Características do Elemento Declarado</span><span class="sxs-lookup"><span data-stu-id="e5b4d-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="e5b4d-148">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="e5b4d-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="e5b4d-149">Instruções</span><span class="sxs-lookup"><span data-stu-id="e5b4d-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
