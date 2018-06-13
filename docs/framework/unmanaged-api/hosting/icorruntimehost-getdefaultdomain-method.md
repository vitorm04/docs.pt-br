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
ms.openlocfilehash: f2351fbb26a38f408d330db3f7600120bd57d6e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437876"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="82ab5-102">Método ICorRuntimeHost::GetDefaultDomain</span><span class="sxs-lookup"><span data-stu-id="82ab5-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="82ab5-103">Obtém um ponteiro de interface do tipo <xref:System._AppDomain?displayProperty=nameWithType> que representa o domínio padrão para o processo atual.</span><span class="sxs-lookup"><span data-stu-id="82ab5-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82ab5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82ab5-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82ab5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82ab5-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="82ab5-106">[out] Um ponteiro de interface do tipo <xref:System._AppDomain?displayProperty=nameWithType> para a <xref:System.AppDomain> instância que representa o domínio de aplicativo padrão para o processo.</span><span class="sxs-lookup"><span data-stu-id="82ab5-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="82ab5-107">Esse ponteiro é digitado `IUnknown`, de modo que os chamadores devem chamar geralmente `QueryInterface` para obter um ponteiro de interface do tipo <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="82ab5-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82ab5-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="82ab5-108">Return Value</span></span>  
  
|<span data-ttu-id="82ab5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="82ab5-109">HRESULT</span></span>|<span data-ttu-id="82ab5-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="82ab5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82ab5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="82ab5-111">S_OK</span></span>|<span data-ttu-id="82ab5-112">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="82ab5-112">The operation was successful.</span></span>|  
|<span data-ttu-id="82ab5-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="82ab5-113">S_FALSE</span></span>|<span data-ttu-id="82ab5-114">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="82ab5-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="82ab5-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="82ab5-115">E_FAIL</span></span>|<span data-ttu-id="82ab5-116">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="82ab5-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="82ab5-117">Se um método retornará E_FAIL, o common language runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="82ab5-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="82ab5-118">As chamadas subsequentes para hospedagem de APIs retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="82ab5-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="82ab5-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="82ab5-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="82ab5-120">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="82ab5-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="82ab5-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82ab5-121">Requirements</span></span>  
 <span data-ttu-id="82ab5-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82ab5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82ab5-123">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="82ab5-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82ab5-124">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="82ab5-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82ab5-125">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="82ab5-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ab5-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82ab5-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="82ab5-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="82ab5-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
