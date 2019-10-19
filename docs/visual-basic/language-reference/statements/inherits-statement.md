---
title: Instrução Inherits (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: e92e12908c89bb7a0bf385a2122b0c8f1eb8a6f7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581750"
---
# <a name="inherits-statement"></a><span data-ttu-id="60951-102">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="60951-102">Inherits Statement</span></span>
<span data-ttu-id="60951-103">Faz com que a classe ou a interface atual herde os atributos, variáveis, propriedades, procedimentos e eventos de outra classe ou conjunto de interfaces.</span><span class="sxs-lookup"><span data-stu-id="60951-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60951-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60951-104">Syntax</span></span>  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="60951-105">Partes</span><span class="sxs-lookup"><span data-stu-id="60951-105">Parts</span></span>  
  
|<span data-ttu-id="60951-106">Termo</span><span class="sxs-lookup"><span data-stu-id="60951-106">Term</span></span>|<span data-ttu-id="60951-107">Definição</span><span class="sxs-lookup"><span data-stu-id="60951-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="60951-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="60951-108">Required.</span></span> <span data-ttu-id="60951-109">O nome da classe da qual essa classe deriva.</span><span class="sxs-lookup"><span data-stu-id="60951-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="60951-110">\- ou -</span><span class="sxs-lookup"><span data-stu-id="60951-110">-or-</span></span><br /><br /> <span data-ttu-id="60951-111">Os nomes das interfaces das quais essa interface deriva.</span><span class="sxs-lookup"><span data-stu-id="60951-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="60951-112">Use vírgulas para separar vários nomes.</span><span class="sxs-lookup"><span data-stu-id="60951-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60951-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="60951-113">Remarks</span></span>  
 <span data-ttu-id="60951-114">Se usado, a instrução `Inherits` deve ser a primeira linha não em branco, que não seja de comentário em uma definição de classe ou de interface.</span><span class="sxs-lookup"><span data-stu-id="60951-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="60951-115">Ele deve seguir imediatamente a instrução `Class` ou `Interface`.</span><span class="sxs-lookup"><span data-stu-id="60951-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="60951-116">Você pode usar `Inherits` apenas em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="60951-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="60951-117">Isso significa que o contexto de declaração para uma herança não pode ser um arquivo de origem, namespace, estrutura, módulo, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="60951-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="60951-118">Regras</span><span class="sxs-lookup"><span data-stu-id="60951-118">Rules</span></span>  
  
- <span data-ttu-id="60951-119">**Herança de classe.**</span><span class="sxs-lookup"><span data-stu-id="60951-119">**Class Inheritance.**</span></span> <span data-ttu-id="60951-120">Se uma classe usar a instrução `Inherits`, você poderá especificar apenas uma classe base.</span><span class="sxs-lookup"><span data-stu-id="60951-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="60951-121">Uma classe não pode herdar de uma classe aninhada dentro dela.</span><span class="sxs-lookup"><span data-stu-id="60951-121">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="60951-122">**Herança de interface.**</span><span class="sxs-lookup"><span data-stu-id="60951-122">**Interface Inheritance.**</span></span> <span data-ttu-id="60951-123">Se uma interface usar a instrução `Inherits`, você poderá especificar uma ou mais interfaces base.</span><span class="sxs-lookup"><span data-stu-id="60951-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="60951-124">Você pode herdar de duas interfaces, mesmo se cada uma delas definir um membro com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="60951-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="60951-125">Se você fizer isso, o código de implementação deverá usar a qualificação de nome para especificar qual membro está sendo implementado.</span><span class="sxs-lookup"><span data-stu-id="60951-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="60951-126">Uma interface não pode herdar de outra interface com um nível de acesso mais restritivo.</span><span class="sxs-lookup"><span data-stu-id="60951-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="60951-127">Por exemplo, uma interface `Public` não pode herdar de uma interface `Friend`.</span><span class="sxs-lookup"><span data-stu-id="60951-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="60951-128">Uma interface não pode herdar de uma interface aninhada dentro dela.</span><span class="sxs-lookup"><span data-stu-id="60951-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="60951-129">Um exemplo de herança de classe no .NET Framework é a classe <xref:System.ArgumentException>, que é herdada da classe <xref:System.SystemException>.</span><span class="sxs-lookup"><span data-stu-id="60951-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="60951-130">Isso fornece a <xref:System.ArgumentException> todas as propriedades predefinidas e os procedimentos exigidos pelas exceções do sistema, como a propriedade <xref:System.Exception.Message%2A> e o método <xref:System.Exception.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="60951-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="60951-131">Um exemplo de herança de interface no .NET Framework é a interface <xref:System.Collections.ICollection>, que é herdada da interface <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="60951-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="60951-132">Isso faz com que <xref:System.Collections.ICollection> herdem a definição do enumerador necessário para atravessar uma coleção.</span><span class="sxs-lookup"><span data-stu-id="60951-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60951-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60951-133">Example</span></span>  
 <span data-ttu-id="60951-134">O exemplo a seguir usa a instrução `Inherits` para mostrar como uma classe denominada `thisClass` pode herdar todos os membros de uma classe base denominada `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="60951-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="60951-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60951-135">Example</span></span>  
 <span data-ttu-id="60951-136">O exemplo a seguir mostra a herança de várias interfaces.</span><span class="sxs-lookup"><span data-stu-id="60951-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="60951-137">A interface chamada `thisInterface` agora inclui todas as definições nas interfaces <xref:System.IComparable>, <xref:System.IDisposable> e <xref:System.IFormattable>. os membros herdados fornecem, respectivamente, a comparação específica de tipo de dois objetos, liberando recursos alocados e expressando o valor de um objeto como um `String`.</span><span class="sxs-lookup"><span data-stu-id="60951-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="60951-138">Uma classe que implementa `thisInterface` deve implementar todos os membros de cada interface base.</span><span class="sxs-lookup"><span data-stu-id="60951-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60951-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60951-139">See also</span></span>

- [<span data-ttu-id="60951-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="60951-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="60951-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="60951-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="60951-142">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="60951-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="60951-143">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="60951-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="60951-144">Interfaces</span><span class="sxs-lookup"><span data-stu-id="60951-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
