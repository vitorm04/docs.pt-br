---
title: Comprimento de registro inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 1bc75303bcc2f46e54c06e89347da28997e59786
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979727"
---
# <a name="bad-record-length"></a><span data-ttu-id="1c434-102">Comprimento de registro inválido</span><span class="sxs-lookup"><span data-stu-id="1c434-102">Bad record length</span></span>
<span data-ttu-id="1c434-103">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="1c434-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="1c434-104">O comprimento de uma variável do registro especificado em uma `FileGet`, `FileGetObject`, `FilePut` ou `FilePutObject` instrução é diferente do que o comprimento especificado no correspondente `FileOpen` instrução.</span><span class="sxs-lookup"><span data-stu-id="1c434-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
-   <span data-ttu-id="1c434-105">A variável em uma `FilePut` ou `FilePutObject` instrução é ou inclui uma cadeia de caracteres de comprimento variável.</span><span class="sxs-lookup"><span data-stu-id="1c434-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
-   <span data-ttu-id="1c434-106">A variável em uma `FilePut` ou `FilePutObject` é ou inclui um `Variant` tipo.</span><span class="sxs-lookup"><span data-stu-id="1c434-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1c434-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1c434-107">To correct this error</span></span>  
  
1. <span data-ttu-id="1c434-108">Verifique se a soma dos tamanhos das variáveis de comprimento fixo no tipo definido pelo usuário definindo o tipo de registro da variável é o mesmo que o valor indicado na `FileOpen` da instrução `Len` cláusula.</span><span class="sxs-lookup"><span data-stu-id="1c434-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2. <span data-ttu-id="1c434-109">Se a variável em uma `FilePut` ou `FilePutObject` instrução é ou inclui uma cadeia de caracteres de comprimento variável, verifique se a cadeia de caracteres de comprimento variável é pelo menos 2 caracteres menor do que o comprimento do registro especificado na `Len` cláusula do `FileOpen` instrução.</span><span class="sxs-lookup"><span data-stu-id="1c434-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3. <span data-ttu-id="1c434-110">Se a variável em uma `FilePut` ou `FilePutObject` é ou inclui uma `Variant` Verifique se a cadeia de caracteres de comprimento variável é menor do que o comprimento do registro especificado em pelo menos 4 bytes a `Len` cláusula do `FileOpen` instrução.</span><span class="sxs-lookup"><span data-stu-id="1c434-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c434-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c434-111">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
