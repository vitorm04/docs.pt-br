---
title: Método IHostTaskManager::SetLocale
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f388a52c320c3f0d5f4ad7e073e1e8960d7947dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749370"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="bde80-102">Método IHostTaskManager::SetLocale</span><span class="sxs-lookup"><span data-stu-id="bde80-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="bde80-103">Notifica o host que o common language runtime (CLR) foi alterado de uma localidade ou cultura, a tarefa em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="bde80-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bde80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bde80-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bde80-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bde80-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="bde80-106">[in] O valor do identificador de localidade que é mapeado para a cultura geográfica recentemente atribuída e o idioma.</span><span class="sxs-lookup"><span data-stu-id="bde80-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bde80-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bde80-107">Return Value</span></span>  
  
|<span data-ttu-id="bde80-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bde80-108">HRESULT</span></span>|<span data-ttu-id="bde80-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bde80-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bde80-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bde80-110">S_OK</span></span>|<span data-ttu-id="bde80-111">`SetLocale` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="bde80-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="bde80-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bde80-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bde80-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="bde80-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bde80-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bde80-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bde80-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="bde80-115">The call timed out.</span></span>|  
|<span data-ttu-id="bde80-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bde80-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bde80-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="bde80-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bde80-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bde80-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bde80-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="bde80-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bde80-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bde80-120">E_FAIL</span></span>|<span data-ttu-id="bde80-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="bde80-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bde80-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="bde80-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bde80-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bde80-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bde80-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="bde80-124">E_NOTIMPL</span></span>|<span data-ttu-id="bde80-125">O host não permite código de usuário gerenciado para modificar a localidade.</span><span class="sxs-lookup"><span data-stu-id="bde80-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bde80-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="bde80-126">Remarks</span></span>  
 <span data-ttu-id="bde80-127">A tempo de execução chama `SetLocale` quando o valor da <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> propriedade é alterada pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bde80-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="bde80-128">Esse método fornece uma oportunidade para o host executar os mecanismos que ele pode ter para a sincronização de localidades.</span><span class="sxs-lookup"><span data-stu-id="bde80-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="bde80-129">Se um host não permite que a localidade a ser alterado a partir do código gerenciado ou não implementa um mecanismo para sincronizar as localidades, ele deverá retornar E_NOTIMPL deste método.</span><span class="sxs-lookup"><span data-stu-id="bde80-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bde80-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bde80-130">Requirements</span></span>  
 <span data-ttu-id="bde80-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bde80-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bde80-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bde80-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bde80-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bde80-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bde80-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bde80-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bde80-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bde80-135">See also</span></span>

- [<span data-ttu-id="bde80-136">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="bde80-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="bde80-137">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="bde80-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="bde80-138">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="bde80-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="bde80-139">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="bde80-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="bde80-140">Método SetUILocale</span><span class="sxs-lookup"><span data-stu-id="bde80-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
