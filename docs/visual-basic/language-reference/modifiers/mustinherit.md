---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 5d622c1cff77a45c8de7772af7efbb73586f4400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602834"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="17891-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17891-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="17891-103">Especifica que uma classe pode ser usada somente como uma classe base e que não é possível criar um objeto diretamente dela.</span><span class="sxs-lookup"><span data-stu-id="17891-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17891-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="17891-104">Remarks</span></span>  
 <span data-ttu-id="17891-105">A finalidade de um *classe base* (também conhecido como um *classe abstrata*) é definir a funcionalidade que é comum a todas as classes derivadas dela.</span><span class="sxs-lookup"><span data-stu-id="17891-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="17891-106">Isso salva as classes derivadas de ter que redefinir os elementos comuns.</span><span class="sxs-lookup"><span data-stu-id="17891-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="17891-107">Em alguns casos, essa funcionalidade comum não está completa para fazer um objeto utilizável, e cada classe derivada define a funcionalidade ausente.</span><span class="sxs-lookup"><span data-stu-id="17891-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="17891-108">Nesse caso, você deseja que o código para criar objetos somente de classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="17891-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="17891-109">Você usa `MustInherit` na classe base para impor isso.</span><span class="sxs-lookup"><span data-stu-id="17891-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="17891-110">Outro uso de um `MustInherit` classe é restringir uma variável para um conjunto de classes relacionadas.</span><span class="sxs-lookup"><span data-stu-id="17891-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="17891-111">Você pode definir uma classe base e derivam todas essas classes relacionadas ele.</span><span class="sxs-lookup"><span data-stu-id="17891-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="17891-112">A classe base não precisa fornecer qualquer funcionalidade comum a todas as classes derivadas, mas pode servir como um filtro para atribuir valores a variáveis.</span><span class="sxs-lookup"><span data-stu-id="17891-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="17891-113">Se o código declara uma variável como a classe base, o Visual Basic permite atribuir apenas um objeto de uma das classes derivadas para a variável.</span><span class="sxs-lookup"><span data-stu-id="17891-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="17891-114">O .NET Framework define vários `MustInherit` classes, entre eles <xref:System.Array>, <xref:System.Enum>, e <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="17891-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="17891-115"><xref:System.ValueType> é um exemplo de uma classe base que restringe a uma variável.</span><span class="sxs-lookup"><span data-stu-id="17891-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="17891-116">Todos os tipos de valor derivam <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="17891-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="17891-117">Se você declarar uma variável como <xref:System.ValueType>, você pode atribuir apenas os tipos de valor para a variável.</span><span class="sxs-lookup"><span data-stu-id="17891-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="17891-118">Regras</span><span class="sxs-lookup"><span data-stu-id="17891-118">Rules</span></span>  
  
-   <span data-ttu-id="17891-119">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="17891-119">**Declaration Context.**</span></span> <span data-ttu-id="17891-120">Você pode usar `MustInherit` somente em um `Class` instrução.</span><span class="sxs-lookup"><span data-stu-id="17891-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
-   <span data-ttu-id="17891-121">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="17891-121">**Combined Modifiers.**</span></span> <span data-ttu-id="17891-122">Não é possível especificar `MustInherit` junto com `NotInheritable` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="17891-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17891-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17891-123">Example</span></span>  
 <span data-ttu-id="17891-124">O exemplo a seguir ilustra a herança forçada e a substituição forçado.</span><span class="sxs-lookup"><span data-stu-id="17891-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="17891-125">A classe base `shape` define uma variável `acrossLine`.</span><span class="sxs-lookup"><span data-stu-id="17891-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="17891-126">As classes `circle` e `square` derivam `shape`.</span><span class="sxs-lookup"><span data-stu-id="17891-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="17891-127">Eles herdam a definição de `acrossLine`, mas eles devem definir a função `area` porque esse cálculo é diferente para cada tipo de forma.</span><span class="sxs-lookup"><span data-stu-id="17891-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 <span data-ttu-id="17891-128">Você pode declarar `shape1` e `shape2` ser do tipo `shape`.</span><span class="sxs-lookup"><span data-stu-id="17891-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="17891-129">No entanto, você não pode criar um objeto de `shape` porque ele não tem a funcionalidade da função `area` e está marcado como `MustInherit`.</span><span class="sxs-lookup"><span data-stu-id="17891-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="17891-130">Porque eles são declarados como `shape`, as variáveis `shape1` e `shape2` restrito a objetos das classes derivadas `circle` e `square`.</span><span class="sxs-lookup"><span data-stu-id="17891-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="17891-131">Visual Basic não permitem que você atribua qualquer outro objeto essas variáveis, que dá a você um alto nível de segurança de tipo.</span><span class="sxs-lookup"><span data-stu-id="17891-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="17891-132">Uso</span><span class="sxs-lookup"><span data-stu-id="17891-132">Usage</span></span>  
 <span data-ttu-id="17891-133">O `MustInherit` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="17891-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="17891-134">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="17891-134">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="17891-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17891-135">See Also</span></span>  
 [<span data-ttu-id="17891-136">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="17891-136">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="17891-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="17891-137">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [<span data-ttu-id="17891-138">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="17891-138">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="17891-139">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="17891-139">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
