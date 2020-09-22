---
title: Entrada passou do final do arquivo
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: c0cb0373fb0652e9600ac8651661708414561aca
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873960"
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="59278-102">Entrada passou do final do arquivo</span><span class="sxs-lookup"><span data-stu-id="59278-102">Input past end of file</span></span>

<span data-ttu-id="59278-103">Uma `Input` instrução está lendo um arquivo vazio ou um em que todos os dados são usados, ou você usou a `EOF` função com um arquivo aberto para acesso binário.</span><span class="sxs-lookup"><span data-stu-id="59278-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="59278-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="59278-104">To correct this error</span></span>  
  
1. <span data-ttu-id="59278-105">Use a `EOF` função imediatamente antes da `Input` instrução para detectar o final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="59278-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2. <span data-ttu-id="59278-106">Se o arquivo for aberto para acesso binário, use `Seek` e `Loc` .</span><span class="sxs-lookup"><span data-stu-id="59278-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59278-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="59278-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
