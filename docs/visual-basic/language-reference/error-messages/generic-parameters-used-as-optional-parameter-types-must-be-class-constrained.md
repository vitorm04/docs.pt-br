---
title: Parâmetros genéricos usados como tipos de parâmetro opcionais devem ter a classe restrita
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 7e2b59f758ef236717a912694576b514e2ae8a60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="2e5c1-102">Parâmetros genéricos usados como tipos de parâmetro opcionais devem ter a classe restrita</span><span class="sxs-lookup"><span data-stu-id="2e5c1-102">Generic parameters used as optional parameter types must be class constrained</span></span>
<span data-ttu-id="2e5c1-103">Um procedimento é declarado com um parâmetro opcional que usa um parâmetro de tipo que não está restrita a conter um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="2e5c1-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="2e5c1-104">Você sempre deve fornecer um valor padrão para cada parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="2e5c1-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="2e5c1-105">Se o parâmetro é de um tipo de referência, o valor opcional deve ser `Nothing`, que é um valor válido para qualquer tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="2e5c1-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="2e5c1-106">No entanto, se o parâmetro é de um tipo de valor, esse tipo deve ser um tipo de dados elementar predefinido pelo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2e5c1-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="2e5c1-107">Isso ocorre porque um tipo de valor composto, como uma estrutura definida pelo usuário, possui nenhum valor padrão válido.</span><span class="sxs-lookup"><span data-stu-id="2e5c1-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="2e5c1-108">Quando você usa um parâmetro de tipo para um parâmetro opcional, você deve assegurar-se de um tipo de referência para evitar a possibilidade de um tipo de valor sem nenhum valor padrão válido.</span><span class="sxs-lookup"><span data-stu-id="2e5c1-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="2e5c1-109">Isso significa que você deve restringir o parâmetro de tipo com o `Class` palavra-chave ou com o nome de uma classe específica.</span><span class="sxs-lookup"><span data-stu-id="2e5c1-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="2e5c1-110">**ID do erro:** BC32124</span><span class="sxs-lookup"><span data-stu-id="2e5c1-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2e5c1-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2e5c1-111">To correct this error</span></span>  
  
-   <span data-ttu-id="2e5c1-112">Restringir o parâmetro de tipo para aceitar somente um tipo de referência, ou não usá-lo para o parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="2e5c1-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e5c1-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e5c1-113">See Also</span></span>  
 [<span data-ttu-id="2e5c1-114">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e5c1-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="2e5c1-115">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="2e5c1-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="2e5c1-116">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="2e5c1-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="2e5c1-117">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="2e5c1-117">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [<span data-ttu-id="2e5c1-118">Estruturas</span><span class="sxs-lookup"><span data-stu-id="2e5c1-118">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="2e5c1-119">Nothing</span><span class="sxs-lookup"><span data-stu-id="2e5c1-119">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
