---
title: Método ICorRuntimeHost::CurrentDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CurrentDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type:
- apiref
ms.openlocfilehash: 38042876cf4397418d2e6e6ed2bfbeb2df2d62d8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762286"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="5231c-102">Método ICorRuntimeHost::CurrentDomain</span><span class="sxs-lookup"><span data-stu-id="5231c-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="5231c-103">Obtém um ponteiro de interface do tipo <xref:System.AppDomain?displayProperty=nameWithType> que representa o domínio carregado no thread atual.</span><span class="sxs-lookup"><span data-stu-id="5231c-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5231c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5231c-104">Syntax</span></span>  
  
```cpp  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5231c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5231c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5231c-106">fora Um ponteiro do tipo <xref:System.AppDomain?displayProperty=nameWithType> que representa o domínio do aplicativo atual do thread.</span><span class="sxs-lookup"><span data-stu-id="5231c-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="5231c-107">Esse ponteiro é digitado `IUnknown` , de modo que os chamadores geralmente devem chamar `QueryInterface` para obter um ponteiro do tipo <xref:System._AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="5231c-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5231c-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="5231c-108">Return Value</span></span>  
  
|<span data-ttu-id="5231c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5231c-109">HRESULT</span></span>|<span data-ttu-id="5231c-110">Description</span><span class="sxs-lookup"><span data-stu-id="5231c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5231c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5231c-111">S_OK</span></span>|<span data-ttu-id="5231c-112">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="5231c-112">The operation was successful.</span></span>|  
|<span data-ttu-id="5231c-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5231c-113">S_FALSE</span></span>|<span data-ttu-id="5231c-114">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="5231c-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="5231c-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5231c-115">E_FAIL</span></span>|<span data-ttu-id="5231c-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="5231c-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="5231c-117">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="5231c-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="5231c-118">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5231c-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5231c-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5231c-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5231c-120">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5231c-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5231c-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5231c-121">Requirements</span></span>  
 <span data-ttu-id="5231c-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5231c-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5231c-123">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5231c-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5231c-124">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5231c-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5231c-125">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="5231c-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5231c-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="5231c-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="5231c-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="5231c-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
