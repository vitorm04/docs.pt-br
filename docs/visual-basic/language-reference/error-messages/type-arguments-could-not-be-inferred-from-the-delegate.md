---
title: "Não foi possível inferir argumentos de tipo do delegado | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36564
- vbc36564
dev_langs:
- VB
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ffff5f47f7d765b726c5fe40ccbe9fcedbbf8652
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="f418e-102">Não foi possível inferir argumentos de tipo a partir do delegado</span><span class="sxs-lookup"><span data-stu-id="f418e-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="f418e-103">Uma instrução de atribuição usa `AddressOf` para atribuir o endereço de um genérico procedimento para um delegado, mas não fornece nenhum argumento de tipo para o procedimento genérico.</span><span class="sxs-lookup"><span data-stu-id="f418e-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="f418e-104">Normalmente, quando você invoca um tipo genérico, você fornece um argumento de tipo para cada parâmetro de tipo que define o tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="f418e-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="f418e-105">Se você não fornecer nenhum argumento de tipo, o compilador tenta inferir os tipos a serem passados para os parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="f418e-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="f418e-106">Se o contexto não fornece informação suficiente para o compilador inferir os tipos, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="f418e-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="f418e-107">**ID do erro:** BC36564</span><span class="sxs-lookup"><span data-stu-id="f418e-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f418e-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f418e-108">To correct this error</span></span>  
  
-   <span data-ttu-id="f418e-109">Especificar os argumentos de tipo para o procedimento genérico de `AddressOf` expressão.</span><span class="sxs-lookup"><span data-stu-id="f418e-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f418e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f418e-110">See Also</span></span>  
 <span data-ttu-id="f418e-111">[Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="f418e-111">[Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="f418e-112"> [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="f418e-112"> [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="f418e-113"> [Procedimentos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="f418e-113"> [Generic Procedures in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) </span></span>  
<span data-ttu-id="f418e-114"> [Lista de tipos](../../../visual-basic/language-reference/statements/type-list.md) </span><span class="sxs-lookup"><span data-stu-id="f418e-114"> [Type List](../../../visual-basic/language-reference/statements/type-list.md) </span></span>  
<span data-ttu-id="f418e-115"> [Métodos de Extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span><span class="sxs-lookup"><span data-stu-id="f418e-115"> [Extension Methods](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span></span>
