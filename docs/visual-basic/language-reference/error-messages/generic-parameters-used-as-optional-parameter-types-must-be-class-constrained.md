---
title: Parâmetros genéricos usados como tipos de parâmetro opcionais devem ter a classe restrita
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 2e3f50d08fdf78b5ca9bf9e3399b00ed0328320f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874035"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="9a61f-102">Parâmetros genéricos usados como tipos de parâmetro opcionais devem ter a classe restrita</span><span class="sxs-lookup"><span data-stu-id="9a61f-102">Generic parameters used as optional parameter types must be class constrained</span></span>

<span data-ttu-id="9a61f-103">Um procedimento é declarado com um parâmetro opcional que usa um parâmetro de tipo que não é restrito a ser um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="9a61f-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="9a61f-104">Você sempre deve fornecer um valor padrão para cada parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="9a61f-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="9a61f-105">Se o parâmetro for de um tipo de referência, o valor opcional deverá ser `Nothing` , que é um valor válido para qualquer tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="9a61f-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="9a61f-106">No entanto, se o parâmetro for de um tipo de valor, esse tipo deverá ser um tipo de dados elementar predefinido por Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9a61f-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="9a61f-107">Isso ocorre porque um tipo de valor composto, como uma estrutura definida pelo usuário, não tem um valor padrão válido.</span><span class="sxs-lookup"><span data-stu-id="9a61f-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="9a61f-108">Quando você usa um parâmetro de tipo para um parâmetro opcional, você deve garantir que ele seja de um tipo de referência para evitar a possibilidade de um tipo de valor sem um valor padrão válido.</span><span class="sxs-lookup"><span data-stu-id="9a61f-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="9a61f-109">Isso significa que você deve restringir o parâmetro de tipo com a `Class` palavra-chave ou com o nome de uma classe específica.</span><span class="sxs-lookup"><span data-stu-id="9a61f-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="9a61f-110">**ID do erro:** BC32124</span><span class="sxs-lookup"><span data-stu-id="9a61f-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9a61f-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9a61f-111">To correct this error</span></span>  
  
- <span data-ttu-id="9a61f-112">Restrinja o parâmetro de tipo para aceitar apenas um tipo de referência ou não use-o para o parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="9a61f-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a61f-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="9a61f-113">See also</span></span>

- [<span data-ttu-id="9a61f-114">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9a61f-114">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="9a61f-115">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="9a61f-115">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="9a61f-116">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="9a61f-116">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="9a61f-117">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="9a61f-117">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="9a61f-118">Estruturas</span><span class="sxs-lookup"><span data-stu-id="9a61f-118">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="9a61f-119">Nothing</span><span class="sxs-lookup"><span data-stu-id="9a61f-119">Nothing</span></span>](../nothing.md)
