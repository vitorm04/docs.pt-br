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
ms.openlocfilehash: 43a8aa4e9e04ee035cb52e9f829de13e5c022217
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604335"
---
# <a name="inherits-statement"></a><span data-ttu-id="2729a-102">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="2729a-102">Inherits Statement</span></span>
<span data-ttu-id="2729a-103">Faz com que a classe ou interface atual herde de atributos, variáveis, propriedades, procedimentos e eventos de outra classe ou conjunto de interfaces.</span><span class="sxs-lookup"><span data-stu-id="2729a-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2729a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2729a-104">Syntax</span></span>  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="2729a-105">Partes</span><span class="sxs-lookup"><span data-stu-id="2729a-105">Parts</span></span>  
  
|<span data-ttu-id="2729a-106">Termo</span><span class="sxs-lookup"><span data-stu-id="2729a-106">Term</span></span>|<span data-ttu-id="2729a-107">Definição</span><span class="sxs-lookup"><span data-stu-id="2729a-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="2729a-108">Obrigatório.</span><span class="sxs-lookup"><span data-stu-id="2729a-108">Required.</span></span> <span data-ttu-id="2729a-109">O nome da classe da qual essa classe deriva.</span><span class="sxs-lookup"><span data-stu-id="2729a-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="2729a-110">-ou-</span><span class="sxs-lookup"><span data-stu-id="2729a-110">-or-</span></span><br /><br /> <span data-ttu-id="2729a-111">Os nomes das interfaces da qual esta interface derivada.</span><span class="sxs-lookup"><span data-stu-id="2729a-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="2729a-112">Use vírgulas para separar vários nomes.</span><span class="sxs-lookup"><span data-stu-id="2729a-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2729a-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="2729a-113">Remarks</span></span>  
 <span data-ttu-id="2729a-114">Se usado, o `Inherits` instrução deve ser a primeira linha não vazia e que não seja de comentários em uma definição de classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="2729a-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="2729a-115">Você deve seguir imediatamente a `Class` ou `Interface` instrução.</span><span class="sxs-lookup"><span data-stu-id="2729a-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="2729a-116">Você pode usar `Inherits` somente em uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="2729a-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="2729a-117">Isso significa que o contexto da declaração para uma herança não pode ser um arquivo de origem, namespace, estrutura, módulo, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="2729a-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2729a-118">Regras</span><span class="sxs-lookup"><span data-stu-id="2729a-118">Rules</span></span>  
  
-   <span data-ttu-id="2729a-119">**Herança de classe.**</span><span class="sxs-lookup"><span data-stu-id="2729a-119">**Class Inheritance.**</span></span> <span data-ttu-id="2729a-120">Se uma classe usa a `Inherits` instrução, você pode especificar apenas uma classe base.</span><span class="sxs-lookup"><span data-stu-id="2729a-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="2729a-121">Uma classe não pode herdar de uma classe aninhada dentro dele.</span><span class="sxs-lookup"><span data-stu-id="2729a-121">A class cannot inherit from a class nested within it.</span></span>  
  
-   <span data-ttu-id="2729a-122">**Herança de interface.**</span><span class="sxs-lookup"><span data-stu-id="2729a-122">**Interface Inheritance.**</span></span> <span data-ttu-id="2729a-123">Se uma interface usa o `Inherits` instrução, você pode especificar uma ou mais interfaces base.</span><span class="sxs-lookup"><span data-stu-id="2729a-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="2729a-124">Você pode herdar de duas interfaces mesmo se cada uma define um membro com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="2729a-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="2729a-125">Se você fizer isso, o código de implementação deve usar qualificação de nome para especificar qual membro que está implementando.</span><span class="sxs-lookup"><span data-stu-id="2729a-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="2729a-126">Uma interface não pode herdar de outra interface com um nível de acesso mais restritivo.</span><span class="sxs-lookup"><span data-stu-id="2729a-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="2729a-127">Por exemplo, um `Public` interface não pode herdar de um `Friend` interface.</span><span class="sxs-lookup"><span data-stu-id="2729a-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="2729a-128">Uma interface não pode herdar de uma interface aninhada dentro dele.</span><span class="sxs-lookup"><span data-stu-id="2729a-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="2729a-129">Um exemplo de herança de classe do .NET Framework é o <xref:System.ArgumentException> classe que herde o <xref:System.SystemException> classe.</span><span class="sxs-lookup"><span data-stu-id="2729a-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="2729a-130">Isso fornece ao <xref:System.ArgumentException> todas as propriedades predefinidas e os procedimentos exigidos por exceções de sistema, como o <xref:System.Exception.Message%2A> propriedade e o <xref:System.Exception.ToString%2A> método.</span><span class="sxs-lookup"><span data-stu-id="2729a-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="2729a-131">Um exemplo de herança de interface no .NET Framework é o <xref:System.Collections.ICollection> interface que herda o <xref:System.Collections.IEnumerable> interface.</span><span class="sxs-lookup"><span data-stu-id="2729a-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="2729a-132">Isso faz com que <xref:System.Collections.ICollection> para herdar a definição do enumerador necessário para percorrer uma coleção.</span><span class="sxs-lookup"><span data-stu-id="2729a-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2729a-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2729a-133">Example</span></span>  
 <span data-ttu-id="2729a-134">O exemplo a seguir usa o `Inherits` instrução para mostrar como uma classe chamada `thisClass` pode herdar todos os membros de uma classe base chamada `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="2729a-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="2729a-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2729a-135">Example</span></span>  
 <span data-ttu-id="2729a-136">O exemplo a seguir mostra a herança de várias interfaces.</span><span class="sxs-lookup"><span data-stu-id="2729a-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 <span data-ttu-id="2729a-137">A interface nomeada `thisInterface` agora inclui todas as definições no <xref:System.IComparable>, <xref:System.IDisposable>, e <xref:System.IFormattable> interfaces os membros herdados fornecem respectivamente para comparação de tipo específico de dois objetos, o liberar os recursos alocados e expressar o valor de um objeto como um `String`.</span><span class="sxs-lookup"><span data-stu-id="2729a-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="2729a-138">Uma classe que implementa `thisInterface` deve implementar cada membro de interface base.</span><span class="sxs-lookup"><span data-stu-id="2729a-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2729a-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2729a-139">See Also</span></span>  
 [<span data-ttu-id="2729a-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="2729a-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [<span data-ttu-id="2729a-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="2729a-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [<span data-ttu-id="2729a-142">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="2729a-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="2729a-143">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="2729a-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="2729a-144">Interfaces</span><span class="sxs-lookup"><span data-stu-id="2729a-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
