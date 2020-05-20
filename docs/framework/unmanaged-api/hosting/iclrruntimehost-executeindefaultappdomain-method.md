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
ms.openlocfilehash: 070c52258b66dcc352f2beef81b9a0694b8301ce
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703281"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="e4c31-102">Método ICLRRuntimeHost::ExecuteInDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="e4c31-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="e4c31-103">Chama o método especificado do tipo especificado no assembly gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="e4c31-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4c31-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4c31-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4c31-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4c31-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="e4c31-106">no O caminho para o <xref:System.Reflection.Assembly> que define o <xref:System.Type> cujo método deve ser invocado.</span><span class="sxs-lookup"><span data-stu-id="e4c31-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="e4c31-107">no O nome do <xref:System.Type> que define o método a ser invocado.</span><span class="sxs-lookup"><span data-stu-id="e4c31-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="e4c31-108">no O nome do método a ser invocado.</span><span class="sxs-lookup"><span data-stu-id="e4c31-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="e4c31-109">no O parâmetro de cadeia de caracteres a ser passado para o método.</span><span class="sxs-lookup"><span data-stu-id="e4c31-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="e4c31-110">fora O valor inteiro retornado pelo método invocado.</span><span class="sxs-lookup"><span data-stu-id="e4c31-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4c31-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e4c31-111">Return Value</span></span>  
  
|<span data-ttu-id="e4c31-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4c31-112">HRESULT</span></span>|<span data-ttu-id="e4c31-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4c31-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4c31-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4c31-114">S_OK</span></span>|<span data-ttu-id="e4c31-115">`ExecuteInDefaultAppDomain`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e4c31-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="e4c31-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e4c31-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e4c31-117">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e4c31-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e4c31-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e4c31-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e4c31-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e4c31-119">The call timed out.</span></span>|  
|<span data-ttu-id="e4c31-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e4c31-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e4c31-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e4c31-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e4c31-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e4c31-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e4c31-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="e4c31-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e4c31-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e4c31-124">E_FAIL</span></span>|<span data-ttu-id="e4c31-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e4c31-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e4c31-126">Se um método retornar E_FAIL, a CRL não poderá mais ser usada no processo.</span><span class="sxs-lookup"><span data-stu-id="e4c31-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="e4c31-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e4c31-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4c31-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4c31-128">Remarks</span></span>  
 <span data-ttu-id="e4c31-129">O método invocado deve ter a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="e4c31-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="e4c31-130">onde `pwzMethodName` representa o nome do método invocado e `pwzArgument` representa o valor da cadeia de caracteres passado como um parâmetro para esse método.</span><span class="sxs-lookup"><span data-stu-id="e4c31-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="e4c31-131">Se o valor HRESULT for definido como S_OK, `pReturnValue` será definido como o valor inteiro retornado pelo método invocado.</span><span class="sxs-lookup"><span data-stu-id="e4c31-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="e4c31-132">Caso contrário, `pReturnValue` não será definido.</span><span class="sxs-lookup"><span data-stu-id="e4c31-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4c31-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4c31-133">Requirements</span></span>  
 <span data-ttu-id="e4c31-134">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4c31-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4c31-135">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e4c31-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4c31-136">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e4c31-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4c31-137">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4c31-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c31-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="e4c31-138">See also</span></span>

- [<span data-ttu-id="e4c31-139">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e4c31-139">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
