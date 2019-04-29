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
ms.openlocfilehash: 1e6805dc67f7ec5ceb8c67d77462a0200b6c0317
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641418"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="bbe80-102">Método ICLRRuntimeHost::ExecuteInDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="bbe80-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="bbe80-103">Chama o método especificado do tipo especificado no assembly gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="bbe80-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbe80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbe80-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbe80-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bbe80-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="bbe80-106">[in] O caminho para o <xref:System.Reflection.Assembly> que define o <xref:System.Type> cujo método é invocado.</span><span class="sxs-lookup"><span data-stu-id="bbe80-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="bbe80-107">[in] O nome da <xref:System.Type> que define o método a ser invocado.</span><span class="sxs-lookup"><span data-stu-id="bbe80-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="bbe80-108">[in] O nome do método a ser invocado.</span><span class="sxs-lookup"><span data-stu-id="bbe80-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="bbe80-109">[in] O parâmetro de cadeia de caracteres para passar para o método.</span><span class="sxs-lookup"><span data-stu-id="bbe80-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="bbe80-110">[out] O valor inteiro retornado pelo método invocado.</span><span class="sxs-lookup"><span data-stu-id="bbe80-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbe80-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bbe80-111">Return Value</span></span>  
  
|<span data-ttu-id="bbe80-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bbe80-112">HRESULT</span></span>|<span data-ttu-id="bbe80-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="bbe80-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbe80-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="bbe80-114">S_OK</span></span>|<span data-ttu-id="bbe80-115">`ExecuteInDefaultAppDomain` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="bbe80-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="bbe80-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bbe80-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bbe80-117">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="bbe80-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bbe80-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bbe80-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bbe80-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="bbe80-119">The call timed out.</span></span>|  
|<span data-ttu-id="bbe80-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bbe80-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bbe80-121">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="bbe80-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bbe80-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bbe80-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bbe80-123">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="bbe80-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bbe80-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bbe80-124">E_FAIL</span></span>|<span data-ttu-id="bbe80-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="bbe80-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bbe80-126">Se um método retornar E_FAIL, a CRL não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="bbe80-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="bbe80-127">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bbe80-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbe80-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="bbe80-128">Remarks</span></span>  
 <span data-ttu-id="bbe80-129">O método invocado deve ter a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="bbe80-129">The invoked method must have the following signature:</span></span>  
  
```  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="bbe80-130">em que `pwzMethodName` representa o nome do método invocado, e `pwzArgument` representa o valor de cadeia de caracteres passado como um parâmetro ao método.</span><span class="sxs-lookup"><span data-stu-id="bbe80-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="bbe80-131">Se o valor HRESULT é definido como S_OK, `pReturnValue` é definido como o valor inteiro retornado pelo método invocado.</span><span class="sxs-lookup"><span data-stu-id="bbe80-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="bbe80-132">Caso contrário, `pReturnValue` não está definido.</span><span class="sxs-lookup"><span data-stu-id="bbe80-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbe80-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bbe80-133">Requirements</span></span>  
 <span data-ttu-id="bbe80-134">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbe80-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbe80-135">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bbe80-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bbe80-136">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bbe80-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbe80-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbe80-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe80-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbe80-138">See also</span></span>

- [<span data-ttu-id="bbe80-139">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="bbe80-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
