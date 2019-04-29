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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea63627bc1e689c93634c8fe8b9048b271758573
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937041"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="1110c-102">Método ICorRuntimeHost::CreateDomain</span><span class="sxs-lookup"><span data-stu-id="1110c-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="1110c-103">Cria um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1110c-103">Creates an application domain.</span></span> <span data-ttu-id="1110c-104">O chamador recebe um ponteiro de interface do tipo <xref:System._AppDomain> a uma instância do tipo <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1110c-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1110c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1110c-105">Syntax</span></span>  
  
```  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1110c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1110c-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="1110c-107">[in] Um parâmetro opcional usado para dar um nome amigável no domínio.</span><span class="sxs-lookup"><span data-stu-id="1110c-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="1110c-108">Este nome amigável pode ser exibido nas interfaces do usuário, como depuradores para identificar o domínio.</span><span class="sxs-lookup"><span data-stu-id="1110c-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="1110c-109">[in] Uma matriz opcional de ponteiros para `IIdentity` instâncias que representam a evidência mapeada por meio da política de segurança para estabelecer um conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="1110c-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="1110c-110">Uma `IIdentity` objeto pode ser obtido chamando o [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="1110c-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="1110c-111">[out] Um ponteiro de interface do tipo <xref:System._AppDomain> a uma instância de <xref:System.AppDomain?displayProperty=nameWithType> que pode ser usado para controlar ainda mais o domínio.</span><span class="sxs-lookup"><span data-stu-id="1110c-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1110c-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1110c-112">Return Value</span></span>  
  
|<span data-ttu-id="1110c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1110c-113">HRESULT</span></span>|<span data-ttu-id="1110c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1110c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1110c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1110c-115">S_OK</span></span>|<span data-ttu-id="1110c-116">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="1110c-116">The operation was successful.</span></span>|  
|<span data-ttu-id="1110c-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1110c-117">S_FALSE</span></span>|<span data-ttu-id="1110c-118">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="1110c-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1110c-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1110c-119">E_FAIL</span></span>|<span data-ttu-id="1110c-120">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1110c-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1110c-121">Se um método retornar E_FAIL, o common language runtime (CLR) não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="1110c-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1110c-122">As chamadas subsequentes para todas as APIs de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1110c-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1110c-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1110c-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1110c-124">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1110c-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1110c-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1110c-125">Requirements</span></span>  
 <span data-ttu-id="1110c-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1110c-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1110c-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1110c-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1110c-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1110c-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1110c-129">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="1110c-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1110c-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1110c-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="1110c-131">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="1110c-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
