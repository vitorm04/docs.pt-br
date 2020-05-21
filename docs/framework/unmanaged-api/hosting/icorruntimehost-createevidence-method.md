---
title: Método ICorRuntimeHost::CreateEvidence
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
ms.openlocfilehash: 4a91f57126c0cf2074bd086ddb2fb4cd9e0716d4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762312"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="aa55c-102">Método ICorRuntimeHost::CreateEvidence</span><span class="sxs-lookup"><span data-stu-id="aa55c-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="aa55c-103">Obtém um ponteiro de interface do tipo <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> , que permite que o host crie evidências de segurança para passar para o método [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) ou [CreateDomainEx](icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="aa55c-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa55c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa55c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa55c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa55c-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="aa55c-106">fora Um ponteiro de interface para uma <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instância usada para criar evidências de segurança.</span><span class="sxs-lookup"><span data-stu-id="aa55c-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="aa55c-107">Esse ponteiro é digitado `IUnknown` , de modo que os chamadores normalmente devem chamar `QueryInterface` essa interface para obter um ponteiro para um <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="aa55c-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa55c-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="aa55c-108">Return Value</span></span>  
  
|<span data-ttu-id="aa55c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa55c-109">HRESULT</span></span>|<span data-ttu-id="aa55c-110">Description</span><span class="sxs-lookup"><span data-stu-id="aa55c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa55c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa55c-111">S_OK</span></span>|<span data-ttu-id="aa55c-112">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="aa55c-112">The operation was successful.</span></span>|  
|<span data-ttu-id="aa55c-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="aa55c-113">S_FALSE</span></span>|<span data-ttu-id="aa55c-114">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="aa55c-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="aa55c-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa55c-115">E_FAIL</span></span>|<span data-ttu-id="aa55c-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="aa55c-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="aa55c-117">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="aa55c-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="aa55c-118">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aa55c-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aa55c-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa55c-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa55c-120">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="aa55c-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa55c-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa55c-121">Remarks</span></span>  
 <span data-ttu-id="aa55c-122">Esse método retorna uma coleção vazia que não pode ser populada a partir de código nativo.</span><span class="sxs-lookup"><span data-stu-id="aa55c-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="aa55c-123"><xref:System.Security.Policy.Evidence>Em vez disso, você deve usar o método.</span><span class="sxs-lookup"><span data-stu-id="aa55c-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa55c-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa55c-124">Requirements</span></span>  
 <span data-ttu-id="aa55c-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa55c-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa55c-126">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aa55c-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa55c-127">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aa55c-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa55c-128">**Versão do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="aa55c-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa55c-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="aa55c-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="aa55c-130">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="aa55c-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
