---
title: "'<expression>' não pode ser usado como restrição de tipo"
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 6e55bfdc175f285b335512e64f4c2407bdb0e8c7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163084"
---
# <a name="bc32061-expression-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="87719-102">BC32061: ' \<expression> ' não pode ser usado como uma restrição de tipo</span><span class="sxs-lookup"><span data-stu-id="87719-102">BC32061: '\<expression>' cannot be used as a type constraint</span></span>

<span data-ttu-id="87719-103">Uma lista de restrições inclui uma expressão que não representa uma restrição válida em um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="87719-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>

 <span data-ttu-id="87719-104">Uma lista de restrições impõe requisitos no argumento de tipo passado para o parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="87719-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="87719-105">Você pode especificar os seguintes requisitos em qualquer combinação:</span><span class="sxs-lookup"><span data-stu-id="87719-105">You can specify the following requirements in any combination:</span></span>

- <span data-ttu-id="87719-106">O argumento de tipo deve implementar uma ou mais interfaces</span><span class="sxs-lookup"><span data-stu-id="87719-106">The type argument must implement one or more interfaces</span></span>

- <span data-ttu-id="87719-107">O argumento de tipo deve herdar de no máximo uma classe</span><span class="sxs-lookup"><span data-stu-id="87719-107">The type argument must inherit from at most one class</span></span>

- <span data-ttu-id="87719-108">O argumento de tipo deve expor um construtor sem parâmetros que o código de criação possa acessar (incluir a `New` restrição)</span><span class="sxs-lookup"><span data-stu-id="87719-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>

 <span data-ttu-id="87719-109">Se você não incluir nenhuma classe ou interface específica na lista de restrições, poderá impor um requisito mais geral especificando um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="87719-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>

- <span data-ttu-id="87719-110">O argumento de tipo deve ser um tipo de valor (incluir a `Structure` restrição)</span><span class="sxs-lookup"><span data-stu-id="87719-110">The type argument must be a value type (include the `Structure` constraint)</span></span>

- <span data-ttu-id="87719-111">O argumento de tipo deve ser um tipo de referência (incluir a `Class` restrição)</span><span class="sxs-lookup"><span data-stu-id="87719-111">The type argument must be a reference type (include the `Class` constraint)</span></span>

 <span data-ttu-id="87719-112">Não é possível especificar ambos `Structure` e `Class` para o mesmo parâmetro de tipo, e você não pode especificar um mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="87719-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>

 <span data-ttu-id="87719-113">**ID do erro:** BC32061</span><span class="sxs-lookup"><span data-stu-id="87719-113">**Error ID:** BC32061</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="87719-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="87719-114">To correct this error</span></span>

- <span data-ttu-id="87719-115">Verifique se a expressão e seus elementos estão escritos corretamente.</span><span class="sxs-lookup"><span data-stu-id="87719-115">Verify that the expression and its elements are spelled correctly.</span></span>

- <span data-ttu-id="87719-116">Se a expressão não for qualificada para a lista anterior de requisitos, remova-a da lista de restrições.</span><span class="sxs-lookup"><span data-stu-id="87719-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>

- <span data-ttu-id="87719-117">Se a expressão se referir a uma interface ou classe, verifique se o compilador tem acesso a essa interface ou classe.</span><span class="sxs-lookup"><span data-stu-id="87719-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="87719-118">Talvez seja necessário qualificar seu nome, e talvez seja necessário adicionar uma referência ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="87719-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="87719-119">Para obter mais informações, consulte "referências a projetos" em [referências a elementos declarados](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="87719-119">For more information, see "References to Projects" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87719-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="87719-120">See also</span></span>

- [<span data-ttu-id="87719-121">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87719-121">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="87719-122">Tipos de valor e referência</span><span class="sxs-lookup"><span data-stu-id="87719-122">Value Types and Reference Types</span></span>](../../programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="87719-123">Referências a elementos declarados</span><span class="sxs-lookup"><span data-stu-id="87719-123">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
