---
title: "Tipo de promoção (Visual Basic) | Documentos do Microsoft"
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
- declared elements, scope
- visibility, declared elements
- Partial keyword, unexpected results with type promotion
- scope, declared elements
- scope, Visual Basic
- type promotion
- declared elements, visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
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
ms.openlocfilehash: 383f4b1d29e9bbf81eee44bf78762a80aea9eb36
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="8a461-102">Promoção de tipos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a461-102">Type Promotion (Visual Basic)</span></span>
<span data-ttu-id="8a461-103">Quando você declarar um elemento de programação em um módulo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] promove seu escopo para o namespace que contém o módulo.</span><span class="sxs-lookup"><span data-stu-id="8a461-103">When you declare a programming element in a module, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="8a461-104">Isso é conhecido como *promoção de tipo*.</span><span class="sxs-lookup"><span data-stu-id="8a461-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="8a461-105">O exemplo a seguir mostra uma definição de um módulo e dois membros desse módulo.</span><span class="sxs-lookup"><span data-stu-id="8a461-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 <span data-ttu-id="8a461-106">[!code-vb[VbVbalrDeclaredElements n º&1;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8a461-106">[!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]</span></span>  
  
 <span data-ttu-id="8a461-107">Dentro de `projModule`, programação elementos declarados no nível de módulo são promovidos para `projNamespace`.</span><span class="sxs-lookup"><span data-stu-id="8a461-107">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="8a461-108">No exemplo anterior, `basicEnum` e `innerClass` são promovidos, mas `numberSub` não é, pois ele não está declarado no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="8a461-108">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="8a461-109">Efeito da promoção de tipo</span><span class="sxs-lookup"><span data-stu-id="8a461-109">Effect of Type Promotion</span></span>  
 <span data-ttu-id="8a461-110">O efeito da promoção de tipos é que uma cadeia de caracteres de qualificação não precisa incluir o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="8a461-110">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="8a461-111">O exemplo a seguir faz duas chamadas para o procedimento no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="8a461-111">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 <span data-ttu-id="8a461-112">[!code-vb[VbVbalrDeclaredElements n º&2;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="8a461-112">[!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]</span></span>  
  
 <span data-ttu-id="8a461-113">No exemplo anterior, a primeira chamada usa cadeias de caracteres de qualificação completa.</span><span class="sxs-lookup"><span data-stu-id="8a461-113">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="8a461-114">No entanto, isso não é necessário devido a promoção de tipos.</span><span class="sxs-lookup"><span data-stu-id="8a461-114">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="8a461-115">A segunda chamada também acessa os membros do módulo sem incluir `projModule` nas sequências de qualificação.</span><span class="sxs-lookup"><span data-stu-id="8a461-115">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="8a461-116">Derrota da promoção de tipo</span><span class="sxs-lookup"><span data-stu-id="8a461-116">Defeat of Type Promotion</span></span>  
 <span data-ttu-id="8a461-117">Se o namespace já tiver um membro com o mesmo nome como um módulo membro, a promoção de tipos é derrotada por esse módulo associado.</span><span class="sxs-lookup"><span data-stu-id="8a461-117">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="8a461-118">O exemplo a seguir mostra uma definição de uma enumeração e um módulo no mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="8a461-118">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 <span data-ttu-id="8a461-119">[!code-vb[VbVbalrDeclaredElements n º&3;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="8a461-119">[!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]</span></span>  
  
 <span data-ttu-id="8a461-120">No exemplo anterior, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não é possível promover a classe `abc` para `thisNameSpace` porque já existe uma enumeração com o mesmo nome no nível de namespace.</span><span class="sxs-lookup"><span data-stu-id="8a461-120">In the preceding example, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="8a461-121">Para acessar `abcSub`, você deve usar a cadeia de caracteres de qualificação completa `thisNamespace.thisModule.abc.abcSub`.</span><span class="sxs-lookup"><span data-stu-id="8a461-121">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="8a461-122">No entanto, a classe `xyz` ainda é promovida, e você pode acessar `xyzSub` com a cadeia de caracteres de qualificação mais curta `thisNamespace.xyz.xyzSub`.</span><span class="sxs-lookup"><span data-stu-id="8a461-122">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="8a461-123">Derrota da promoção de tipos para tipos parciais</span><span class="sxs-lookup"><span data-stu-id="8a461-123">Defeat of Type Promotion for Partial Types</span></span>  
 <span data-ttu-id="8a461-124">Se uma classe ou estrutura em um módulo usa o [parcial](../../../../visual-basic/language-reference/modifiers/partial.md) palavra-chave, a promoção de tipos é derrotada automaticamente por essa classe ou estrutura, se o namespace tenha um membro com o mesmo nome ou não.</span><span class="sxs-lookup"><span data-stu-id="8a461-124">If a class or structure inside a module uses the [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="8a461-125">Outros elementos no módulo ainda são qualificados para promoção de tipos.</span><span class="sxs-lookup"><span data-stu-id="8a461-125">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="8a461-126">**Consequências.**</span><span class="sxs-lookup"><span data-stu-id="8a461-126">**Consequences.**</span></span> <span data-ttu-id="8a461-127">Derrota da promoção de tipos de uma definição parcial pode causar resultados inesperados e até mesmo erros de compilador.</span><span class="sxs-lookup"><span data-stu-id="8a461-127">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="8a461-128">O exemplo a seguir mostra o esqueleto de definições parciais de uma classe, um deles é dentro de um módulo.</span><span class="sxs-lookup"><span data-stu-id="8a461-128">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 <span data-ttu-id="8a461-129">[!code-vb[VbVbalrDeclaredElements n º&4;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="8a461-129">[!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]</span></span>  
  
 <span data-ttu-id="8a461-130">No exemplo anterior, o desenvolvedor pode esperar o compilador para mesclar as duas definições parciais de `sampleClass`.</span><span class="sxs-lookup"><span data-stu-id="8a461-130">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="8a461-131">No entanto, o compilador não considera a promoção para a definição parcial dentro de `sampleModule`.</span><span class="sxs-lookup"><span data-stu-id="8a461-131">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="8a461-132">Como resultado, ele tenta compilar duas classes separados e distintas, ambas chamadas `sampleClass` , mas com caminhos diferentes de qualificação.</span><span class="sxs-lookup"><span data-stu-id="8a461-132">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="8a461-133">O compilador mescla definições parciais somente quando seus caminhos totalmente qualificados são idênticos.</span><span class="sxs-lookup"><span data-stu-id="8a461-133">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="8a461-134">Recomendações</span><span class="sxs-lookup"><span data-stu-id="8a461-134">Recommendations</span></span>  
 <span data-ttu-id="8a461-135">As recomendações a seguir representam uma boa prática de programação.</span><span class="sxs-lookup"><span data-stu-id="8a461-135">The following recommendations represent good programming practice.</span></span>  
  
-   <span data-ttu-id="8a461-136">**Nomes exclusivos.**</span><span class="sxs-lookup"><span data-stu-id="8a461-136">**Unique Names.**</span></span> <span data-ttu-id="8a461-137">Quando você tem controle total sobre a nomeação de elementos de programação, é sempre uma boa ideia usar nomes exclusivos em todos os lugares.</span><span class="sxs-lookup"><span data-stu-id="8a461-137">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="8a461-138">Nomes idênticos exigem qualificação extra e podem tornar seu código mais difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="8a461-138">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="8a461-139">Eles também podem levar a erros sutis e resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="8a461-139">They can also lead to subtle errors and unexpected results.</span></span>  
  
-   <span data-ttu-id="8a461-140">**Qualificação completa.**</span><span class="sxs-lookup"><span data-stu-id="8a461-140">**Full Qualification.**</span></span> <span data-ttu-id="8a461-141">Quando você estiver trabalhando com módulos e outros elementos no mesmo namespace, a abordagem mais segura é usar sempre qualificação completa para todos os elementos de programação.</span><span class="sxs-lookup"><span data-stu-id="8a461-141">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="8a461-142">Se a promoção de tipos é derrotada por um membro de módulo e você não qualificar esse membro totalmente, você poderá acessar inadvertidamente um elemento de programação diferente.</span><span class="sxs-lookup"><span data-stu-id="8a461-142">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a461-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a461-143">See Also</span></span>  
 <span data-ttu-id="8a461-144">[Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8a461-144">[Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md) </span></span>  
<span data-ttu-id="8a461-145"> [Instrução Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8a461-145"> [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md) </span></span>  
<span data-ttu-id="8a461-146"> [Parcial](../../../../visual-basic/language-reference/modifiers/partial.md) </span><span class="sxs-lookup"><span data-stu-id="8a461-146"> [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) </span></span>  
<span data-ttu-id="8a461-147"> [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span><span class="sxs-lookup"><span data-stu-id="8a461-147"> [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span></span>  
<span data-ttu-id="8a461-148"> [Como: controlar o escopo de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md) </span><span class="sxs-lookup"><span data-stu-id="8a461-148"> [How to: Control the Scope of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md) </span></span>  
<span data-ttu-id="8a461-149"> [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span><span class="sxs-lookup"><span data-stu-id="8a461-149"> [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span></span>
