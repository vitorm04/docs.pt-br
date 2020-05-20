---
title: Função CoUninitializeCor
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
ms.openlocfilehash: 8a8c2764398d737192190f91646d45f4edf3a0e4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616472"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="fcb82-102">Função CoUninitializeCor</span><span class="sxs-lookup"><span data-stu-id="fcb82-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="fcb82-103">`CoUninitializeCor` é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="fcb82-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcb82-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fcb82-104">Syntax</span></span>  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="fcb82-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="fcb82-105">Remarks</span></span>  
 <span data-ttu-id="fcb82-106">O Common Language Runtime não pode ser descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="fcb82-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="fcb82-107">Para remover completamente o tempo de execução de um processo em execução, você deve desligar esse processo.</span><span class="sxs-lookup"><span data-stu-id="fcb82-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcb82-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="fcb82-108">See also</span></span>

- [<span data-ttu-id="fcb82-109">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="fcb82-109">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
