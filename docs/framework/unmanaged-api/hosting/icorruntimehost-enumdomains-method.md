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
ms.openlocfilehash: a97471e1c257902633b7eb363c3cc51288c70917
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762247"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="0ccd0-102">Método ICorRuntimeHost::EnumDomains</span><span class="sxs-lookup"><span data-stu-id="0ccd0-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="0ccd0-103">Obtém um enumerador para os domínios no processo atual.</span><span class="sxs-lookup"><span data-stu-id="0ccd0-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ccd0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ccd0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ccd0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ccd0-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="0ccd0-106">fora Um enumerador para os domínios.</span><span class="sxs-lookup"><span data-stu-id="0ccd0-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ccd0-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="0ccd0-107">Return Value</span></span>  
  
|<span data-ttu-id="0ccd0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ccd0-108">HRESULT</span></span>|<span data-ttu-id="0ccd0-109">Description</span><span class="sxs-lookup"><span data-stu-id="0ccd0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ccd0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ccd0-110">S_OK</span></span>|<span data-ttu-id="0ccd0-111">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ccd0-111">The operation was successful.</span></span>|  
|<span data-ttu-id="0ccd0-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0ccd0-112">S_FALSE</span></span>|<span data-ttu-id="0ccd0-113">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="0ccd0-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="0ccd0-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ccd0-114">E_FAIL</span></span>|<span data-ttu-id="0ccd0-115">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0ccd0-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0ccd0-116">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="0ccd0-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="0ccd0-117">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0ccd0-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0ccd0-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ccd0-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ccd0-119">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0ccd0-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ccd0-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0ccd0-120">Requirements</span></span>  
 <span data-ttu-id="0ccd0-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ccd0-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ccd0-122">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ccd0-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ccd0-123">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0ccd0-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ccd0-124">**Versão do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="0ccd0-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ccd0-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="0ccd0-125">See also</span></span>

- [<span data-ttu-id="0ccd0-126">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0ccd0-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
