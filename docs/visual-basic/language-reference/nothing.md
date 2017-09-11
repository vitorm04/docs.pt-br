---
title: Nada (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Nothing
- vb.Nothing
dev_langs:
- VB
helpviewer_keywords:
- Nothing keyword
- Nothing keyword, syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
caps.latest.revision: 31
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
ms.openlocfilehash: eaad4ac4dba83000a2f96194aa519e4d930f9fd4
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="nothing-visual-basic"></a><span data-ttu-id="7c004-102">Nada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c004-102">Nothing (Visual Basic)</span></span>
<span data-ttu-id="7c004-103">Representa o valor padrão de qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="7c004-103">Represents the default value of any data type.</span></span> <span data-ttu-id="7c004-104">Para tipos de referência, o valor padrão é o `null` referência.</span><span class="sxs-lookup"><span data-stu-id="7c004-104">For reference types, the default value is the `null` reference.</span></span> <span data-ttu-id="7c004-105">Para tipos de valor, o valor padrão depende se o tipo de valor é anulável.</span><span class="sxs-lookup"><span data-stu-id="7c004-105">For value types, the default value depends on whether the value type is nullable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c004-106">Para tipos de valor não nulo, `Nothing` no Visual Basic difere `null` em c#.</span><span class="sxs-lookup"><span data-stu-id="7c004-106">For non-nullable value types, `Nothing` in Visual Basic differs from `null` in C#.</span></span> <span data-ttu-id="7c004-107">No Visual Basic, se você definir uma variável de um tipo de valor não nulo para `Nothing`, a variável é definida como o valor padrão para seu tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="7c004-107">In Visual Basic, if you set a variable of a non-nullable value type to `Nothing`, the variable is set to the default value for its declared type.</span></span> <span data-ttu-id="7c004-108">No c#, se você atribuir uma variável de um tipo de valor não nulo para `null`, ocorrerá um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="7c004-108">In C#, if you assign a variable of a non-nullable value type to `null`, a compile-time error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c004-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c004-109">Remarks</span></span>  
 <span data-ttu-id="7c004-110">`Nothing`representa o valor padrão de um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="7c004-110">`Nothing` represents the default value of a data type.</span></span> <span data-ttu-id="7c004-111">O valor padrão depende se a variável é de um tipo de valor ou de um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="7c004-111">The default value depends on whether the variable is of a value type or of a reference type.</span></span>  
  
 <span data-ttu-id="7c004-112">Uma variável de um *tipo de valor* contém diretamente seu valor.</span><span class="sxs-lookup"><span data-stu-id="7c004-112">A variable of a *value type* directly contains its value.</span></span> <span data-ttu-id="7c004-113">Tipos de valor incluem todos os tipos de dados numéricos, `Boolean`, `Char`, `Date`, todas as estruturas e todas as enumerações.</span><span class="sxs-lookup"><span data-stu-id="7c004-113">Value types include all numeric data types, `Boolean`, `Char`, `Date`, all structures, and all enumerations.</span></span> <span data-ttu-id="7c004-114">Uma variável de um *tipo de referência* armazena uma referência a uma instância do objeto na memória.</span><span class="sxs-lookup"><span data-stu-id="7c004-114">A variable of a *reference type* stores a reference to an instance of the object in memory.</span></span> <span data-ttu-id="7c004-115">Tipos de referência incluem classes, matrizes, delegados e cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7c004-115">Reference types include classes, arrays, delegates, and strings.</span></span> <span data-ttu-id="7c004-116">Para obter mais informações, consulte [tipos de valor e tipos de referência](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="7c004-116">For more information, see [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
 <span data-ttu-id="7c004-117">Se uma variável é de um valor de tipo, o comportamento de `Nothing` depende se a variável for de um tipo de dados anulável.</span><span class="sxs-lookup"><span data-stu-id="7c004-117">If a variable is of a value type, the behavior of `Nothing` depends on whether the variable is of a nullable data type.</span></span> <span data-ttu-id="7c004-118">Para representar um tipo de valor anulável, adicione um `?` modificador para o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="7c004-118">To represent a nullable value type, add a `?` modifier to the type name.</span></span> <span data-ttu-id="7c004-119">Atribuindo `Nothing` a uma variável anulável define o valor como `null`.</span><span class="sxs-lookup"><span data-stu-id="7c004-119">Assigning `Nothing` to a nullable variable sets the value to `null`.</span></span> <span data-ttu-id="7c004-120">Para obter mais informações e exemplos, consulte [tipos de valor anulável](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="7c004-120">For more information and examples, see [Nullable Value Types](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span>  
  
 <span data-ttu-id="7c004-121">Se for uma variável de um tipo de valor não é anulável, atribuindo `Nothing` para ele define como o valor padrão para seu tipo declarado.</span><span class="sxs-lookup"><span data-stu-id="7c004-121">If a variable is of a value type that is not nullable, assigning `Nothing` to it sets it to the default value for its declared type.</span></span> <span data-ttu-id="7c004-122">Se o tipo contém membros variáveis, eles são definidos para seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="7c004-122">If that type contains variable members, they are all set to their default values.</span></span> <span data-ttu-id="7c004-123">O exemplo a seguir ilustra isso para tipos escalares.</span><span class="sxs-lookup"><span data-stu-id="7c004-123">The following example illustrates this for scalar types.</span></span>  
  
 <span data-ttu-id="7c004-124">[!code-vb[VbVbalrKeywords&#7;](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7c004-124">[!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]</span></span>  
  
 <span data-ttu-id="7c004-125">Se for uma variável do tipo de referência, atribuindo `Nothing` à variável define como um `null` referência do tipo da variável.</span><span class="sxs-lookup"><span data-stu-id="7c004-125">If a variable is of a reference type, assigning `Nothing` to the variable sets it to a `null` reference of the variable's type.</span></span> <span data-ttu-id="7c004-126">Uma variável que é definida como um `null` referência não está associada a qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="7c004-126">A variable that is set to a `null` reference is not associated with any object.</span></span> <span data-ttu-id="7c004-127">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="7c004-127">The following example demonstrates this.</span></span>  
  
 <span data-ttu-id="7c004-128">[!code-vb[VbVbalrKeywords n º&8;](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7c004-128">[!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]</span></span>  
  
 <span data-ttu-id="7c004-129">Ao verificar se uma referência (ou o tipo de valor anulável) é variável `null`, não use `= Nothing` ou `<> Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7c004-129">When checking whether a reference (or nullable value type) variable is `null`, do not use `= Nothing` or `<> Nothing`.</span></span> <span data-ttu-id="7c004-130">Sempre use `Is Nothing` ou `IsNot Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7c004-130">Always use `Is Nothing` or `IsNot Nothing`.</span></span>  
  
 <span data-ttu-id="7c004-131">Cadeias de caracteres no Visual Basic, a cadeia de caracteres vazia é igual a `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7c004-131">For strings in Visual Basic, the empty string equals `Nothing`.</span></span> <span data-ttu-id="7c004-132">Portanto, `"" = Nothing` é verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="7c004-132">Therefore, `"" = Nothing` is true.</span></span>  
  
 <span data-ttu-id="7c004-133">O exemplo a seguir mostra as comparações que usam o `Is` e `IsNot` operadores.</span><span class="sxs-lookup"><span data-stu-id="7c004-133">The following example shows comparisons that use the `Is` and `IsNot` operators.</span></span>  
  
 <span data-ttu-id="7c004-134">[!code-vb[VbVbalrKeywords n º&9;](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="7c004-134">[!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]</span></span>  
  
 <span data-ttu-id="7c004-135">Se você declarar uma variável sem usar um `As` cláusula e defina-o como `Nothing`, a variável tem um tipo de `Object`.</span><span class="sxs-lookup"><span data-stu-id="7c004-135">If you declare a variable without using an `As` clause and set it to `Nothing`, the variable has a type of `Object`.</span></span> <span data-ttu-id="7c004-136">Um exemplo disso é `Dim something = Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7c004-136">An example of this is `Dim something = Nothing`.</span></span> <span data-ttu-id="7c004-137">Um erro de tempo de compilação nesse caso ocorre quando `Option Strict` está em e `Option Infer` está desativado.</span><span class="sxs-lookup"><span data-stu-id="7c004-137">A compile-time error occurs in this case when `Option Strict` is on and `Option Infer` is off.</span></span>  
  
 <span data-ttu-id="7c004-138">Quando você atribui `Nothing` a uma variável de objeto, ele não se refere a qualquer instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="7c004-138">When you assign `Nothing` to an object variable, it no longer refers to any object instance.</span></span> <span data-ttu-id="7c004-139">Se a variável tivesse anteriormente referenciado uma instância, defini-la como `Nothing` finaliza a instância em si.</span><span class="sxs-lookup"><span data-stu-id="7c004-139">If the variable had previously referred to an instance, setting it to `Nothing` does not terminate the instance itself.</span></span> <span data-ttu-id="7c004-140">A instância é finalizada, e os recursos de memória e do sistema associados a ele são liberados, somente após o coletor de lixo (GC) detectar que não há referências ativas restantes.</span><span class="sxs-lookup"><span data-stu-id="7c004-140">The instance is terminated, and the memory and system resources associated with it are released, only after the garbage collector (GC) detects that there are no active references remaining.</span></span>  
  
 <span data-ttu-id="7c004-141">`Nothing`difere de <xref:System.DBNull>objeto que representa um variant não inicializado ou uma coluna de banco de dados que não existe.</xref:System.DBNull></span><span class="sxs-lookup"><span data-stu-id="7c004-141">`Nothing` differs from the <xref:System.DBNull> object, which represents an uninitialized variant or a nonexistent database column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c004-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c004-142">See Also</span></span>  
 <span data-ttu-id="7c004-143">[Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7c004-143">[Dim Statement](../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="7c004-144"> [Vida útil do objeto: Como os objetos são criados e destruídos](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md) </span><span class="sxs-lookup"><span data-stu-id="7c004-144"> [Object Lifetime: How Objects Are Created and Destroyed](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md) </span></span>  
<span data-ttu-id="7c004-145"> [Tempo de vida no Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md) </span><span class="sxs-lookup"><span data-stu-id="7c004-145"> [Lifetime in Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md) </span></span>  
<span data-ttu-id="7c004-146"> [Operador is](../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="7c004-146"> [Is Operator](../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="7c004-147"> [Operador IsNot](../../visual-basic/language-reference/operators/isnot-operator.md) </span><span class="sxs-lookup"><span data-stu-id="7c004-147"> [IsNot Operator](../../visual-basic/language-reference/operators/isnot-operator.md) </span></span>  
<span data-ttu-id="7c004-148"> [Tipos de Valor Anulável](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="7c004-148"> [Nullable Value Types](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)</span></span>
