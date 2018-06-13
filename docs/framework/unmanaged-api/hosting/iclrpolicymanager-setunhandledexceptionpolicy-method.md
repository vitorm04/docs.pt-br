---
title: Método ICLRPolicyManager::SetUnhandledExceptionPolicy
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6a3d5bb8a8cc5acc88373fa4952848d08ccd485
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434910"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="20b6a-102">Método ICLRPolicyManager::SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="20b6a-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="20b6a-103">Especifica o comportamento do common language runtime (CLR) quando ocorre uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="20b6a-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20b6a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20b6a-104">Syntax</span></span>  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20b6a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="20b6a-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="20b6a-106">[in] Uma da [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) valores, que indica se o comportamento é definido pelo CLR ou no host.</span><span class="sxs-lookup"><span data-stu-id="20b6a-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20b6a-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="20b6a-107">Return Value</span></span>  
  
|<span data-ttu-id="20b6a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20b6a-108">HRESULT</span></span>|<span data-ttu-id="20b6a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="20b6a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20b6a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="20b6a-110">S_OK</span></span>|<span data-ttu-id="20b6a-111">`SetUnhandledExceptionPolicy` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="20b6a-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="20b6a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="20b6a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="20b6a-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="20b6a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="20b6a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="20b6a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="20b6a-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="20b6a-115">The call timed out.</span></span>|  
|<span data-ttu-id="20b6a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="20b6a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="20b6a-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="20b6a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="20b6a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="20b6a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="20b6a-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="20b6a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="20b6a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20b6a-120">E_FAIL</span></span>|<span data-ttu-id="20b6a-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="20b6a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="20b6a-122">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="20b6a-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="20b6a-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="20b6a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20b6a-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="20b6a-124">Remarks</span></span>  
 <span data-ttu-id="20b6a-125">Por padrão, o CLR é o manipulador final de todas as exceções sem tratamento e seu comportamento padrão é subdividir o processo.</span><span class="sxs-lookup"><span data-stu-id="20b6a-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="20b6a-126">O host pode alterar esse comportamento, definindo a `policy` valor eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="20b6a-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="20b6a-127">Esse valor permite que o host implementar seu próprio comportamento padrão, como nas versões anteriores do CLR.</span><span class="sxs-lookup"><span data-stu-id="20b6a-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20b6a-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20b6a-128">Requirements</span></span>  
 <span data-ttu-id="20b6a-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20b6a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20b6a-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="20b6a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20b6a-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="20b6a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20b6a-132">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20b6a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20b6a-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20b6a-133">See Also</span></span>  
 [<span data-ttu-id="20b6a-134">Enumeração EClrUnhandledException</span><span class="sxs-lookup"><span data-stu-id="20b6a-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)  
 [<span data-ttu-id="20b6a-135">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="20b6a-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="20b6a-136">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="20b6a-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="20b6a-137">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="20b6a-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
