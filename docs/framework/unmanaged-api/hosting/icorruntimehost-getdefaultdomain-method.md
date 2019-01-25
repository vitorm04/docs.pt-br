---
title: Método ICorRuntimeHost::GetDefaultDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d301ace3ed99ff8e15ed6ab80781fd8c7f83aaec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743485"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="5cf06-102">Método ICorRuntimeHost::GetDefaultDomain</span><span class="sxs-lookup"><span data-stu-id="5cf06-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="5cf06-103">Obtém um ponteiro de interface do tipo <xref:System._AppDomain?displayProperty=nameWithType> que representa o domínio padrão para o processo atual.</span><span class="sxs-lookup"><span data-stu-id="5cf06-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cf06-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5cf06-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5cf06-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5cf06-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5cf06-106">[out] Um ponteiro de interface do tipo <xref:System._AppDomain?displayProperty=nameWithType> para o <xref:System.AppDomain> instância que representa o domínio de aplicativo padrão para o processo.</span><span class="sxs-lookup"><span data-stu-id="5cf06-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="5cf06-107">Esse ponteiro é digitado `IUnknown`, de modo que os chamadores devem chamar geralmente `QueryInterface` para obter um ponteiro de interface do tipo <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5cf06-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cf06-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5cf06-108">Return Value</span></span>  
  
|<span data-ttu-id="5cf06-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5cf06-109">HRESULT</span></span>|<span data-ttu-id="5cf06-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5cf06-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5cf06-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5cf06-111">S_OK</span></span>|<span data-ttu-id="5cf06-112">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="5cf06-112">The operation was successful.</span></span>|  
|<span data-ttu-id="5cf06-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5cf06-113">S_FALSE</span></span>|<span data-ttu-id="5cf06-114">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="5cf06-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="5cf06-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5cf06-115">E_FAIL</span></span>|<span data-ttu-id="5cf06-116">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="5cf06-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="5cf06-117">Se um método retornar E_FAIL, o common language runtime (CLR) não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="5cf06-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="5cf06-118">As chamadas subsequentes para todas as APIs de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5cf06-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5cf06-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5cf06-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5cf06-120">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5cf06-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5cf06-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5cf06-121">Requirements</span></span>  
 <span data-ttu-id="5cf06-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cf06-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cf06-123">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5cf06-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5cf06-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5cf06-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5cf06-125">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="5cf06-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf06-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5cf06-126">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="5cf06-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="5cf06-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
