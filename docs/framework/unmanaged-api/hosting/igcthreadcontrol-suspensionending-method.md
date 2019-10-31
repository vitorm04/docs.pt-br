---
title: Método IGCThreadControl::SuspensionEnding
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
ms.openlocfilehash: 8d8efccde56d8d37a75b1d9bbec706411c6b1f45
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134792"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="c2a75-102">Método IGCThreadControl::SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="c2a75-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="c2a75-103">Notifica o host de que o tempo de execução está retomando threads após uma coleta de lixo ou outra suspensão.</span><span class="sxs-lookup"><span data-stu-id="c2a75-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2a75-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2a75-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2a75-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2a75-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="c2a75-106">no A geração na qual uma coleta de lixo foi executada.</span><span class="sxs-lookup"><span data-stu-id="c2a75-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2a75-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2a75-107">Remarks</span></span>  
 <span data-ttu-id="c2a75-108">Não reagende nenhum thread durante o retorno de chamada `SuspensionEnding`.</span><span class="sxs-lookup"><span data-stu-id="c2a75-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2a75-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2a75-109">Requirements</span></span>  
 <span data-ttu-id="c2a75-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2a75-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2a75-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c2a75-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2a75-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c2a75-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2a75-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2a75-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2a75-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2a75-114">See also</span></span>

- [<span data-ttu-id="c2a75-115">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="c2a75-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
