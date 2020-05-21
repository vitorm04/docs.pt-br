---
title: Método ICorRuntimeHost::CreateDomainSetup
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
ms.openlocfilehash: aa1ce70311cd4ef0204c1c31efee8bd7b313c81d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762325"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="cbbdf-102">Método ICorRuntimeHost::CreateDomainSetup</span><span class="sxs-lookup"><span data-stu-id="cbbdf-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="cbbdf-103">Obtém um ponteiro de interface do tipo IAppDomainSetup para uma <xref:System.AppDomainSetup?displayProperty=nameWithType> instância.</span><span class="sxs-lookup"><span data-stu-id="cbbdf-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="cbbdf-104">`IAppDomainSetup`fornece métodos para configurar aspectos de um domínio de aplicativo antes de sua criação.</span><span class="sxs-lookup"><span data-stu-id="cbbdf-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbbdf-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbbdf-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbbdf-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cbbdf-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="cbbdf-107">fora Um ponteiro de interface para uma <xref:System.AppDomainSetup?displayProperty=nameWithType> instância.</span><span class="sxs-lookup"><span data-stu-id="cbbdf-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="cbbdf-108">Esse parâmetro é digitado como `IUnknown` , de modo que os chamadores geralmente devem chamar `QueryInterface` esse ponteiro para obter um ponteiro de interface do tipo `IAppDomainSetup` .</span><span class="sxs-lookup"><span data-stu-id="cbbdf-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbbdf-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="cbbdf-109">Return Value</span></span>  
  
|<span data-ttu-id="cbbdf-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cbbdf-110">HRESULT</span></span>|<span data-ttu-id="cbbdf-111">Description</span><span class="sxs-lookup"><span data-stu-id="cbbdf-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cbbdf-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cbbdf-112">S_OK</span></span>|<span data-ttu-id="cbbdf-113">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="cbbdf-113">The operation was successful.</span></span>|  
|<span data-ttu-id="cbbdf-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="cbbdf-114">S_FALSE</span></span>|<span data-ttu-id="cbbdf-115">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="cbbdf-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="cbbdf-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cbbdf-116">E_FAIL</span></span>|<span data-ttu-id="cbbdf-117">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="cbbdf-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="cbbdf-118">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="cbbdf-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="cbbdf-119">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cbbdf-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cbbdf-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cbbdf-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cbbdf-121">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="cbbdf-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbbdf-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="cbbdf-122">Remarks</span></span>  
 <span data-ttu-id="cbbdf-123">O ponteiro retornado desse método normalmente é passado como um parâmetro para o método [CreateDomainEx](icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cbbdf-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbbdf-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cbbdf-124">Requirements</span></span>  
 <span data-ttu-id="cbbdf-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbbdf-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbbdf-126">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cbbdf-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cbbdf-127">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cbbdf-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbbdf-128">**Versão do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="cbbdf-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbbdf-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="cbbdf-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="cbbdf-130">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="cbbdf-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
