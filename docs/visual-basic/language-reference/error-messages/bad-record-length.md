---
title: "Comprimento de registro inválido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID59
dev_langs:
- VB
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
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
ms.openlocfilehash: 38386bba72072a1400dde9a593e1735c920afd49
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="bad-record-length"></a><span data-ttu-id="e577c-102">Comprimento de registro inválido</span><span class="sxs-lookup"><span data-stu-id="e577c-102">Bad record length</span></span>
<span data-ttu-id="e577c-103">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="e577c-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="e577c-104">O comprimento de uma variável do Registro especificada em uma `FileGet`, `FileGetObject`, `FilePut` ou `FilePutObject` instrução difere do comprimento especificado na correspondentes `FileOpen` instrução.</span><span class="sxs-lookup"><span data-stu-id="e577c-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
-   <span data-ttu-id="e577c-105">A variável em uma `FilePut` ou `FilePutObject` instrução é ou inclui uma cadeia de caracteres de comprimento variável.</span><span class="sxs-lookup"><span data-stu-id="e577c-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
-   <span data-ttu-id="e577c-106">A variável em uma `FilePut` ou `FilePutObject` é ou inclui um `Variant`tipo**.**</span><span class="sxs-lookup"><span data-stu-id="e577c-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant`type**.**</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e577c-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e577c-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="e577c-108">Verifique se a soma dos tamanhos das variáveis de comprimento fixo no tipo definido pelo usuário definindo o tipo de registro da variável é o mesmo que o valor indicado no `FileOpen` da instrução `Len` cláusula.</span><span class="sxs-lookup"><span data-stu-id="e577c-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2.  <span data-ttu-id="e577c-109">Se a variável em uma `FilePut` ou `FilePutObject` instrução é ou inclui uma cadeia de caracteres de comprimento variável, verifique se a cadeia de caracteres de comprimento variável é pelo menos 2 caracteres menor do que o comprimento do registro especificado no `Len` cláusula do `FileOpen` instrução.</span><span class="sxs-lookup"><span data-stu-id="e577c-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3.  <span data-ttu-id="e577c-110">Se a variável em uma `FilePut` ou `FilePutObject` é ou inclui um `Variant` certificar-se de que a cadeia de caracteres de comprimento variável é ao menos 4 bytes menor do que o comprimento do registro especificado no `Len` cláusula do `FileOpen` instrução.</span><span class="sxs-lookup"><span data-stu-id="e577c-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e577c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e577c-111">See Also</span></span>  
 <span data-ttu-id="e577c-112"><xref:Microsoft.VisualBasic.FileSystem.FileGet%2A></xref:Microsoft.VisualBasic.FileSystem.FileGet%2A></span><span class="sxs-lookup"><span data-stu-id="e577c-112"><xref:Microsoft.VisualBasic.FileSystem.FileGet%2A></span></span>   
 <span data-ttu-id="e577c-113"><xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A></xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A></span><span class="sxs-lookup"><span data-stu-id="e577c-113"><xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A></span></span>   
 <span data-ttu-id="e577c-114"><xref:Microsoft.VisualBasic.FileSystem.FilePut%2A></xref:Microsoft.VisualBasic.FileSystem.FilePut%2A></span><span class="sxs-lookup"><span data-stu-id="e577c-114"><xref:Microsoft.VisualBasic.FileSystem.FilePut%2A></span></span>   
 <span data-ttu-id="e577c-115"><xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A></xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A></span><span class="sxs-lookup"><span data-stu-id="e577c-115"><xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A></span></span>
