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
ms.openlocfilehash: 478e07f18d40043de4e800c36647ac4a32499635
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120427"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="6d20b-102">Método ICLRRuntimeHost::GetCLRControl</span><span class="sxs-lookup"><span data-stu-id="6d20b-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="6d20b-103">Obtém um ponteiro de interface do tipo [interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) que os hosts podem usar para personalizar aspectos do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6d20b-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d20b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d20b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d20b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6d20b-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="6d20b-106">fora Um ponteiro de interface do tipo [interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) que permite que os hosts configurem aspectos adicionais do CLR.</span><span class="sxs-lookup"><span data-stu-id="6d20b-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d20b-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6d20b-107">Return Value</span></span>  
  
|<span data-ttu-id="6d20b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d20b-108">HRESULT</span></span>|<span data-ttu-id="6d20b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d20b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d20b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d20b-110">S_OK</span></span>|<span data-ttu-id="6d20b-111">`GetCLRControl` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="6d20b-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="6d20b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6d20b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6d20b-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="6d20b-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6d20b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6d20b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6d20b-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="6d20b-115">The call timed out.</span></span>|  
|<span data-ttu-id="6d20b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6d20b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6d20b-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="6d20b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6d20b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6d20b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6d20b-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="6d20b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6d20b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6d20b-120">E_FAIL</span></span>|<span data-ttu-id="6d20b-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="6d20b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6d20b-122">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="6d20b-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6d20b-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6d20b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6d20b-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="6d20b-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="6d20b-125">O CLR já foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="6d20b-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d20b-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d20b-126">Remarks</span></span>  
 <span data-ttu-id="6d20b-127">`ICLRControl` fornece o método de [método GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) , que permite que o host obtenha um ponteiro de interface para um dos tipos de gerente.</span><span class="sxs-lookup"><span data-stu-id="6d20b-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d20b-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d20b-128">Requirements</span></span>  
 <span data-ttu-id="6d20b-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d20b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d20b-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6d20b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d20b-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6d20b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d20b-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d20b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d20b-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d20b-133">See also</span></span>

- [<span data-ttu-id="6d20b-134">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="6d20b-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="6d20b-135">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6d20b-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
