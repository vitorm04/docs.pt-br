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
ms.openlocfilehash: 492a60d3c8d18bec4e99ae778686fec6e8724248
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140563"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="f1d8b-102">Método ICorRuntimeHost::UnloadDomain</span><span class="sxs-lookup"><span data-stu-id="f1d8b-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="f1d8b-103">Descarrega o domínio de aplicativo especificado do processo atual.</span><span class="sxs-lookup"><span data-stu-id="f1d8b-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1d8b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1d8b-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1d8b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1d8b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f1d8b-106">[in] Um ponteiro de tipo <xref:System._AppDomain?displayProperty=nameWithType> que representa o domínio a ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="f1d8b-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1d8b-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f1d8b-107">Return Value</span></span>  
  
|<span data-ttu-id="f1d8b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1d8b-108">HRESULT</span></span>|<span data-ttu-id="f1d8b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1d8b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1d8b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1d8b-110">S_OK</span></span>|<span data-ttu-id="f1d8b-111">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="f1d8b-111">The operation was successful.</span></span>|  
|<span data-ttu-id="f1d8b-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f1d8b-112">S_FALSE</span></span>|<span data-ttu-id="f1d8b-113">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="f1d8b-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="f1d8b-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f1d8b-114">E_FAIL</span></span>|<span data-ttu-id="f1d8b-115">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f1d8b-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="f1d8b-116">Se um método retornar E_FAIL, o common language runtime (CLR) não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="f1d8b-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="f1d8b-117">As chamadas subsequentes para todas as APIs de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f1d8b-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f1d8b-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f1d8b-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f1d8b-119">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f1d8b-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1d8b-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1d8b-120">Requirements</span></span>  
 <span data-ttu-id="f1d8b-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1d8b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1d8b-122">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f1d8b-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1d8b-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f1d8b-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1d8b-124">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="f1d8b-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d8b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1d8b-125">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="f1d8b-126">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f1d8b-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
