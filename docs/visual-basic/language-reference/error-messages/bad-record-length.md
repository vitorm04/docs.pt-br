---
title: Comprimento de registro inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 6967015572b2567f52697f7ddcb1ff594013a2c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869256"
---
# <a name="bad-record-length"></a><span data-ttu-id="a5802-102">Comprimento de registro inválido</span><span class="sxs-lookup"><span data-stu-id="a5802-102">Bad record length</span></span>

<span data-ttu-id="a5802-103">Entre as possíveis causas desse erro estão:</span><span class="sxs-lookup"><span data-stu-id="a5802-103">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="a5802-104">O comprimento de uma variável de registro especificada em `FileGet` uma `FileGetObject` `FilePut` instrução, ou `FilePutObject` difere do comprimento especificado na `FileOpen` instrução correspondente.</span><span class="sxs-lookup"><span data-stu-id="a5802-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
- <span data-ttu-id="a5802-105">A variável em uma `FilePut` `FilePutObject` instrução or é ou inclui uma cadeia de caracteres de comprimento variável.</span><span class="sxs-lookup"><span data-stu-id="a5802-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
- <span data-ttu-id="a5802-106">A variável em um `FilePut` ou `FilePutObject` é ou inclui um `Variant` tipo.</span><span class="sxs-lookup"><span data-stu-id="a5802-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a5802-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a5802-107">To correct this error</span></span>  
  
1. <span data-ttu-id="a5802-108">Verifique se a soma dos tamanhos das variáveis de comprimento fixo no tipo definido pelo usuário definindo o tipo da variável de registro é igual ao valor indicado na `FileOpen` cláusula da instrução `Len` .</span><span class="sxs-lookup"><span data-stu-id="a5802-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2. <span data-ttu-id="a5802-109">Se a variável em uma `FilePut` `FilePutObject` instrução or for ou incluir uma cadeia de caracteres de comprimento variável, certifique-se de que a cadeia de caracteres de comprimento variável tenha pelo menos 2 caracteres mais curto do que o tamanho do registro especificado na `Len` cláusula da `FileOpen` instrução.</span><span class="sxs-lookup"><span data-stu-id="a5802-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3. <span data-ttu-id="a5802-110">Se a variável em um `FilePut` ou `FilePutObject` for ou incluir uma `Variant` , verifique se a cadeia de caracteres de comprimento variável tem pelo menos 4 bytes de comprimento menor do que o tamanho do registro especificado na `Len` cláusula da `FileOpen` instrução.</span><span class="sxs-lookup"><span data-stu-id="a5802-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5802-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="a5802-111">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
