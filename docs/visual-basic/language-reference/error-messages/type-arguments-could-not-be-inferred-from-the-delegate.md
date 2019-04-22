---
title: Não foi possível inferir argumentos de tipo a partir do delegado
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 1024cf6f2c1fa112db29cb710eef190a5022d3af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838593"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="95a4b-102">Não foi possível inferir argumentos de tipo a partir do delegado</span><span class="sxs-lookup"><span data-stu-id="95a4b-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="95a4b-103">Usa uma instrução de atribuição `AddressOf` para atribuir o endereço de um genérico o procedimento para um delegado, mas ele não fornece quaisquer argumentos de tipo para o procedimento genérico.</span><span class="sxs-lookup"><span data-stu-id="95a4b-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="95a4b-104">Normalmente, quando você invoca um tipo genérico, você fornece um argumento de tipo para cada parâmetro de tipo que define o tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="95a4b-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="95a4b-105">Se você não fornecer nenhum argumento de tipo, o compilador tentará inferir os tipos a serem passados para os parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="95a4b-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="95a4b-106">Se o contexto não fornece informações suficientes para que o compilador inferir os tipos, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="95a4b-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="95a4b-107">**ID do erro:** BC36564</span><span class="sxs-lookup"><span data-stu-id="95a4b-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="95a4b-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="95a4b-108">To correct this error</span></span>  
  
-   <span data-ttu-id="95a4b-109">Especifica os argumentos de tipo para o procedimento genérico no `AddressOf` expressão.</span><span class="sxs-lookup"><span data-stu-id="95a4b-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a4b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95a4b-110">See also</span></span>

- [<span data-ttu-id="95a4b-111">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="95a4b-111">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="95a4b-112">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="95a4b-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="95a4b-113">Procedimentos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="95a4b-113">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="95a4b-114">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="95a4b-114">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="95a4b-115">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="95a4b-115">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
