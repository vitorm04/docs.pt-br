---
title: "Ordinal não é válido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID452
dev_langs:
- VB
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: 8
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
ms.openlocfilehash: 700c52046d30a283ac5f2684ba698eff3284f036
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="ac8a7-102">O ordinal não é válido</span><span class="sxs-lookup"><span data-stu-id="ac8a7-102">Ordinal is not valid</span></span>
<span data-ttu-id="ac8a7-103">Sua chamada para uma biblioteca de vínculo dinâmico (DLL) indicada usa um número em vez de um nome de procedimento, usando o `#num` sintaxe.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="ac8a7-104">Este erro possui as seguintes causas possíveis:</span><span class="sxs-lookup"><span data-stu-id="ac8a7-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="ac8a7-105">Uma tentativa de converter o `#num` expressão a um ordinal falhou.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="ac8a7-106">O `#num` especificado não especifica qualquer função na DLL.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="ac8a7-107">Uma biblioteca de tipos tem uma declaração inválida resultando em uso interno do número ordinal inválido.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ac8a7-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ac8a7-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="ac8a7-109">Verifique se que a expressão representa um número válido, ou chame o procedimento por nome.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2.  <span data-ttu-id="ac8a7-110">Certifique-se de `#num` identifica uma função válida no DLL.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3.  <span data-ttu-id="ac8a7-111">Isole a chamada de procedimento causando o problema comentando o código.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="ac8a7-112">Escrever um `Declare` declaração de procedimento e relatar o problema para o fornecedor da biblioteca de tipo.</span><span class="sxs-lookup"><span data-stu-id="ac8a7-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac8a7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac8a7-113">See Also</span></span>  
 [<span data-ttu-id="ac8a7-114">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="ac8a7-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
