---
title: Método ICorRuntimeHost::CreateDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
ms.openlocfilehash: 74f17c77e74edb1226dda2d9ebaa9486e1769ce4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762351"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="2de5e-102">Método ICorRuntimeHost::CreateDomain</span><span class="sxs-lookup"><span data-stu-id="2de5e-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="2de5e-103">Cria um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2de5e-103">Creates an application domain.</span></span> <span data-ttu-id="2de5e-104">O chamador recebe um ponteiro de interface do tipo <xref:System._AppDomain> para uma instância do tipo <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2de5e-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2de5e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2de5e-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2de5e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2de5e-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="2de5e-107">no Um parâmetro opcional usado para fornecer um nome amigável ao domínio.</span><span class="sxs-lookup"><span data-stu-id="2de5e-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="2de5e-108">Esse nome amigável pode ser exibido em interfaces do usuário, como depuradores, para identificar o domínio.</span><span class="sxs-lookup"><span data-stu-id="2de5e-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="2de5e-109">no Uma matriz opcional de ponteiros para `IIdentity` instâncias que representam evidências mapeadas pela política de segurança para estabelecer um conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="2de5e-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="2de5e-110">Um `IIdentity` objeto pode ser obtido chamando o método [CreateEvidence](icorruntimehost-createevidence-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2de5e-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="2de5e-111">fora Um ponteiro de interface do tipo <xref:System._AppDomain> para uma instância do <xref:System.AppDomain?displayProperty=nameWithType> que pode ser usado para controlar ainda mais o domínio.</span><span class="sxs-lookup"><span data-stu-id="2de5e-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2de5e-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="2de5e-112">Return Value</span></span>  
  
|<span data-ttu-id="2de5e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2de5e-113">HRESULT</span></span>|<span data-ttu-id="2de5e-114">Description</span><span class="sxs-lookup"><span data-stu-id="2de5e-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2de5e-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="2de5e-115">S_OK</span></span>|<span data-ttu-id="2de5e-116">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="2de5e-116">The operation was successful.</span></span>|  
|<span data-ttu-id="2de5e-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2de5e-117">S_FALSE</span></span>|<span data-ttu-id="2de5e-118">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="2de5e-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="2de5e-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2de5e-119">E_FAIL</span></span>|<span data-ttu-id="2de5e-120">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="2de5e-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="2de5e-121">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="2de5e-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="2de5e-122">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2de5e-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2de5e-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2de5e-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2de5e-124">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="2de5e-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2de5e-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2de5e-125">Requirements</span></span>  
 <span data-ttu-id="2de5e-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2de5e-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2de5e-127">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2de5e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2de5e-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2de5e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2de5e-129">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="2de5e-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2de5e-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="2de5e-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="2de5e-131">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="2de5e-131">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
