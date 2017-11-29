---
title: "Método ICLRDebugManager::SetSymbolReadingPolicy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.SetSymbolReadingPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d116883c39b4400451ede07df83ac77893ce285c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="cad87-102">Método ICLRDebugManager::SetSymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="cad87-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="cad87-103">Define a política para a leitura de arquivos do programa (PDB) de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="cad87-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="cad87-104">A política determina se as informações sobre números de linha e de arquivos estão incluídas em pilhas de chamadas.</span><span class="sxs-lookup"><span data-stu-id="cad87-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cad87-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cad87-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cad87-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cad87-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="cad87-107">[in] Membro de [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="cad87-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cad87-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cad87-108">Return Value</span></span>  
  
|<span data-ttu-id="cad87-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cad87-109">HRESULT</span></span>|<span data-ttu-id="cad87-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="cad87-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cad87-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cad87-111">S_OK</span></span>|<span data-ttu-id="cad87-112">`SetSymbolReadingPolicy`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="cad87-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="cad87-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cad87-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cad87-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="cad87-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cad87-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cad87-115">E_FAIL</span></span>|<span data-ttu-id="cad87-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="cad87-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cad87-117">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="cad87-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cad87-118">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cad87-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cad87-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cad87-119">Requirements</span></span>  
 <span data-ttu-id="cad87-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cad87-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cad87-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cad87-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cad87-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cad87-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cad87-123">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cad87-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cad87-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cad87-124">See Also</span></span>  
 [<span data-ttu-id="cad87-125">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="cad87-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
