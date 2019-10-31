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
ms.openlocfilehash: e2eddfab68e5c9e2ebffe2c96c9348f3cd799c7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127760"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="efcba-102">Método ICorRuntimeHost::CloseEnum</span><span class="sxs-lookup"><span data-stu-id="efcba-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="efcba-103">Redefine um enumerador de domínio de volta para o início da lista de domínios.</span><span class="sxs-lookup"><span data-stu-id="efcba-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efcba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="efcba-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efcba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="efcba-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="efcba-106">no O enumerador a ser redefinido.</span><span class="sxs-lookup"><span data-stu-id="efcba-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efcba-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="efcba-107">Return Value</span></span>  
  
|<span data-ttu-id="efcba-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="efcba-108">HRESULT</span></span>|<span data-ttu-id="efcba-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="efcba-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="efcba-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="efcba-110">S_OK</span></span>|<span data-ttu-id="efcba-111">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="efcba-111">The operation was successful.</span></span>|  
|<span data-ttu-id="efcba-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="efcba-112">S_FALSE</span></span>|<span data-ttu-id="efcba-113">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="efcba-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="efcba-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="efcba-114">E_FAIL</span></span>|<span data-ttu-id="efcba-115">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="efcba-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="efcba-116">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="efcba-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="efcba-117">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="efcba-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="efcba-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="efcba-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="efcba-119">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="efcba-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="efcba-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="efcba-120">Requirements</span></span>  
 <span data-ttu-id="efcba-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efcba-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efcba-122">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="efcba-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="efcba-123">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="efcba-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="efcba-124">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="efcba-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efcba-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="efcba-125">See also</span></span>

- [<span data-ttu-id="efcba-126">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="efcba-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="efcba-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="efcba-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
