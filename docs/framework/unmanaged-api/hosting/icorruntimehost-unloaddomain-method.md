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
ms.openlocfilehash: 9d769c54c67e146df3dbe00f3a7aedad43ba548a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528687"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="5312f-102">Método ICorRuntimeHost::UnloadDomain</span><span class="sxs-lookup"><span data-stu-id="5312f-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="5312f-103">Descarrega o domínio de aplicativo especificado do processo atual.</span><span class="sxs-lookup"><span data-stu-id="5312f-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5312f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5312f-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5312f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5312f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5312f-106">[in] Um ponteiro de tipo <xref:System._AppDomain?displayProperty=nameWithType> que representa o domínio a ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="5312f-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5312f-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5312f-107">Return Value</span></span>  
  
|<span data-ttu-id="5312f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5312f-108">HRESULT</span></span>|<span data-ttu-id="5312f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5312f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5312f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5312f-110">S_OK</span></span>|<span data-ttu-id="5312f-111">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="5312f-111">The operation was successful.</span></span>|  
|<span data-ttu-id="5312f-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5312f-112">S_FALSE</span></span>|<span data-ttu-id="5312f-113">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="5312f-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="5312f-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5312f-114">E_FAIL</span></span>|<span data-ttu-id="5312f-115">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="5312f-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="5312f-116">Se um método retornar E_FAIL, o common language runtime (CLR) não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="5312f-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="5312f-117">As chamadas subsequentes para todas as APIs de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5312f-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5312f-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5312f-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5312f-119">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5312f-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5312f-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5312f-120">Requirements</span></span>  
 <span data-ttu-id="5312f-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5312f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5312f-122">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5312f-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5312f-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5312f-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5312f-124">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="5312f-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5312f-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5312f-125">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="5312f-126">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="5312f-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
