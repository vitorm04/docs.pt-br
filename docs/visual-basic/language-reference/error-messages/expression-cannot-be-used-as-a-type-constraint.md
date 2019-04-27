---
title: "'<expression>' não pode ser usado como restrição de tipo"
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 8dbf510d7c6ee80e2dcd2f9d2552bc870413cbab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801472"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="07e42-102">'\<expressão >' não pode ser usado como restrição de tipo</span><span class="sxs-lookup"><span data-stu-id="07e42-102">'\<expression>' cannot be used as a type constraint</span></span>
<span data-ttu-id="07e42-103">Uma lista de restrições inclui uma expressão que não representa uma restrição válida em um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="07e42-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="07e42-104">Uma lista de restrição impõe requisitos o argumento de tipo passado para o parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="07e42-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="07e42-105">Você pode especificar os requisitos a seguir em qualquer combinação:</span><span class="sxs-lookup"><span data-stu-id="07e42-105">You can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="07e42-106">O argumento de tipo deve implementar uma ou mais interfaces</span><span class="sxs-lookup"><span data-stu-id="07e42-106">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="07e42-107">O argumento de tipo deve herdar de no máximo uma classe</span><span class="sxs-lookup"><span data-stu-id="07e42-107">The type argument must inherit from at most one class</span></span>  
  
-   <span data-ttu-id="07e42-108">O argumento de tipo deve expor um construtor sem parâmetros que o código de criação pode acessar (incluem o `New` restrição)</span><span class="sxs-lookup"><span data-stu-id="07e42-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="07e42-109">Se você não incluir qualquer interface ou classe específica na lista de restrição, você pode impor um requisito mais geral, especificando um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="07e42-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
-   <span data-ttu-id="07e42-110">O argumento de tipo deve ser um tipo de valor (incluem o `Structure` restrição)</span><span class="sxs-lookup"><span data-stu-id="07e42-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
-   <span data-ttu-id="07e42-111">O argumento de tipo deve ser um tipo de referência (incluem o `Class` restrição)</span><span class="sxs-lookup"><span data-stu-id="07e42-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="07e42-112">Não é possível especificar ambos `Structure` e `Class` para o mesmo tipo de parâmetro e você não pode especificar um mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="07e42-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="07e42-113">**ID do erro:** BC32061</span><span class="sxs-lookup"><span data-stu-id="07e42-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="07e42-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="07e42-114">To correct this error</span></span>  
  
-   <span data-ttu-id="07e42-115">Verifique se a expressão e seus elementos foram escritos corretamente.</span><span class="sxs-lookup"><span data-stu-id="07e42-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
-   <span data-ttu-id="07e42-116">Se a expressão não está qualificada para a lista anterior de requisitos, remova-o da lista de restrições.</span><span class="sxs-lookup"><span data-stu-id="07e42-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
-   <span data-ttu-id="07e42-117">Se a expressão se refere a uma interface ou classe, verifique se o compilador tem acesso a essa interface ou classe.</span><span class="sxs-lookup"><span data-stu-id="07e42-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="07e42-118">Talvez você precise qualificar seu nome, e talvez seja necessário adicionar uma referência ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="07e42-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="07e42-119">Para obter mais informações, consulte "Referências a projetos" em [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="07e42-119">For more information, see "References to Projects" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e42-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07e42-120">See also</span></span>

- [<span data-ttu-id="07e42-121">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07e42-121">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="07e42-122">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="07e42-122">Value Types and Reference Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="07e42-123">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="07e42-123">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
