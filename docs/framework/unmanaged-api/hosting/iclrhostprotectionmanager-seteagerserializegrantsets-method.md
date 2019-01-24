---
title: Método ICLRHostProtectionManager::SetEagerSerializeGrantSets
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 948fd78ae2839bd24a44c8c0b806e32b1da7125f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729766"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="8de50-102">Método ICLRHostProtectionManager::SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="8de50-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="8de50-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="8de50-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8de50-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8de50-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8de50-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8de50-105">Return Value</span></span>  
  
|<span data-ttu-id="8de50-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8de50-106">HRESULT</span></span>|<span data-ttu-id="8de50-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8de50-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8de50-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8de50-108">S_OK</span></span>|<span data-ttu-id="8de50-109">`SetEagerSerializeGrantSets` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8de50-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="8de50-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8de50-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8de50-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8de50-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8de50-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8de50-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8de50-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8de50-113">The call timed out.</span></span>|  
|<span data-ttu-id="8de50-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8de50-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8de50-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8de50-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8de50-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8de50-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8de50-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="8de50-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8de50-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8de50-118">E_FAIL</span></span>|<span data-ttu-id="8de50-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8de50-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8de50-120">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="8de50-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8de50-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8de50-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8de50-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8de50-122">Requirements</span></span>  
 <span data-ttu-id="8de50-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8de50-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8de50-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8de50-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8de50-125">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8de50-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8de50-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8de50-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de50-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8de50-127">See also</span></span>
- [<span data-ttu-id="8de50-128">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="8de50-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="8de50-129">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="8de50-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
