---
title: Método ICorRuntimeHost::EnumDomains
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.EnumDomains
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 545af69e06e7ea4262450025e9cb0d6529f99ad4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780052"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="bb998-102">Método ICorRuntimeHost::EnumDomains</span><span class="sxs-lookup"><span data-stu-id="bb998-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="bb998-103">Obtém um enumerador para os domínios no processo atual.</span><span class="sxs-lookup"><span data-stu-id="bb998-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb998-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb998-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb998-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bb998-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="bb998-106">[out] Um enumerador para os domínios.</span><span class="sxs-lookup"><span data-stu-id="bb998-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb998-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bb998-107">Return Value</span></span>  
  
|<span data-ttu-id="bb998-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb998-108">HRESULT</span></span>|<span data-ttu-id="bb998-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb998-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb998-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb998-110">S_OK</span></span>|<span data-ttu-id="bb998-111">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="bb998-111">The operation was successful.</span></span>|  
|<span data-ttu-id="bb998-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bb998-112">S_FALSE</span></span>|<span data-ttu-id="bb998-113">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="bb998-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="bb998-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb998-114">E_FAIL</span></span>|<span data-ttu-id="bb998-115">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="bb998-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="bb998-116">Se um método retornar E_FAIL, o common language runtime (CLR) não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="bb998-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="bb998-117">As chamadas subsequentes para todas as APIs de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bb998-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bb998-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bb998-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bb998-119">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="bb998-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb998-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb998-120">Requirements</span></span>  
 <span data-ttu-id="bb998-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb998-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb998-122">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb998-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb998-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bb998-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb998-124">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="bb998-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb998-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb998-125">See also</span></span>

- [<span data-ttu-id="bb998-126">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="bb998-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
