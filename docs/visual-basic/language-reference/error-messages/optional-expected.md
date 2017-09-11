---
title: '&quot;Optional&quot; esperado | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30202
- vbc30202
dev_langs:
- VB
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
caps.latest.revision: 9
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
ms.openlocfilehash: 6debad770cdcdade32ec7ea683c708a812545707
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39optional39-expected"></a><span data-ttu-id="2dd96-102">'Optional' esperado</span><span class="sxs-lookup"><span data-stu-id="2dd96-102">&#39;Optional&#39; expected</span></span>
<span data-ttu-id="2dd96-103">Um argumento opcional na declaração de procedimento é seguido por um argumento necessário.</span><span class="sxs-lookup"><span data-stu-id="2dd96-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="2dd96-104">Cada argumento após um argumento opcional também deve ser opcional.</span><span class="sxs-lookup"><span data-stu-id="2dd96-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="2dd96-105">**ID do erro:** BC30202</span><span class="sxs-lookup"><span data-stu-id="2dd96-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2dd96-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2dd96-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="2dd96-107">Se o argumento destina-se a ser necessários, movê-la para preceder o primeiro argumento opcional na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="2dd96-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="2dd96-108">Se o argumento destina-se a ser opcional, use o `Optional` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="2dd96-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd96-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2dd96-109">See Also</span></span>  
 [<span data-ttu-id="2dd96-110">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="2dd96-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
