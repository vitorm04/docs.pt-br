---
title: Chave (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AnonymousKey
dev_langs:
- VB
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: 22
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
ms.openlocfilehash: b4d83a7d8acb3ac4897213ec469b6b0fc0356045
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="key-visual-basic"></a><span data-ttu-id="81ae0-102">Chave (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81ae0-102">Key (Visual Basic)</span></span>
<span data-ttu-id="81ae0-103">O `Key` palavra-chave permite que você especifique o comportamento para propriedades de tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="81ae0-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="81ae0-104">Somente as propriedades que você designar como propriedades de chave participam de testes de igualdade entre instâncias de tipo anônimo ou cálculo dos valores de código de hash.</span><span class="sxs-lookup"><span data-stu-id="81ae0-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="81ae0-105">Os valores das propriedades de chave não podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="81ae0-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="81ae0-106">Você designa uma propriedade de um tipo anônimo como uma propriedade-chave colocando a palavra-chave `Key` na frente de sua declaração na lista de inicialização.</span><span class="sxs-lookup"><span data-stu-id="81ae0-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="81ae0-107">No exemplo a seguir, `Airline` e `FlightNo` propriedades-chave, mas `Gate` não é.</span><span class="sxs-lookup"><span data-stu-id="81ae0-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 <span data-ttu-id="81ae0-108">[!code-vb[VbVbalrAnonymousTypes&#26;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="81ae0-108">[!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]</span></span>  
  
 <span data-ttu-id="81ae0-109">Quando um novo tipo anônimo é criado, ele herda diretamente de <xref:System.Object>.</xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="81ae0-109">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="81ae0-110">O compilador desautoriza três membros herdados: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>e <xref:System.Object.ToString%2A>.</xref:System.Object.ToString%2A> </xref:System.Object.GetHashCode%2A> </xref:System.Object.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="81ae0-110">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="81ae0-111">O código de substituição é gerada para <xref:System.Object.Equals%2A>e <xref:System.Object.GetHashCode%2A>baseado nas propriedades de chave.</xref:System.Object.GetHashCode%2A> </xref:System.Object.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="81ae0-111">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="81ae0-112">Se não houver nenhuma propriedade de chave no tipo, <xref:System.Object.GetHashCode%2A>e <xref:System.Object.Equals%2A>não são substituídas.</xref:System.Object.Equals%2A> </xref:System.Object.GetHashCode%2A></span><span class="sxs-lookup"><span data-stu-id="81ae0-112">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="81ae0-113">Igualdade</span><span class="sxs-lookup"><span data-stu-id="81ae0-113">Equality</span></span>  
 <span data-ttu-id="81ae0-114">Duas instâncias de tipo anônimo são iguais se são instâncias do mesmo tipo e se os valores de suas propriedades de chave são iguais.</span><span class="sxs-lookup"><span data-stu-id="81ae0-114">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="81ae0-115">Nos exemplos a seguir, `flight2` é igual a `flight1` do exemplo anterior porque eles são instâncias do mesmo anônimo tipo e têm valores correspondentes para suas propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="81ae0-115">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="81ae0-116">No entanto, `flight3` não é igual a `flight1` porque ele tem um valor diferente para uma propriedade de chave, `FlightNo`.</span><span class="sxs-lookup"><span data-stu-id="81ae0-116">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="81ae0-117">Instância `flight4` não é do mesmo tipo como `flight1` porque eles designar propriedades diferentes como propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="81ae0-117">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 <span data-ttu-id="81ae0-118">[!code-vb[VbVbalrAnonymousTypes&#27;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="81ae0-118">[!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]</span></span>  
  
 <span data-ttu-id="81ae0-119">Se duas instâncias são declaradas com apenas propriedades não-chave, idênticas em nome, tipo, ordem e valor, as duas instâncias não são iguais.</span><span class="sxs-lookup"><span data-stu-id="81ae0-119">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="81ae0-120">Uma instância sem propriedades-chave é igual somente a mesmo.</span><span class="sxs-lookup"><span data-stu-id="81ae0-120">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="81ae0-121">Para obter mais informações sobre as condições sob as quais duas instâncias de tipo anônimo são instâncias do mesmo tipo anônimo, consulte [tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="81ae0-121">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="81ae0-122">Cálculo de código de hash</span><span class="sxs-lookup"><span data-stu-id="81ae0-122">Hash Code Calculation</span></span>  
 <span data-ttu-id="81ae0-123">Como <xref:System.Object.Equals%2A>, a função de hash que é definida em <xref:System.Object.GetHashCode%2A>para um tipo anônimo é com base nas propriedades do tipo de chave.</xref:System.Object.GetHashCode%2A> </xref:System.Object.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="81ae0-123">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="81ae0-124">Os exemplos a seguir mostram a interação entre propriedades de chave e hash de valores de código.</span><span class="sxs-lookup"><span data-stu-id="81ae0-124">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="81ae0-125">Instâncias de um tipo anônimo que têm os mesmos valores para todas as propriedades de chave têm o mesmo valor de código de hash, mesmo se as propriedades não-chave não tiver valores correspondentes.</span><span class="sxs-lookup"><span data-stu-id="81ae0-125">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="81ae0-126">A instrução a seguir retorna `True`.</span><span class="sxs-lookup"><span data-stu-id="81ae0-126">The following statement returns `True`.</span></span>  
  
 <span data-ttu-id="81ae0-127">[!code-vb[VbVbalrAnonymousTypes&#37;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="81ae0-127">[!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]</span></span>  
  
 <span data-ttu-id="81ae0-128">Instâncias de um tipo anônimo que têm valores diferentes para uma ou mais propriedades de chave têm valores de código de hash diferente.</span><span class="sxs-lookup"><span data-stu-id="81ae0-128">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="81ae0-129">A instrução a seguir retorna `False`.</span><span class="sxs-lookup"><span data-stu-id="81ae0-129">The following statement returns `False`.</span></span>  
  
 <span data-ttu-id="81ae0-130">[!code-vb[VbVbalrAnonymousTypes&38;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="81ae0-130">[!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]</span></span>  
  
 <span data-ttu-id="81ae0-131">Instâncias de tipos anônimos que designar propriedades diferentes como propriedades de chave não são instâncias do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="81ae0-131">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="81ae0-132">Elas têm valores de código de hash diferente mesmo quando os nomes e valores de todas as propriedades são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="81ae0-132">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="81ae0-133">A instrução a seguir retorna `False`.</span><span class="sxs-lookup"><span data-stu-id="81ae0-133">The following statement returns `False`.</span></span>  
  
 <span data-ttu-id="81ae0-134">[!code-vb[VbVbalrAnonymousTypes&#39;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="81ae0-134">[!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]</span></span>  
  
## <a name="read-only-values"></a><span data-ttu-id="81ae0-135">Valores somente leitura</span><span class="sxs-lookup"><span data-stu-id="81ae0-135">Read-Only Values</span></span>  
 <span data-ttu-id="81ae0-136">Os valores das propriedades de chave não podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="81ae0-136">The values of key properties cannot be changed.</span></span> <span data-ttu-id="81ae0-137">Por exemplo, em `flight1` nos exemplos anteriores, o `Airline` e `FlightNo` campos são somente leitura, mas `Gate` pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="81ae0-137">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 <span data-ttu-id="81ae0-138">[!code-vb[VbVbalrAnonymousTypes&#28;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="81ae0-138">[!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ae0-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81ae0-139">See Also</span></span>  
 <span data-ttu-id="81ae0-140">[Definição de tipo anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md) </span><span class="sxs-lookup"><span data-stu-id="81ae0-140">[Anonymous Type Definition](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md) </span></span>  
<span data-ttu-id="81ae0-141"> [Como: inferir nomes de propriedade e tipos nas declarações de tipo anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md) </span><span class="sxs-lookup"><span data-stu-id="81ae0-141"> [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md) </span></span>  
<span data-ttu-id="81ae0-142"> [Tipos Anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="81ae0-142"> [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span></span>
