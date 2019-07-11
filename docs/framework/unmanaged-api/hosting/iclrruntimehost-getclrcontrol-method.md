---
title: Método ICLRRuntimeHost::GetCLRControl
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b697e2cf7688767ac58c6bd2a3f18d781ab439b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768748"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="e875e-102">Método ICLRRuntimeHost::GetCLRControl</span><span class="sxs-lookup"><span data-stu-id="e875e-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="e875e-103">Obtém um ponteiro de interface do tipo [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) que os hosts podem usar para personalizar os aspectos do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e875e-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e875e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e875e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e875e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e875e-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="e875e-106">[out] Um ponteiro de interface do tipo [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) que permite que os hosts configurar aspectos adicionais do CLR.</span><span class="sxs-lookup"><span data-stu-id="e875e-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e875e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e875e-107">Return Value</span></span>  
  
|<span data-ttu-id="e875e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e875e-108">HRESULT</span></span>|<span data-ttu-id="e875e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e875e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e875e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e875e-110">S_OK</span></span>|<span data-ttu-id="e875e-111">`GetCLRControl` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e875e-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="e875e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e875e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e875e-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e875e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e875e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e875e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e875e-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e875e-115">The call timed out.</span></span>|  
|<span data-ttu-id="e875e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e875e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e875e-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e875e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e875e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e875e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e875e-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="e875e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e875e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e875e-120">E_FAIL</span></span>|<span data-ttu-id="e875e-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e875e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e875e-122">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e875e-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e875e-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e875e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e875e-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="e875e-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="e875e-125">O CLR já foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="e875e-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e875e-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="e875e-126">Remarks</span></span>  
 <span data-ttu-id="e875e-127">`ICLRControl` fornece o [método GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) método, que permite que o host obter um ponteiro de interface para um dos tipos de Gerenciador.</span><span class="sxs-lookup"><span data-stu-id="e875e-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e875e-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e875e-128">Requirements</span></span>  
 <span data-ttu-id="e875e-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e875e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e875e-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e875e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e875e-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e875e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e875e-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e875e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e875e-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e875e-133">See also</span></span>

- [<span data-ttu-id="e875e-134">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="e875e-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="e875e-135">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e875e-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
