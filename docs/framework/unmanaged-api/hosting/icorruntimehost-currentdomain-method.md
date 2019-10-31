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
ms.openlocfilehash: f2249d10159b1ff0be7ead0783efb8a2742d26b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139610"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="4ebc5-102">Método ICorRuntimeHost::CurrentDomain</span><span class="sxs-lookup"><span data-stu-id="4ebc5-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="4ebc5-103">Obtém um ponteiro de interface do tipo <xref:System.AppDomain?displayProperty=nameWithType> que representa o domínio carregado no thread atual.</span><span class="sxs-lookup"><span data-stu-id="4ebc5-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ebc5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ebc5-104">Syntax</span></span>  
  
```cpp  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ebc5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4ebc5-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="4ebc5-106">fora Um ponteiro do tipo <xref:System.AppDomain?displayProperty=nameWithType> que representa o domínio do aplicativo atual do thread.</span><span class="sxs-lookup"><span data-stu-id="4ebc5-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="4ebc5-107">Esse ponteiro é digitado `IUnknown`, de modo que os chamadores geralmente devem chamar `QueryInterface` para obter um ponteiro do tipo <xref:System._AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="4ebc5-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ebc5-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="4ebc5-108">Return Value</span></span>  
  
|<span data-ttu-id="4ebc5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ebc5-109">HRESULT</span></span>|<span data-ttu-id="4ebc5-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="4ebc5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ebc5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ebc5-111">S_OK</span></span>|<span data-ttu-id="4ebc5-112">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="4ebc5-112">The operation was successful.</span></span>|  
|<span data-ttu-id="4ebc5-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4ebc5-113">S_FALSE</span></span>|<span data-ttu-id="4ebc5-114">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="4ebc5-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="4ebc5-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4ebc5-115">E_FAIL</span></span>|<span data-ttu-id="4ebc5-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="4ebc5-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="4ebc5-117">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="4ebc5-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="4ebc5-118">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4ebc5-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4ebc5-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4ebc5-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4ebc5-120">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="4ebc5-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ebc5-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4ebc5-121">Requirements</span></span>  
 <span data-ttu-id="4ebc5-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ebc5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ebc5-123">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4ebc5-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ebc5-124">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4ebc5-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ebc5-125">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="4ebc5-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ebc5-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ebc5-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="4ebc5-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="4ebc5-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
