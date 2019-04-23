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
ms.openlocfilehash: 2dc3d350f5c97736b3b65c814a668195aceef2b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132815"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="9080c-102">Método ICLRDebugManager::SetSymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="9080c-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="9080c-103">Define a política para a leitura de arquivos de banco de dados (PDB) do programa.</span><span class="sxs-lookup"><span data-stu-id="9080c-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="9080c-104">A política determina se a opção informações sobre arquivos e números de linha estão incluídas em pilhas de chamadas.</span><span class="sxs-lookup"><span data-stu-id="9080c-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9080c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9080c-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9080c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9080c-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="9080c-107">[in] Um membro do [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="9080c-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9080c-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9080c-108">Return Value</span></span>  
  
|<span data-ttu-id="9080c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9080c-109">HRESULT</span></span>|<span data-ttu-id="9080c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="9080c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9080c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9080c-111">S_OK</span></span>|<span data-ttu-id="9080c-112">`SetSymbolReadingPolicy` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9080c-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="9080c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9080c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9080c-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9080c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9080c-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9080c-115">E_FAIL</span></span>|<span data-ttu-id="9080c-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9080c-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9080c-117">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="9080c-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9080c-118">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9080c-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9080c-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9080c-119">Requirements</span></span>  
 <span data-ttu-id="9080c-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9080c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9080c-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9080c-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9080c-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9080c-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9080c-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9080c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9080c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9080c-124">See also</span></span>

- [<span data-ttu-id="9080c-125">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="9080c-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
