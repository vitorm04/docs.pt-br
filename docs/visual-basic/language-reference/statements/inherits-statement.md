---
title: Instrução Inherits
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 6e6e9cc9210232059210862f2bda691c57b372d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353233"
---
# <a name="inherits-statement"></a><span data-ttu-id="3f9ea-102">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="3f9ea-102">Inherits Statement</span></span>
<span data-ttu-id="3f9ea-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f9ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f9ea-104">Syntax</span></span>  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="3f9ea-105">Partes</span><span class="sxs-lookup"><span data-stu-id="3f9ea-105">Parts</span></span>  
  
|<span data-ttu-id="3f9ea-106">Termo</span><span class="sxs-lookup"><span data-stu-id="3f9ea-106">Term</span></span>|<span data-ttu-id="3f9ea-107">Definição</span><span class="sxs-lookup"><span data-stu-id="3f9ea-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="3f9ea-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-108">Required.</span></span> <span data-ttu-id="3f9ea-109">The name of the class from which this class derives.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="3f9ea-110">\- ou -</span><span class="sxs-lookup"><span data-stu-id="3f9ea-110">-or-</span></span><br /><br /> <span data-ttu-id="3f9ea-111">The names of the interfaces from which this interface derives.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="3f9ea-112">Use commas to separate multiple names.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f9ea-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f9ea-113">Remarks</span></span>  
 <span data-ttu-id="3f9ea-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="3f9ea-115">It should immediately follow the `Class` or `Interface` statement.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="3f9ea-116">You can use `Inherits` only in a class or interface.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="3f9ea-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3f9ea-118">Regras</span><span class="sxs-lookup"><span data-stu-id="3f9ea-118">Rules</span></span>  
  
- <span data-ttu-id="3f9ea-119">**Class Inheritance.**</span><span class="sxs-lookup"><span data-stu-id="3f9ea-119">**Class Inheritance.**</span></span> <span data-ttu-id="3f9ea-120">If a class uses the `Inherits` statement, you can specify only one base class.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="3f9ea-121">A class cannot inherit from a class nested within it.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-121">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="3f9ea-122">**Interface Inheritance.**</span><span class="sxs-lookup"><span data-stu-id="3f9ea-122">**Interface Inheritance.**</span></span> <span data-ttu-id="3f9ea-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="3f9ea-124">You can inherit from two interfaces even if they each define a member with the same name.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="3f9ea-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="3f9ea-126">An interface cannot inherit from another interface with a more restrictive access level.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="3f9ea-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="3f9ea-128">An interface cannot inherit from an interface nested within it.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="3f9ea-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="3f9ea-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="3f9ea-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="3f9ea-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f9ea-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f9ea-133">Example</span></span>  
 <span data-ttu-id="3f9ea-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="3f9ea-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f9ea-135">Example</span></span>  
 <span data-ttu-id="3f9ea-136">The following example shows inheritance of multiple interfaces.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="3f9ea-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="3f9ea-138">A class that implements `thisInterface` must implement every member of every base interface.</span><span class="sxs-lookup"><span data-stu-id="3f9ea-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f9ea-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f9ea-139">See also</span></span>

- [<span data-ttu-id="3f9ea-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="3f9ea-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="3f9ea-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="3f9ea-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="3f9ea-142">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="3f9ea-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="3f9ea-143">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="3f9ea-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="3f9ea-144">Interfaces</span><span class="sxs-lookup"><span data-stu-id="3f9ea-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
