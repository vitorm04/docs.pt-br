---
title: Função CoUninitializeEE
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
ms.openlocfilehash: fa6297e926d53c02bb0d1af7b59b45b8ee152399
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616457"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="3ed34-102">Função CoUninitializeEE</span><span class="sxs-lookup"><span data-stu-id="3ed34-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="3ed34-103">`CoUninitializeEE`é obsoleto e não fornece nenhuma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="3ed34-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ed34-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ed34-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="3ed34-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="3ed34-105">Remarks</span></span>  
 <span data-ttu-id="3ed34-106">O mecanismo de execução de Common Language Runtime não pode ser descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="3ed34-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="3ed34-107">Para desligar a chamada do mecanismo de execução [CorExitProcess](corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="3ed34-107">To shut down the execution engine call [CorExitProcess](corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed34-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="3ed34-108">See also</span></span>

- [<span data-ttu-id="3ed34-109">Função CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="3ed34-109">CoInitializeEE Function</span></span>](coinitializeee-function.md)
- [<span data-ttu-id="3ed34-110">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="3ed34-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
