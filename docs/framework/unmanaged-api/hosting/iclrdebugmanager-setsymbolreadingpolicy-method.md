---
title: Método ICLRDebugManager::SetSymbolReadingPolicy
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetSymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ee21861ed3911303d4661721b65e9e147c6953a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="c9d02-102">Método ICLRDebugManager::SetSymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="c9d02-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="c9d02-103">Define a política para a leitura de arquivos do programa (PDB) de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c9d02-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="c9d02-104">A política determina se as informações sobre números de linha e de arquivos estão incluídas em pilhas de chamadas.</span><span class="sxs-lookup"><span data-stu-id="c9d02-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9d02-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9d02-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9d02-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9d02-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="c9d02-107">[in] Membro de [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="c9d02-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9d02-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c9d02-108">Return Value</span></span>  
  
|<span data-ttu-id="c9d02-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9d02-109">HRESULT</span></span>|<span data-ttu-id="c9d02-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9d02-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9d02-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9d02-111">S_OK</span></span>|<span data-ttu-id="c9d02-112">`SetSymbolReadingPolicy` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="c9d02-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="c9d02-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c9d02-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c9d02-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c9d02-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c9d02-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c9d02-115">E_FAIL</span></span>|<span data-ttu-id="c9d02-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c9d02-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c9d02-117">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="c9d02-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c9d02-118">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c9d02-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9d02-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9d02-119">Requirements</span></span>  
 <span data-ttu-id="c9d02-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9d02-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9d02-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c9d02-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9d02-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c9d02-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9d02-123">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9d02-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d02-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9d02-124">See Also</span></span>  
 [<span data-ttu-id="c9d02-125">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="c9d02-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
