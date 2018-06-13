---
title: Método ICorRuntimeHost::CloseEnum
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 961fd6693d3a70f28fdfba8635452d4f4d943fc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437190"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="9d5f3-102">Método ICorRuntimeHost::CloseEnum</span><span class="sxs-lookup"><span data-stu-id="9d5f3-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="9d5f3-103">Redefine um enumerador de domínio para o início da lista de domínios.</span><span class="sxs-lookup"><span data-stu-id="9d5f3-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d5f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d5f3-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d5f3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d5f3-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="9d5f3-106">[in] O enumerador para redefinir.</span><span class="sxs-lookup"><span data-stu-id="9d5f3-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d5f3-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9d5f3-107">Return Value</span></span>  
  
|<span data-ttu-id="9d5f3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d5f3-108">HRESULT</span></span>|<span data-ttu-id="9d5f3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d5f3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d5f3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d5f3-110">S_OK</span></span>|<span data-ttu-id="9d5f3-111">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9d5f3-111">The operation was successful.</span></span>|  
|<span data-ttu-id="9d5f3-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9d5f3-112">S_FALSE</span></span>|<span data-ttu-id="9d5f3-113">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="9d5f3-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9d5f3-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d5f3-114">E_FAIL</span></span>|<span data-ttu-id="9d5f3-115">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9d5f3-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9d5f3-116">Se um método retornará E_FAIL, o common language runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="9d5f3-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="9d5f3-117">As chamadas subsequentes para hospedagem de APIs retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9d5f3-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9d5f3-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d5f3-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d5f3-119">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9d5f3-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d5f3-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d5f3-120">Requirements</span></span>  
 <span data-ttu-id="9d5f3-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d5f3-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d5f3-122">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d5f3-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d5f3-123">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9d5f3-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d5f3-124">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="9d5f3-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d5f3-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d5f3-125">See Also</span></span>  
 [<span data-ttu-id="9d5f3-126">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="9d5f3-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="9d5f3-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9d5f3-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
