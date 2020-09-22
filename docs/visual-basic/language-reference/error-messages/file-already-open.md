---
title: Arquivo já aberto
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 97f9e13e6802e793f7c7baf1f03ec51205eb6d42
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874170"
---
# <a name="file-already-open"></a><span data-ttu-id="1e3eb-102">Arquivo já aberto</span><span class="sxs-lookup"><span data-stu-id="1e3eb-102">File already open</span></span>

<span data-ttu-id="1e3eb-103">Às vezes, um arquivo deve ser fechado antes que outra `FileOpen` ou outra operação possa ocorrer.</span><span class="sxs-lookup"><span data-stu-id="1e3eb-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="1e3eb-104">Entre as possíveis causas desse erro estão:</span><span class="sxs-lookup"><span data-stu-id="1e3eb-104">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="1e3eb-105">Uma operação de modo de saída sequencial `FileOpen` foi executada para um arquivo que já está aberto</span><span class="sxs-lookup"><span data-stu-id="1e3eb-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
- <span data-ttu-id="1e3eb-106">Uma instrução refere-se a um arquivo aberto.</span><span class="sxs-lookup"><span data-stu-id="1e3eb-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1e3eb-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1e3eb-107">To correct this error</span></span>  
  
1. <span data-ttu-id="1e3eb-108">Feche o arquivo antes de executar a instrução.</span><span class="sxs-lookup"><span data-stu-id="1e3eb-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e3eb-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="1e3eb-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
