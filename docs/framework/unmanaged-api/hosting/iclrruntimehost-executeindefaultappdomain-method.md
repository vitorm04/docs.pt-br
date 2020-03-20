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
ms.openlocfilehash: 1a1bc7609042422de876fe167a9e61655aaf62b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176403"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="841a1-102">Método ICLRRuntimeHost::ExecuteInDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="841a1-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="841a1-103">Chama o método especificado do tipo especificado no conjunto gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="841a1-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="841a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="841a1-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="841a1-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="841a1-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="841a1-106">[em] O caminho <xref:System.Reflection.Assembly> para o <xref:System.Type> que define o cujo método deve ser invocado.</span><span class="sxs-lookup"><span data-stu-id="841a1-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="841a1-107">[em] O nome <xref:System.Type> do que define o método para invocar.</span><span class="sxs-lookup"><span data-stu-id="841a1-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="841a1-108">[em] O nome do método para invocar.</span><span class="sxs-lookup"><span data-stu-id="841a1-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="841a1-109">[em] O parâmetro de seqüência para passar para o método.</span><span class="sxs-lookup"><span data-stu-id="841a1-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="841a1-110">[fora] O valor inteiro devolvido pelo método invocado.</span><span class="sxs-lookup"><span data-stu-id="841a1-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="841a1-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="841a1-111">Return Value</span></span>  
  
|<span data-ttu-id="841a1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="841a1-112">HRESULT</span></span>|<span data-ttu-id="841a1-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="841a1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="841a1-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="841a1-114">S_OK</span></span>|<span data-ttu-id="841a1-115">`ExecuteInDefaultAppDomain`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="841a1-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="841a1-116">Host_e_clrnotavailable</span><span class="sxs-lookup"><span data-stu-id="841a1-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="841a1-117">O tempo de execução do idioma comum (CLR) não foi carregado em um processo, ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="841a1-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="841a1-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="841a1-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="841a1-119">A chamada acabou.</span><span class="sxs-lookup"><span data-stu-id="841a1-119">The call timed out.</span></span>|  
|<span data-ttu-id="841a1-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="841a1-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="841a1-121">O interlocutor não é dono da fechadura.</span><span class="sxs-lookup"><span data-stu-id="841a1-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="841a1-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="841a1-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="841a1-123">Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="841a1-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="841a1-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="841a1-124">E_FAIL</span></span>|<span data-ttu-id="841a1-125">Uma falha catastrófica desconhecida ocorreu.</span><span class="sxs-lookup"><span data-stu-id="841a1-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="841a1-126">Se um método retornar E_FAIL, o CRL não poderá mais ser utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="841a1-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="841a1-127">Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="841a1-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="841a1-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="841a1-128">Remarks</span></span>  
 <span data-ttu-id="841a1-129">O método invocado deve ter a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="841a1-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="841a1-130">onde `pwzMethodName` representa o nome do método `pwzArgument` invocado, e representa o valor da corda passado como parâmetro para esse método.</span><span class="sxs-lookup"><span data-stu-id="841a1-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="841a1-131">Se o valor HRESULT for `pReturnValue` definido como S_OK, será definido como valor inteiro retornado pelo método invocado.</span><span class="sxs-lookup"><span data-stu-id="841a1-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="841a1-132">Caso contrário, `pReturnValue` não está definido.</span><span class="sxs-lookup"><span data-stu-id="841a1-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="841a1-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="841a1-133">Requirements</span></span>  
 <span data-ttu-id="841a1-134">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="841a1-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="841a1-135">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="841a1-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="841a1-136">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="841a1-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="841a1-137">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="841a1-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="841a1-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="841a1-138">See also</span></span>

- [<span data-ttu-id="841a1-139">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="841a1-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
