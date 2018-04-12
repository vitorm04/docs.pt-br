---
title: Chave (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20dbe4e67fb3e415ba0202555ace7fd5afed68d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="key-visual-basic"></a><span data-ttu-id="62142-102">Chave (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62142-102">Key (Visual Basic)</span></span>
<span data-ttu-id="62142-103">O `Key` palavra-chave permite que você especifique o comportamento para propriedades de tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="62142-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="62142-104">Somente as propriedades que você designar como propriedades de chave participam de testes de igualdade entre instâncias de tipo anônimo ou cálculo de valores de código de hash.</span><span class="sxs-lookup"><span data-stu-id="62142-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="62142-105">Os valores das propriedades de chave não podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="62142-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="62142-106">Designar uma propriedade de um tipo anônimo como uma propriedade de chave, colocando a palavra-chave `Key` na frente de sua declaração na lista de inicialização.</span><span class="sxs-lookup"><span data-stu-id="62142-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="62142-107">No exemplo a seguir, `Airline` e `FlightNo` são propriedades de chave, mas `Gate` não é.</span><span class="sxs-lookup"><span data-stu-id="62142-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 <span data-ttu-id="62142-108">Quando um novo tipo anônimo é criado, ele herda diretamente de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="62142-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="62142-109">O compilador desautoriza três membros herdados: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, e <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="62142-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="62142-110">O código de substituição que é produzido para <xref:System.Object.Equals%2A> e <xref:System.Object.GetHashCode%2A> baseia-se em Propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="62142-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="62142-111">Se não houver nenhuma propriedade de chave do tipo, <xref:System.Object.GetHashCode%2A> e <xref:System.Object.Equals%2A> não serão substituídos.</span><span class="sxs-lookup"><span data-stu-id="62142-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="62142-112">Igualdade</span><span class="sxs-lookup"><span data-stu-id="62142-112">Equality</span></span>  
 <span data-ttu-id="62142-113">Duas instâncias de tipo anônimo são iguais se estes forem instâncias do mesmo tipo e se os valores de suas propriedades de chave são iguais.</span><span class="sxs-lookup"><span data-stu-id="62142-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="62142-114">Nos exemplos a seguir, `flight2` é igual a `flight1` do exemplo anterior porque eles são instâncias do mesmo anônimo tipo e têm valores correspondentes para suas propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="62142-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="62142-115">No entanto, `flight3` não é igual a `flight1` porque ele tem um valor diferente para uma propriedade de chave, `FlightNo`.</span><span class="sxs-lookup"><span data-stu-id="62142-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="62142-116">Instância `flight4` não é do mesmo tipo como `flight1` porque eles designar propriedades diferentes como propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="62142-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 <span data-ttu-id="62142-117">Se duas instâncias são declaradas com apenas propriedades não-chave, idênticas em nome, tipo, ordem e valor, as duas instâncias não são iguais.</span><span class="sxs-lookup"><span data-stu-id="62142-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="62142-118">Uma instância sem propriedades de chave é igual somente a mesmo.</span><span class="sxs-lookup"><span data-stu-id="62142-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="62142-119">Para obter mais informações sobre as condições sob as quais duas instâncias de tipo anônimo são instâncias do mesmo tipo anônimo, consulte [tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="62142-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="62142-120">Cálculo de hash de código</span><span class="sxs-lookup"><span data-stu-id="62142-120">Hash Code Calculation</span></span>  
 <span data-ttu-id="62142-121">Como <xref:System.Object.Equals%2A>, a função de hash que é definida em <xref:System.Object.GetHashCode%2A> para um tipo anônimo baseado nas propriedades do tipo de chave.</span><span class="sxs-lookup"><span data-stu-id="62142-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="62142-122">Os exemplos a seguir mostram a interação entre propriedades de chave e hash de valores de código.</span><span class="sxs-lookup"><span data-stu-id="62142-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="62142-123">Instâncias de um tipo anônimo que têm os mesmos valores para todas as propriedades de chave têm o mesmo valor de código de hash, mesmo se as propriedades não-chave não têm valores correspondentes.</span><span class="sxs-lookup"><span data-stu-id="62142-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="62142-124">A instrução a seguir retorna `True`.</span><span class="sxs-lookup"><span data-stu-id="62142-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 <span data-ttu-id="62142-125">Instâncias de um tipo anônimo que têm valores diferentes para uma ou mais propriedades de chave têm valores de código hash diferente.</span><span class="sxs-lookup"><span data-stu-id="62142-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="62142-126">A instrução a seguir retorna `False`.</span><span class="sxs-lookup"><span data-stu-id="62142-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 <span data-ttu-id="62142-127">Instâncias de tipos anônimos que designar propriedades diferentes como propriedades de chave não são instâncias do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="62142-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="62142-128">Tiverem valores de código hash diferente, mesmo quando os nomes e valores de todas as propriedades são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="62142-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="62142-129">A instrução a seguir retorna `False`.</span><span class="sxs-lookup"><span data-stu-id="62142-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a><span data-ttu-id="62142-130">Valores somente leitura</span><span class="sxs-lookup"><span data-stu-id="62142-130">Read-Only Values</span></span>  
 <span data-ttu-id="62142-131">Os valores das propriedades de chave não podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="62142-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="62142-132">Por exemplo, em `flight1` nos exemplos anteriores, o `Airline` e `FlightNo` campos são somente leitura, mas `Gate` pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="62142-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="62142-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62142-133">See Also</span></span>  
 [<span data-ttu-id="62142-134">Definição do Tipo Anônimo</span><span class="sxs-lookup"><span data-stu-id="62142-134">Anonymous Type Definition</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [<span data-ttu-id="62142-135">Como inferir nomes e tipos de propriedade na declaração de tipo anônimo</span><span class="sxs-lookup"><span data-stu-id="62142-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [<span data-ttu-id="62142-136">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="62142-136">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
