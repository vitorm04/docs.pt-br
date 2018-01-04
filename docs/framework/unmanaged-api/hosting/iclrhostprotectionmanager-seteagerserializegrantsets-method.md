---
title: "Método ICLRHostProtectionManager::SetEagerSerializeGrantSets"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1d2bb2ecc4ae7edb4edbaa3ff36650c70c82daf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="9288b-102">Método ICLRHostProtectionManager::SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="9288b-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="9288b-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="9288b-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9288b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9288b-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9288b-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9288b-105">Return Value</span></span>  
  
|<span data-ttu-id="9288b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9288b-106">HRESULT</span></span>|<span data-ttu-id="9288b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9288b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9288b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9288b-108">S_OK</span></span>|<span data-ttu-id="9288b-109">`SetEagerSerializeGrantSets`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="9288b-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="9288b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9288b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9288b-111">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9288b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9288b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9288b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9288b-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="9288b-113">The call timed out.</span></span>|  
|<span data-ttu-id="9288b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9288b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9288b-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9288b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9288b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9288b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9288b-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="9288b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9288b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9288b-118">E_FAIL</span></span>|<span data-ttu-id="9288b-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9288b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9288b-120">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="9288b-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9288b-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9288b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9288b-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9288b-122">Requirements</span></span>  
 <span data-ttu-id="9288b-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9288b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9288b-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9288b-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9288b-125">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9288b-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9288b-126">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9288b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9288b-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9288b-127">See Also</span></span>  
 [<span data-ttu-id="9288b-128">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="9288b-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="9288b-129">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="9288b-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
