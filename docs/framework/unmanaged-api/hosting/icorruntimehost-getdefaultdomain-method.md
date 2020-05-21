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
ms.openlocfilehash: a23083777d0cd5965511f3689578a60220008420
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762224"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="3013f-102">Método ICorRuntimeHost::GetDefaultDomain</span><span class="sxs-lookup"><span data-stu-id="3013f-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="3013f-103">Obtém um ponteiro de interface do tipo <xref:System._AppDomain?displayProperty=nameWithType> que representa o domínio padrão para o processo atual.</span><span class="sxs-lookup"><span data-stu-id="3013f-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3013f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3013f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3013f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3013f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="3013f-106">fora Um ponteiro de interface do tipo <xref:System._AppDomain?displayProperty=nameWithType> para a <xref:System.AppDomain> instância que representa o domínio de aplicativo padrão para o processo.</span><span class="sxs-lookup"><span data-stu-id="3013f-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="3013f-107">Esse ponteiro é digitado `IUnknown` , de modo que os chamadores geralmente devem chamar `QueryInterface` para obter um ponteiro de interface do tipo <xref:System._AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3013f-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3013f-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="3013f-108">Return Value</span></span>  
  
|<span data-ttu-id="3013f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3013f-109">HRESULT</span></span>|<span data-ttu-id="3013f-110">Description</span><span class="sxs-lookup"><span data-stu-id="3013f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3013f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3013f-111">S_OK</span></span>|<span data-ttu-id="3013f-112">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="3013f-112">The operation was successful.</span></span>|  
|<span data-ttu-id="3013f-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="3013f-113">S_FALSE</span></span>|<span data-ttu-id="3013f-114">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="3013f-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="3013f-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3013f-115">E_FAIL</span></span>|<span data-ttu-id="3013f-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3013f-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="3013f-117">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="3013f-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="3013f-118">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3013f-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3013f-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3013f-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3013f-120">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3013f-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3013f-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3013f-121">Requirements</span></span>  
 <span data-ttu-id="3013f-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3013f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3013f-123">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3013f-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3013f-124">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3013f-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3013f-125">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="3013f-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3013f-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="3013f-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="3013f-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="3013f-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
