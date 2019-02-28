---
title: Herda de instrução (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 18e35bab219003439136bc5d88f4b2f0ea6cdd1c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965742"
---
# <a name="inherits-statement"></a><span data-ttu-id="cdce9-102">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="cdce9-102">Inherits Statement</span></span>
<span data-ttu-id="cdce9-103">Faz com que a classe ou interface atual herde atributos, variáveis, propriedades, procedimentos e eventos de outra classe ou conjunto de interfaces.</span><span class="sxs-lookup"><span data-stu-id="cdce9-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdce9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdce9-104">Syntax</span></span>  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="cdce9-105">Partes</span><span class="sxs-lookup"><span data-stu-id="cdce9-105">Parts</span></span>  
  
|<span data-ttu-id="cdce9-106">Termo</span><span class="sxs-lookup"><span data-stu-id="cdce9-106">Term</span></span>|<span data-ttu-id="cdce9-107">Definição</span><span class="sxs-lookup"><span data-stu-id="cdce9-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="cdce9-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="cdce9-108">Required.</span></span> <span data-ttu-id="cdce9-109">O nome da classe da qual essa classe deriva.</span><span class="sxs-lookup"><span data-stu-id="cdce9-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="cdce9-110">-ou-</span><span class="sxs-lookup"><span data-stu-id="cdce9-110">-or-</span></span><br /><br /> <span data-ttu-id="cdce9-111">Os nomes das interfaces da qual deriva dessa interface.</span><span class="sxs-lookup"><span data-stu-id="cdce9-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="cdce9-112">Use vírgulas para separar vários nomes.</span><span class="sxs-lookup"><span data-stu-id="cdce9-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdce9-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="cdce9-113">Remarks</span></span>  
 <span data-ttu-id="cdce9-114">Se usado, o `Inherits` instrução deve ser a primeira linha não está em branco, sem comentário em uma definição de classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="cdce9-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="cdce9-115">Você deve seguir imediatamente o `Class` ou `Interface` instrução.</span><span class="sxs-lookup"><span data-stu-id="cdce9-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="cdce9-116">Você pode usar `Inherits` somente em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="cdce9-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="cdce9-117">Isso significa que o contexto da declaração para uma herança não pode ser um arquivo de origem, namespace, estrutura, módulo, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="cdce9-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="cdce9-118">Regras</span><span class="sxs-lookup"><span data-stu-id="cdce9-118">Rules</span></span>  
  
-   <span data-ttu-id="cdce9-119">**Herança de classe.**</span><span class="sxs-lookup"><span data-stu-id="cdce9-119">**Class Inheritance.**</span></span> <span data-ttu-id="cdce9-120">Se uma classe usa o `Inherits` instrução, você pode especificar apenas uma classe base.</span><span class="sxs-lookup"><span data-stu-id="cdce9-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="cdce9-121">Uma classe não pode herdar de uma classe aninhada dentro dele.</span><span class="sxs-lookup"><span data-stu-id="cdce9-121">A class cannot inherit from a class nested within it.</span></span>  
  
-   <span data-ttu-id="cdce9-122">**Herança de interface.**</span><span class="sxs-lookup"><span data-stu-id="cdce9-122">**Interface Inheritance.**</span></span> <span data-ttu-id="cdce9-123">Se uma interface usa o `Inherits` instrução, você pode especificar uma ou mais interfaces base.</span><span class="sxs-lookup"><span data-stu-id="cdce9-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="cdce9-124">Você pode herdar de duas interfaces, mesmo se cada um deles definir um membro com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="cdce9-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="cdce9-125">Se você fizer isso, o código de implementação deve usar a qualificação de nome para especificar qual membro que está implementando.</span><span class="sxs-lookup"><span data-stu-id="cdce9-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="cdce9-126">Uma interface não pode herdar de outra interface com um nível de acesso mais restritivo.</span><span class="sxs-lookup"><span data-stu-id="cdce9-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="cdce9-127">Por exemplo, uma `Public` interface não pode herdar de um `Friend` interface.</span><span class="sxs-lookup"><span data-stu-id="cdce9-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="cdce9-128">Uma interface não pode herdar de uma interface aninhada dentro dele.</span><span class="sxs-lookup"><span data-stu-id="cdce9-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="cdce9-129">Um exemplo de herança de classe no .NET Framework é o <xref:System.ArgumentException> classe, que herda o <xref:System.SystemException> classe.</span><span class="sxs-lookup"><span data-stu-id="cdce9-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="cdce9-130">Isso fornece ao <xref:System.ArgumentException> todas as propriedades pré-definidas e procedimentos exigidos por exceções de sistema, como o <xref:System.Exception.Message%2A> propriedade e o <xref:System.Exception.ToString%2A> método.</span><span class="sxs-lookup"><span data-stu-id="cdce9-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="cdce9-131">Um exemplo de herança de interface no .NET Framework é o <xref:System.Collections.ICollection> interface, que herda o <xref:System.Collections.IEnumerable> interface.</span><span class="sxs-lookup"><span data-stu-id="cdce9-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="cdce9-132">Isso faz com que <xref:System.Collections.ICollection> para herdar a definição do enumerador necessário para percorrer uma coleção.</span><span class="sxs-lookup"><span data-stu-id="cdce9-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdce9-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cdce9-133">Example</span></span>  
 <span data-ttu-id="cdce9-134">O exemplo a seguir usa o `Inherits` instrução para mostrar como uma classe chamada `thisClass` pode herdar todos os membros de uma classe base chamada `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="cdce9-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="cdce9-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cdce9-135">Example</span></span>  
 <span data-ttu-id="cdce9-136">O exemplo a seguir mostra a herança de várias interfaces.</span><span class="sxs-lookup"><span data-stu-id="cdce9-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="cdce9-137">Interface chamada `thisInterface` agora inclui todas as definições na <xref:System.IComparable>, <xref:System.IDisposable>, e <xref:System.IFormattable> interfaces membros herdados fornecem respectivamente para comparação de tipo específico de dois objetos, o liberando alocados a recursos e expressar o valor de um objeto como um `String`.</span><span class="sxs-lookup"><span data-stu-id="cdce9-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="cdce9-138">Uma classe que implementa `thisInterface` deve implementar todos os membros de interface base.</span><span class="sxs-lookup"><span data-stu-id="cdce9-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdce9-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdce9-139">See also</span></span>
- [<span data-ttu-id="cdce9-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="cdce9-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="cdce9-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="cdce9-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="cdce9-142">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="cdce9-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="cdce9-143">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="cdce9-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="cdce9-144">Interfaces</span><span class="sxs-lookup"><span data-stu-id="cdce9-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
