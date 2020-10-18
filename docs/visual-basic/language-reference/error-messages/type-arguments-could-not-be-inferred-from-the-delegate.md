---
title: Não foi possível inferir argumentos de tipo a partir do delegado
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: f7937a34ab425da684f892250884d21e020e4c57
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161238"
---
# <a name="bc36564-type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="990a8-102">BC36564: não foi possível inferir os argumentos de tipo a partir do delegado</span><span class="sxs-lookup"><span data-stu-id="990a8-102">BC36564: Type arguments could not be inferred from the delegate</span></span>

<span data-ttu-id="990a8-103">Uma instrução de atribuição usa `AddressOf` para atribuir o endereço de um procedimento genérico a um delegado, mas não fornece nenhum argumento de tipo para o procedimento genérico.</span><span class="sxs-lookup"><span data-stu-id="990a8-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>

 <span data-ttu-id="990a8-104">Normalmente, quando você invoca um tipo genérico, você fornece um argumento de tipo para cada parâmetro de tipo que o tipo genérico define.</span><span class="sxs-lookup"><span data-stu-id="990a8-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="990a8-105">Se você não fornecer nenhum argumento de tipo, o compilador tentará inferir os tipos a serem passados para os parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="990a8-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="990a8-106">Se o contexto não fornecer informações suficientes para que o compilador inferir os tipos, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="990a8-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>

 <span data-ttu-id="990a8-107">**ID do erro:** BC36564</span><span class="sxs-lookup"><span data-stu-id="990a8-107">**Error ID:** BC36564</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="990a8-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="990a8-108">To correct this error</span></span>

- <span data-ttu-id="990a8-109">Especifique os argumentos de tipo para o procedimento genérico na `AddressOf` expressão.</span><span class="sxs-lookup"><span data-stu-id="990a8-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>

## <a name="see-also"></a><span data-ttu-id="990a8-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="990a8-110">See also</span></span>

- [<span data-ttu-id="990a8-111">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="990a8-111">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="990a8-112">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="990a8-112">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="990a8-113">Procedimentos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="990a8-113">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="990a8-114">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="990a8-114">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="990a8-115">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="990a8-115">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
