---
title: Não foi possível inferir argumentos de tipo a partir do delegado
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 57a3a24af32d9eb85a0f905aa3a73a956723b6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="72758-102">Não foi possível inferir argumentos de tipo a partir do delegado</span><span class="sxs-lookup"><span data-stu-id="72758-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="72758-103">Usa uma instrução de atribuição `AddressOf` para atribuir o endereço de um generic procedimento como um delegado, mas não fornece nenhum argumento de tipo para o procedimento genérico.</span><span class="sxs-lookup"><span data-stu-id="72758-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="72758-104">Normalmente, quando você invoca um tipo genérico, você fornece um argumento de tipo para cada parâmetro de tipo que define o tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="72758-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="72758-105">Se você não fornecer nenhum argumento de tipo, o compilador tenta inferir os tipos a serem passados para os parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="72758-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="72758-106">Se o contexto não fornece informações suficientes para o compilador inferir os tipos, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="72758-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="72758-107">**ID do erro:** BC36564</span><span class="sxs-lookup"><span data-stu-id="72758-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="72758-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="72758-108">To correct this error</span></span>  
  
-   <span data-ttu-id="72758-109">Especificar os argumentos de tipo para o procedimento genérico de `AddressOf` expressão.</span><span class="sxs-lookup"><span data-stu-id="72758-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72758-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72758-110">See Also</span></span>  
 [<span data-ttu-id="72758-111">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72758-111">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="72758-112">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="72758-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="72758-113">Procedimentos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72758-113">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [<span data-ttu-id="72758-114">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="72758-114">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="72758-115">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="72758-115">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
