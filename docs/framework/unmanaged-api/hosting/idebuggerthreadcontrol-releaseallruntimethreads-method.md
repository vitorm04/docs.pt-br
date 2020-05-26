---
title: Método IDebuggerThreadControl::ReleaseAllRuntimeThreads
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
ms.openlocfilehash: 50ffb33456f942a71089f9bc44daa07f6b77ab21
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805294"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="631cf-102">Método IDebuggerThreadControl::ReleaseAllRuntimeThreads</span><span class="sxs-lookup"><span data-stu-id="631cf-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="631cf-103">Notifica o host de que os serviços de depuração estão prestes a liberar todos os threads bloqueados.</span><span class="sxs-lookup"><span data-stu-id="631cf-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="631cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="631cf-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="631cf-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="631cf-105">Remarks</span></span>  
 <span data-ttu-id="631cf-106">O `ReleaseAllRuntimeThreads` método nunca será chamado em um thread de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="631cf-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="631cf-107">Se o host tiver um thread de tempo de execução bloqueado, ele deverá liberá-lo agora.</span><span class="sxs-lookup"><span data-stu-id="631cf-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="631cf-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="631cf-108">Requirements</span></span>  
 <span data-ttu-id="631cf-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="631cf-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="631cf-110">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="631cf-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="631cf-111">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="631cf-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="631cf-112">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="631cf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="631cf-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="631cf-113">See also</span></span>

- [<span data-ttu-id="631cf-114">Interface IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="631cf-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
