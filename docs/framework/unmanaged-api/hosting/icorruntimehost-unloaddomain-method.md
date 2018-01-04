---
title: "Método ICorRuntimeHost::UnloadDomain"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.UnloadDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 067b60b9da02300e9e7316712d0058a61ab8a697
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="71937-102">Método ICorRuntimeHost::UnloadDomain</span><span class="sxs-lookup"><span data-stu-id="71937-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="71937-103">Descarrega o domínio de aplicativo especificado do processo atual.</span><span class="sxs-lookup"><span data-stu-id="71937-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71937-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71937-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71937-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="71937-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="71937-106">[in] Um ponteiro de tipo <xref:System._AppDomain?displayProperty=nameWithType> que representa o domínio a ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="71937-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71937-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="71937-107">Return Value</span></span>  
  
|<span data-ttu-id="71937-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71937-108">HRESULT</span></span>|<span data-ttu-id="71937-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="71937-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71937-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="71937-110">S_OK</span></span>|<span data-ttu-id="71937-111">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="71937-111">The operation was successful.</span></span>|  
|<span data-ttu-id="71937-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="71937-112">S_FALSE</span></span>|<span data-ttu-id="71937-113">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="71937-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="71937-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71937-114">E_FAIL</span></span>|<span data-ttu-id="71937-115">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="71937-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="71937-116">Se um método retornará E_FAIL, o common language runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="71937-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="71937-117">As chamadas subsequentes para hospedagem de APIs retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="71937-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="71937-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="71937-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="71937-119">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="71937-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71937-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71937-120">Requirements</span></span>  
 <span data-ttu-id="71937-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71937-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71937-122">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="71937-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71937-123">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="71937-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71937-124">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="71937-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71937-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71937-125">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="71937-126">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="71937-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
