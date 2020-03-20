---
title: Método ICLRRuntimeHost::ExecuteInAppDomain
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
ms.openlocfilehash: c012e4e2b5e41737f7bbe6a0fb887693b0ba22c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176416"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="b31de-102">Método ICLRRuntimeHost::ExecuteInAppDomain</span><span class="sxs-lookup"><span data-stu-id="b31de-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="b31de-103">Especifica o <xref:System.AppDomain> em que executar o código gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="b31de-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b31de-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b31de-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b31de-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="b31de-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="b31de-106">[em] O ID numérico do <xref:System.AppDomain> em que executar o método especificado.</span><span class="sxs-lookup"><span data-stu-id="b31de-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="b31de-107">[em] Um ponteiro para a função para <xref:System.AppDomain>executar dentro do especificado .</span><span class="sxs-lookup"><span data-stu-id="b31de-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="b31de-108">[em] Um ponteiro para memória opaca alocada por chamadores.</span><span class="sxs-lookup"><span data-stu-id="b31de-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="b31de-109">Esse parâmetro é passado pelo tempo de execução do idioma comum (CLR) para o retorno de chamada de domínio.</span><span class="sxs-lookup"><span data-stu-id="b31de-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="b31de-110">Não é memória de pilha gerenciada por tempo de execução; tanto a alocação quanto a vida útil desta memória são controladas pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="b31de-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b31de-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b31de-111">Return Value</span></span>  
  
|<span data-ttu-id="b31de-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b31de-112">HRESULT</span></span>|<span data-ttu-id="b31de-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b31de-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b31de-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b31de-114">S_OK</span></span>|<span data-ttu-id="b31de-115">`ExecuteInAppDomain`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="b31de-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="b31de-116">Host_e_clrnotavailable</span><span class="sxs-lookup"><span data-stu-id="b31de-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b31de-117">A CLR não foi carregada em um processo, ou a CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="b31de-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b31de-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b31de-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b31de-119">A chamada acabou.</span><span class="sxs-lookup"><span data-stu-id="b31de-119">The call timed out.</span></span>|  
|<span data-ttu-id="b31de-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b31de-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b31de-121">O interlocutor não é dono da fechadura.</span><span class="sxs-lookup"><span data-stu-id="b31de-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b31de-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b31de-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b31de-123">Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="b31de-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b31de-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b31de-124">E_FAIL</span></span>|<span data-ttu-id="b31de-125">Uma falha catastrófica desconhecida ocorreu.</span><span class="sxs-lookup"><span data-stu-id="b31de-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b31de-126">Se um método retornar E_FAIL, a CLR não poderá mais ser utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b31de-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b31de-127">Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b31de-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b31de-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="b31de-128">Remarks</span></span>  
 <span data-ttu-id="b31de-129">`ExecuteInAppDomain`permite que o host exercite o controle sobre <xref:System.AppDomain> o qual o método gerenciado especificado deve ser executado.</span><span class="sxs-lookup"><span data-stu-id="b31de-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="b31de-130">Você pode obter o valor do identificador de um domínio de <xref:System.AppDomain.Id%2A> aplicativo, que corresponde ao valor da propriedade, chamando-o de [Método GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="b31de-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b31de-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b31de-131">Requirements</span></span>  
 <span data-ttu-id="b31de-132">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b31de-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b31de-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b31de-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b31de-134">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b31de-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b31de-135">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b31de-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b31de-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="b31de-136">See also</span></span>

- [<span data-ttu-id="b31de-137">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="b31de-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
