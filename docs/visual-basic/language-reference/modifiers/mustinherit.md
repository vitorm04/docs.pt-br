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
ms.openlocfilehash: 0bda03d3c01356317fbcc56d44199ff4f9484b5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816558"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="f721b-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f721b-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="f721b-103">Especifica que uma classe pode ser usada apenas como uma classe base e que não é possível criar um objeto diretamente a partir dele.</span><span class="sxs-lookup"><span data-stu-id="f721b-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f721b-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="f721b-104">Remarks</span></span>  
 <span data-ttu-id="f721b-105">A finalidade de um *classe base* (também conhecido como um *classe abstrata*) é definir a funcionalidade comum a todas as classes derivadas dela.</span><span class="sxs-lookup"><span data-stu-id="f721b-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="f721b-106">Isso salva as classes derivadas de ter que redefinir os elementos comuns.</span><span class="sxs-lookup"><span data-stu-id="f721b-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="f721b-107">Em alguns casos, essa funcionalidade comum não está completa o suficiente para fazer um objeto utilizável e cada classe derivada define a funcionalidade ausente.</span><span class="sxs-lookup"><span data-stu-id="f721b-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="f721b-108">Nesse caso, você deseja que o código para criar objetos somente de classes derivadas de consumo.</span><span class="sxs-lookup"><span data-stu-id="f721b-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="f721b-109">Você usa `MustInherit` na classe base para impor isso.</span><span class="sxs-lookup"><span data-stu-id="f721b-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="f721b-110">Outro uso de um `MustInherit` classe é restringir a uma variável a um conjunto de classes relacionadas.</span><span class="sxs-lookup"><span data-stu-id="f721b-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="f721b-111">Você pode definir uma classe base e derivar todas essas classes relacionadas ele.</span><span class="sxs-lookup"><span data-stu-id="f721b-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="f721b-112">A classe base não precisa fornecer qualquer funcionalidade comum a todas as classes derivadas, mas ele pode servir como um filtro para atribuir valores a variáveis.</span><span class="sxs-lookup"><span data-stu-id="f721b-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="f721b-113">Se seu código consumidor declara uma variável como a classe base, o Visual Basic permite que você atribuir apenas um objeto de uma das classes derivadas para a variável.</span><span class="sxs-lookup"><span data-stu-id="f721b-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="f721b-114">O .NET Framework define várias `MustInherit` classes, entre elas <xref:System.Array>, <xref:System.Enum>, e <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="f721b-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="f721b-115"><xref:System.ValueType> é um exemplo de uma classe base que restringe a uma variável.</span><span class="sxs-lookup"><span data-stu-id="f721b-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="f721b-116">Todos os tipos de valor derivam <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="f721b-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="f721b-117">Se você declarar uma variável como <xref:System.ValueType>, você pode atribuir apenas os tipos de valor para a variável.</span><span class="sxs-lookup"><span data-stu-id="f721b-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f721b-118">Regras</span><span class="sxs-lookup"><span data-stu-id="f721b-118">Rules</span></span>  
  
-   <span data-ttu-id="f721b-119">**Contexto da declaração.**</span><span class="sxs-lookup"><span data-stu-id="f721b-119">**Declaration Context.**</span></span> <span data-ttu-id="f721b-120">Você pode usar `MustInherit` somente em um `Class` instrução.</span><span class="sxs-lookup"><span data-stu-id="f721b-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
-   <span data-ttu-id="f721b-121">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="f721b-121">**Combined Modifiers.**</span></span> <span data-ttu-id="f721b-122">Não é possível especificar `MustInherit` junto com `NotInheritable` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="f721b-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f721b-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f721b-123">Example</span></span>  
 <span data-ttu-id="f721b-124">O exemplo a seguir ilustra a herança forçada e o substituindo forçado.</span><span class="sxs-lookup"><span data-stu-id="f721b-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="f721b-125">A classe base `shape` define uma variável `acrossLine`.</span><span class="sxs-lookup"><span data-stu-id="f721b-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="f721b-126">As classes `circle` e `square` derivam `shape`.</span><span class="sxs-lookup"><span data-stu-id="f721b-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="f721b-127">Eles herdam a definição de `acrossLine`, mas eles devem definir a função `area` porque esse cálculo é diferente para cada tipo de forma.</span><span class="sxs-lookup"><span data-stu-id="f721b-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="f721b-128">Você pode declarar `shape1` e `shape2` ser do tipo `shape`.</span><span class="sxs-lookup"><span data-stu-id="f721b-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="f721b-129">No entanto, você não pode criar um objeto de `shape` porque ele não tem a funcionalidade da função `area` e é marcado como `MustInherit`.</span><span class="sxs-lookup"><span data-stu-id="f721b-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="f721b-130">Porque elas são declaradas como `shape`, as variáveis `shape1` e `shape2` são restritos aos objetos de classes derivadas `circle` e `square`.</span><span class="sxs-lookup"><span data-stu-id="f721b-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="f721b-131">Visual Basic não permitem que você atribua qualquer outro objeto para essas variáveis, que lhe dá um alto nível de segurança de tipos.</span><span class="sxs-lookup"><span data-stu-id="f721b-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="f721b-132">Uso</span><span class="sxs-lookup"><span data-stu-id="f721b-132">Usage</span></span>  
 <span data-ttu-id="f721b-133">O `MustInherit` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="f721b-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="f721b-134">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="f721b-134">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f721b-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f721b-135">See also</span></span>

- [<span data-ttu-id="f721b-136">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="f721b-136">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="f721b-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="f721b-137">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="f721b-138">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="f721b-138">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="f721b-139">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="f721b-139">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
