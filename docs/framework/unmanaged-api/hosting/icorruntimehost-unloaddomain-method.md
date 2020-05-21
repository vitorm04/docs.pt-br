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
ms.openlocfilehash: 558b6e4c6ac369e33be3d45b7241e8b11db8bfae
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760388"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="b3461-102">Método ICorRuntimeHost::UnloadDomain</span><span class="sxs-lookup"><span data-stu-id="b3461-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="b3461-103">Descarrega o domínio de aplicativo especificado do processo atual.</span><span class="sxs-lookup"><span data-stu-id="b3461-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3461-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3461-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3461-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b3461-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b3461-106">no Um ponteiro do tipo <xref:System._AppDomain?displayProperty=nameWithType> que representa o domínio a ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="b3461-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3461-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="b3461-107">Return Value</span></span>  
  
|<span data-ttu-id="b3461-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3461-108">HRESULT</span></span>|<span data-ttu-id="b3461-109">Description</span><span class="sxs-lookup"><span data-stu-id="b3461-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3461-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3461-110">S_OK</span></span>|<span data-ttu-id="b3461-111">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b3461-111">The operation was successful.</span></span>|  
|<span data-ttu-id="b3461-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b3461-112">S_FALSE</span></span>|<span data-ttu-id="b3461-113">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="b3461-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="b3461-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b3461-114">E_FAIL</span></span>|<span data-ttu-id="b3461-115">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b3461-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="b3461-116">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="b3461-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="b3461-117">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b3461-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b3461-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b3461-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b3461-119">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b3461-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b3461-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3461-120">Requirements</span></span>  
 <span data-ttu-id="b3461-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3461-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3461-122">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b3461-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3461-123">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b3461-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3461-124">**Versão do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="b3461-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3461-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="b3461-125">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="b3461-126">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="b3461-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
