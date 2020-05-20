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
ms.openlocfilehash: 7fa02c4c79da118543117aada7d1b9cca09c4cae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703406"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="9c000-102">Método ICLRPolicyManager::SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="9c000-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="9c000-103">Especifica o comportamento do Common Language Runtime (CLR) quando ocorre uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="9c000-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c000-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c000-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c000-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9c000-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="9c000-106">no Um dos valores de [EClrUnhandledException](eclrunhandledexception-enumeration.md) , indicando se o comportamento é definido pelo CLR ou pelo host.</span><span class="sxs-lookup"><span data-stu-id="9c000-106">[in] One of the [EClrUnhandledException](eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c000-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9c000-107">Return Value</span></span>  
  
|<span data-ttu-id="9c000-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c000-108">HRESULT</span></span>|<span data-ttu-id="9c000-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c000-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c000-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c000-110">S_OK</span></span>|<span data-ttu-id="9c000-111">`SetUnhandledExceptionPolicy`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9c000-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="9c000-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9c000-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9c000-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9c000-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9c000-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9c000-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9c000-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="9c000-115">The call timed out.</span></span>|  
|<span data-ttu-id="9c000-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9c000-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9c000-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9c000-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9c000-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9c000-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9c000-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="9c000-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9c000-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9c000-120">E_FAIL</span></span>|<span data-ttu-id="9c000-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9c000-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9c000-122">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="9c000-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9c000-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9c000-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c000-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c000-124">Remarks</span></span>  
 <span data-ttu-id="9c000-125">Por padrão, o CLR é o manipulador final para todas as exceções sem tratamento e seu comportamento padrão é subdividir o processo.</span><span class="sxs-lookup"><span data-stu-id="9c000-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="9c000-126">O host pode alterar esse comportamento definindo o `policy` valor como eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="9c000-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="9c000-127">Esse valor permite que o host implemente seu próprio comportamento padrão, como nas versões anteriores do CLR.</span><span class="sxs-lookup"><span data-stu-id="9c000-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c000-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9c000-128">Requirements</span></span>  
 <span data-ttu-id="9c000-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c000-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c000-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9c000-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c000-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9c000-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c000-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c000-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c000-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="9c000-133">See also</span></span>

- [<span data-ttu-id="9c000-134">Enumeração EClrUnhandledException</span><span class="sxs-lookup"><span data-stu-id="9c000-134">EClrUnhandledException Enumeration</span></span>](eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="9c000-135">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="9c000-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="9c000-136">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="9c000-136">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="9c000-137">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="9c000-137">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
