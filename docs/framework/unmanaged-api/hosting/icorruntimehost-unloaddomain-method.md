---
title: Método ICorRuntimeHost::UnloadDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4db96133315b23a2d0b4bd32b597ee03f5d697b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438110"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="7c91e-102">Método ICorRuntimeHost::UnloadDomain</span><span class="sxs-lookup"><span data-stu-id="7c91e-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="7c91e-103">Descarrega o domínio de aplicativo especificado do processo atual.</span><span class="sxs-lookup"><span data-stu-id="7c91e-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c91e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c91e-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c91e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7c91e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7c91e-106">[in] Um ponteiro de tipo <xref:System._AppDomain?displayProperty=nameWithType> que representa o domínio a ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="7c91e-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c91e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7c91e-107">Return Value</span></span>  
  
|<span data-ttu-id="7c91e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c91e-108">HRESULT</span></span>|<span data-ttu-id="7c91e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c91e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c91e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c91e-110">S_OK</span></span>|<span data-ttu-id="7c91e-111">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="7c91e-111">The operation was successful.</span></span>|  
|<span data-ttu-id="7c91e-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7c91e-112">S_FALSE</span></span>|<span data-ttu-id="7c91e-113">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="7c91e-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="7c91e-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7c91e-114">E_FAIL</span></span>|<span data-ttu-id="7c91e-115">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7c91e-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="7c91e-116">Se um método retornará E_FAIL, o common language runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="7c91e-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="7c91e-117">As chamadas subsequentes para hospedagem de APIs retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7c91e-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7c91e-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7c91e-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7c91e-119">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7c91e-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c91e-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c91e-120">Requirements</span></span>  
 <span data-ttu-id="7c91e-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c91e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c91e-122">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7c91e-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c91e-123">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7c91e-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c91e-124">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="7c91e-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c91e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c91e-125">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="7c91e-126">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="7c91e-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
