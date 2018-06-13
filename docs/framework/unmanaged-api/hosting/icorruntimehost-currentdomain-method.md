---
title: Método ICorRuntimeHost::CurrentDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CurrentDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96cda3f504910d8fb70905f66b45f417158c505d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436839"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="d2eae-102">Método ICorRuntimeHost::CurrentDomain</span><span class="sxs-lookup"><span data-stu-id="d2eae-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="d2eae-103">Obtém um ponteiro de interface do tipo <xref:System.AppDomain?displayProperty=nameWithType> que representa o domínio carregado no thread atual.</span><span class="sxs-lookup"><span data-stu-id="d2eae-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2eae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2eae-104">Syntax</span></span>  
  
```  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2eae-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2eae-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d2eae-106">[out] Um ponteiro de tipo <xref:System.AppDomain?displayProperty=nameWithType> que representa o domínio de aplicativo atual do thread.</span><span class="sxs-lookup"><span data-stu-id="d2eae-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="d2eae-107">Esse ponteiro é digitado `IUnknown`, de modo que os chamadores devem chamar geralmente `QueryInterface` para obter um ponteiro de tipo <xref:System._AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="d2eae-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2eae-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d2eae-108">Return Value</span></span>  
  
|<span data-ttu-id="d2eae-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2eae-109">HRESULT</span></span>|<span data-ttu-id="d2eae-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2eae-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2eae-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2eae-111">S_OK</span></span>|<span data-ttu-id="d2eae-112">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d2eae-112">The operation was successful.</span></span>|  
|<span data-ttu-id="d2eae-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d2eae-113">S_FALSE</span></span>|<span data-ttu-id="d2eae-114">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="d2eae-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="d2eae-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d2eae-115">E_FAIL</span></span>|<span data-ttu-id="d2eae-116">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d2eae-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="d2eae-117">Se um método retornará E_FAIL, o common language runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="d2eae-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="d2eae-118">As chamadas subsequentes para hospedagem de APIs retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d2eae-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d2eae-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d2eae-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d2eae-120">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d2eae-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2eae-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2eae-121">Requirements</span></span>  
 <span data-ttu-id="d2eae-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2eae-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2eae-123">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d2eae-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2eae-124">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d2eae-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2eae-125">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="d2eae-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2eae-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2eae-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="d2eae-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="d2eae-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
