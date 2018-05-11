---
title: Método ICLRRuntimeHost::ExecuteInDefaultAppDomain
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dcddb5766894a30f1ccb2552a09abe7153c6eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="2d721-102">Método ICLRRuntimeHost::ExecuteInDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="2d721-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="2d721-103">Chama o método especificado do tipo especificado no assembly gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="2d721-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d721-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d721-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d721-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2d721-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="2d721-106">[in] O caminho para o <xref:System.Reflection.Assembly> que define o <xref:System.Type> cujo método é invocado.</span><span class="sxs-lookup"><span data-stu-id="2d721-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="2d721-107">[in] O nome do <xref:System.Type> que define o método a ser invocado.</span><span class="sxs-lookup"><span data-stu-id="2d721-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="2d721-108">[in] O nome do método a ser invocado.</span><span class="sxs-lookup"><span data-stu-id="2d721-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="2d721-109">[in] O parâmetro de cadeia de caracteres para passar para o método.</span><span class="sxs-lookup"><span data-stu-id="2d721-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="2d721-110">[out] O valor de inteiro retornado pelo método invocado.</span><span class="sxs-lookup"><span data-stu-id="2d721-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d721-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2d721-111">Return Value</span></span>  
  
|<span data-ttu-id="2d721-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d721-112">HRESULT</span></span>|<span data-ttu-id="2d721-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d721-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d721-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d721-114">S_OK</span></span>|<span data-ttu-id="2d721-115">`ExecuteInDefaultAppDomain` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="2d721-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="2d721-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d721-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d721-117">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="2d721-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d721-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d721-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d721-119">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="2d721-119">The call timed out.</span></span>|  
|<span data-ttu-id="2d721-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d721-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d721-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2d721-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d721-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d721-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d721-123">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="2d721-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d721-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d721-124">E_FAIL</span></span>|<span data-ttu-id="2d721-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="2d721-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d721-126">Se um método retornará E_FAIL, a CRL não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="2d721-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="2d721-127">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2d721-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d721-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d721-128">Remarks</span></span>  
 <span data-ttu-id="2d721-129">O método invocado deve ter a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="2d721-129">The invoked method must have the following signature:</span></span>  
  
```  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="2d721-130">onde `pwzMethodName` representa o nome do método invocado, e `pwzArgument` representa o valor de cadeia de caracteres passado como um parâmetro para esse método.</span><span class="sxs-lookup"><span data-stu-id="2d721-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="2d721-131">Se o valor HRESULT é definido como S_OK, `pReturnValue` é definido como o valor inteiro retornado pelo método invocado.</span><span class="sxs-lookup"><span data-stu-id="2d721-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="2d721-132">Caso contrário, `pReturnValue` não está definido.</span><span class="sxs-lookup"><span data-stu-id="2d721-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d721-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d721-133">Requirements</span></span>  
 <span data-ttu-id="2d721-134">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d721-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d721-135">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d721-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d721-136">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2d721-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d721-137">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d721-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d721-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d721-138">See Also</span></span>  
 [<span data-ttu-id="2d721-139">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="2d721-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
