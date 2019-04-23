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
ms.openlocfilehash: 9f988084310b920907bb7f212e7d40ca0d1c91db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197510"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="a29c6-102">Método ICLRPolicyManager::SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="a29c6-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="a29c6-103">Especifica o comportamento do common language runtime (CLR) quando ocorre uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="a29c6-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a29c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a29c6-104">Syntax</span></span>  
  
```  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a29c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a29c6-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="a29c6-106">[in] Um dos [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) valores, que indica se o comportamento é definido por CLR ou o host.</span><span class="sxs-lookup"><span data-stu-id="a29c6-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a29c6-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a29c6-107">Return Value</span></span>  
  
|<span data-ttu-id="a29c6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a29c6-108">HRESULT</span></span>|<span data-ttu-id="a29c6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a29c6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a29c6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a29c6-110">S_OK</span></span>|<span data-ttu-id="a29c6-111">`SetUnhandledExceptionPolicy` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a29c6-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="a29c6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a29c6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a29c6-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a29c6-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a29c6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a29c6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a29c6-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="a29c6-115">The call timed out.</span></span>|  
|<span data-ttu-id="a29c6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a29c6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a29c6-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a29c6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a29c6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a29c6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a29c6-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="a29c6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a29c6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a29c6-120">E_FAIL</span></span>|<span data-ttu-id="a29c6-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a29c6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a29c6-122">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="a29c6-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a29c6-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a29c6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a29c6-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="a29c6-124">Remarks</span></span>  
 <span data-ttu-id="a29c6-125">Por padrão, o CLR é o manipulador de final de todas as exceções sem tratamento e seu comportamento padrão é subdividir o processo.</span><span class="sxs-lookup"><span data-stu-id="a29c6-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="a29c6-126">O host pode alterar esse comportamento, definindo o `policy` valor a eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="a29c6-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="a29c6-127">Esse valor permite que o host implementar seu próprio comportamento padrão, como nas versões anteriores do CLR.</span><span class="sxs-lookup"><span data-stu-id="a29c6-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a29c6-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a29c6-128">Requirements</span></span>  
 <span data-ttu-id="a29c6-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a29c6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a29c6-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a29c6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a29c6-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a29c6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a29c6-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a29c6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a29c6-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a29c6-133">See also</span></span>

- [<span data-ttu-id="a29c6-134">Enumeração EClrUnhandledException</span><span class="sxs-lookup"><span data-stu-id="a29c6-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="a29c6-135">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="a29c6-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="a29c6-136">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="a29c6-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="a29c6-137">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="a29c6-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
