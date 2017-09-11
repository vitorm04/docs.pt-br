---
title: "&quot;&lt;typename&gt;&quot; é um tipo delegado | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
dev_langs:
- VB
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
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
ms.openlocfilehash: 55532e269a7d6756157d324a2db14320df5d3f55
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="39f21-102">'&lt;typename&gt;' é um tipo delegate</span><span class="sxs-lookup"><span data-stu-id="39f21-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="39f21-103">'\<typename >' é um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="39f21-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="39f21-104">A construção Delegate permite somente uma única expressão AddressOf como uma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="39f21-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="39f21-105">Geralmente, uma expressão AddressOf pode ser usada em vez de uma construção delegate.</span><span class="sxs-lookup"><span data-stu-id="39f21-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="39f21-106">Um `New` cláusula criando uma instância de uma classe delegate fornece uma lista de argumentos inválido para o construtor delegado.</span><span class="sxs-lookup"><span data-stu-id="39f21-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="39f21-107">Você pode fornecer um único `AddressOf` expressão ao criar uma nova instância do delegado.</span><span class="sxs-lookup"><span data-stu-id="39f21-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="39f21-108">Esse erro pode resultar se você não passar argumentos ao construtor delegado, se você passar mais de um argumento, ou se você passar um argumento único que não é válido `AddressOf` expressão.</span><span class="sxs-lookup"><span data-stu-id="39f21-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="39f21-109">**ID do erro:** BC32008</span><span class="sxs-lookup"><span data-stu-id="39f21-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="39f21-110">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="39f21-110">To correct this error</span></span>  
  
-   <span data-ttu-id="39f21-111">Usar um único `AddressOf` expressão na lista de argumentos para a classe delegate de `New` cláusula.</span><span class="sxs-lookup"><span data-stu-id="39f21-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f21-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39f21-112">See Also</span></span>  
 <span data-ttu-id="39f21-113">[Novo operador](../../../visual-basic/language-reference/operators/new-operator.md) </span><span class="sxs-lookup"><span data-stu-id="39f21-113">[New Operator](../../../visual-basic/language-reference/operators/new-operator.md) </span></span>  
<span data-ttu-id="39f21-114"> [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="39f21-114"> [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="39f21-115"> [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="39f21-115"> [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="39f21-116"> [Como invocar um método delegado](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)</span><span class="sxs-lookup"><span data-stu-id="39f21-116"> [How to: Invoke a Delegate Method](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)</span></span>
