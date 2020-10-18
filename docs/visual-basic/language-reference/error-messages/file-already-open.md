---
title: Arquivo já aberto
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: ce8f8bf96d7355e45b2df82e8a131472c2ed2367
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162746"
---
# <a name="file-already-open"></a><span data-ttu-id="cb016-102">Arquivo já aberto</span><span class="sxs-lookup"><span data-stu-id="cb016-102">File already open</span></span>

<span data-ttu-id="cb016-103">Às vezes, um arquivo deve ser fechado antes que outra `FileOpen` ou outra operação possa ocorrer.</span><span class="sxs-lookup"><span data-stu-id="cb016-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="cb016-104">Entre as possíveis causas desse erro estão:</span><span class="sxs-lookup"><span data-stu-id="cb016-104">Among the possible causes of this error are:</span></span>

- <span data-ttu-id="cb016-105">Uma operação de modo de saída sequencial `FileOpen` foi executada para um arquivo que já está aberto</span><span class="sxs-lookup"><span data-stu-id="cb016-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>

- <span data-ttu-id="cb016-106">Uma instrução refere-se a um arquivo aberto.</span><span class="sxs-lookup"><span data-stu-id="cb016-106">A statement refers to an open file.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="cb016-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="cb016-107">To correct this error</span></span>

- <span data-ttu-id="cb016-108">Feche o arquivo antes de executar a instrução.</span><span class="sxs-lookup"><span data-stu-id="cb016-108">Close the file before executing the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb016-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="cb016-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
