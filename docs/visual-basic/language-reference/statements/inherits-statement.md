---
title: "Instrução Inherits | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Inherits
- Inherits
dev_langs:
- VB
helpviewer_keywords:
- Inherits statement
- Inherits statement, syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
caps.latest.revision: 16
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
ms.openlocfilehash: 43d28dd311e7ecefef91a79169ed7a240055c06e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="inherits-statement"></a><span data-ttu-id="9176d-102">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="9176d-102">Inherits Statement</span></span>
<span data-ttu-id="9176d-103">Faz com que a classe ou interface atual herde os atributos, variáveis, propriedades, procedimentos e eventos de outra classe ou conjunto de interfaces.</span><span class="sxs-lookup"><span data-stu-id="9176d-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9176d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9176d-104">Syntax</span></span>  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="9176d-105">Partes</span><span class="sxs-lookup"><span data-stu-id="9176d-105">Parts</span></span>  
  
|<span data-ttu-id="9176d-106">Termo</span><span class="sxs-lookup"><span data-stu-id="9176d-106">Term</span></span>|<span data-ttu-id="9176d-107">Definição</span><span class="sxs-lookup"><span data-stu-id="9176d-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="9176d-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9176d-108">Required.</span></span> <span data-ttu-id="9176d-109">O nome da classe da qual essa classe deriva.</span><span class="sxs-lookup"><span data-stu-id="9176d-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="9176d-110">-ou-</span><span class="sxs-lookup"><span data-stu-id="9176d-110">-or-</span></span><br /><br /> <span data-ttu-id="9176d-111">Os nomes das interfaces da qual esta interface deriva.</span><span class="sxs-lookup"><span data-stu-id="9176d-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="9176d-112">Use vírgulas para separar vários nomes.</span><span class="sxs-lookup"><span data-stu-id="9176d-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9176d-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="9176d-113">Remarks</span></span>  
 <span data-ttu-id="9176d-114">Se usado, o `Inherits` instrução deve ser a primeira linha não vazia e que não seja de comentários em uma definição de classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="9176d-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="9176d-115">Você deve seguir imediatamente o `Class` ou `Interface` instrução.</span><span class="sxs-lookup"><span data-stu-id="9176d-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="9176d-116">Você pode usar `Inherits` somente em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="9176d-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="9176d-117">Isso significa que o contexto da declaração para uma herança não pode ser um arquivo fonte, namespace, estrutura, módulo, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="9176d-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9176d-118">Regras</span><span class="sxs-lookup"><span data-stu-id="9176d-118">Rules</span></span>  
  
-   <span data-ttu-id="9176d-119">**Herança de classe.**</span><span class="sxs-lookup"><span data-stu-id="9176d-119">**Class Inheritance.**</span></span> <span data-ttu-id="9176d-120">Se uma classe usa a `Inherits` instrução, você pode especificar apenas uma classe base.</span><span class="sxs-lookup"><span data-stu-id="9176d-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="9176d-121">Uma classe não pode herdar de uma classe aninhada nela.</span><span class="sxs-lookup"><span data-stu-id="9176d-121">A class cannot inherit from a class nested within it.</span></span>  
  
-   <span data-ttu-id="9176d-122">**Herança da interface.**</span><span class="sxs-lookup"><span data-stu-id="9176d-122">**Interface Inheritance.**</span></span> <span data-ttu-id="9176d-123">Se uma interface usa a `Inherits` instrução, você pode especificar uma ou mais interfaces base.</span><span class="sxs-lookup"><span data-stu-id="9176d-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="9176d-124">Você pode herdar de duas interfaces mesmo se cada uma define um membro com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="9176d-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="9176d-125">Se você fizer isso, o código de implementação deve usar a qualificação de nome para especificar qual membro que está implementando.</span><span class="sxs-lookup"><span data-stu-id="9176d-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="9176d-126">Uma interface não pode herdar de outra interface com um nível de acesso mais restritivo.</span><span class="sxs-lookup"><span data-stu-id="9176d-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="9176d-127">Por exemplo, um `Public` interface não pode herdar de um `Friend` interface.</span><span class="sxs-lookup"><span data-stu-id="9176d-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="9176d-128">Uma interface não pode herdar de uma interface aninhada nela.</span><span class="sxs-lookup"><span data-stu-id="9176d-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="9176d-129">Um exemplo de herança de classe no .NET Framework é a <xref:System.ArgumentException>classe que herde a <xref:System.SystemException>classe.</xref:System.SystemException> </xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="9176d-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="9176d-130">Isso fornece ao <xref:System.ArgumentException>todas as propriedades predefinidas e procedimentos exigidos por exceções de sistema, como o <xref:System.Exception.Message%2A>propriedade e o <xref:System.Exception.ToString%2A>método.</xref:System.Exception.ToString%2A> </xref:System.Exception.Message%2A> </xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="9176d-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="9176d-131">Um exemplo de herança de interface no .NET Framework é o <xref:System.Collections.ICollection>interface, que herda o <xref:System.Collections.IEnumerable>interface.</xref:System.Collections.IEnumerable> </xref:System.Collections.ICollection></span><span class="sxs-lookup"><span data-stu-id="9176d-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="9176d-132">Isso faz com que <xref:System.Collections.ICollection>herde a definição do enumerador necessário para percorrer uma coleção.</xref:System.Collections.ICollection></span><span class="sxs-lookup"><span data-stu-id="9176d-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9176d-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9176d-133">Example</span></span>  
 <span data-ttu-id="9176d-134">O exemplo a seguir usa o `Inherits` instrução para mostrar como uma classe chamada `thisClass` pode herdar todos os membros de uma classe base chamada `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="9176d-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 <span data-ttu-id="9176d-135">[!code-vb[VbVbalrStatements&#37;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9176d-135">[!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="9176d-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9176d-136">Example</span></span>  
 <span data-ttu-id="9176d-137">O exemplo a seguir mostra a herança de várias interfaces.</span><span class="sxs-lookup"><span data-stu-id="9176d-137">The following example shows inheritance of multiple interfaces.</span></span>  
  
 <span data-ttu-id="9176d-138">[!code-vb[VbVbalrStatements&38;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="9176d-138">[!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]</span></span>  
  
 <span data-ttu-id="9176d-139">A interface denominada `thisInterface` inclui agora todas as definições no <xref:System.IComparable>, <xref:System.IDisposable>, e <xref:System.IFormattable>interfaces membros herdados oferecem respectivamente para comparação de tipo específico de dois objetos, liberando recursos alocados e expressar o valor de um objeto como um `String`.</xref:System.IFormattable> </xref:System.IDisposable> </xref:System.IComparable></span><span class="sxs-lookup"><span data-stu-id="9176d-139">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="9176d-140">Uma classe que implementa `thisInterface` deve implementar todo membro de interface base.</span><span class="sxs-lookup"><span data-stu-id="9176d-140">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9176d-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9176d-141">See Also</span></span>  
 <span data-ttu-id="9176d-142">[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md) </span><span class="sxs-lookup"><span data-stu-id="9176d-142">[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md) </span></span>  
<span data-ttu-id="9176d-143"> [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md) </span><span class="sxs-lookup"><span data-stu-id="9176d-143"> [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md) </span></span>  
<span data-ttu-id="9176d-144"> [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="9176d-144"> [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="9176d-145"> [Noções básicas sobre herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span><span class="sxs-lookup"><span data-stu-id="9176d-145"> [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span></span>  
<span data-ttu-id="9176d-146"> [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span><span class="sxs-lookup"><span data-stu-id="9176d-146"> [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span></span>
