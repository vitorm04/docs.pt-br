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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a06d57348cfbdfb8bb57580a48e54e298e27e166
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438188"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="de053-102">Método ICorRuntimeHost::CreateEvidence</span><span class="sxs-lookup"><span data-stu-id="de053-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="de053-103">Obtém um ponteiro de interface do tipo <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, que permite que o host criar a evidência de segurança para passar para o [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) ou [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="de053-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de053-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de053-104">Syntax</span></span>  
  
```  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de053-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de053-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="de053-106">[out] Um ponteiro de interface para um <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instância usada para criar a evidência de segurança.</span><span class="sxs-lookup"><span data-stu-id="de053-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="de053-107">Esse ponteiro é digitado `IUnknown`, de modo que os chamadores devem chamar normalmente `QueryInterface` nesta interface para obter um ponteiro para um <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de053-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de053-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="de053-108">Return Value</span></span>  
  
|<span data-ttu-id="de053-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="de053-109">HRESULT</span></span>|<span data-ttu-id="de053-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="de053-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de053-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="de053-111">S_OK</span></span>|<span data-ttu-id="de053-112">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="de053-112">The operation was successful.</span></span>|  
|<span data-ttu-id="de053-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="de053-113">S_FALSE</span></span>|<span data-ttu-id="de053-114">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="de053-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="de053-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="de053-115">E_FAIL</span></span>|<span data-ttu-id="de053-116">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="de053-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="de053-117">Se um método retornará E_FAIL, o common language runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="de053-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="de053-118">As chamadas subsequentes para hospedagem de APIs retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="de053-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="de053-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="de053-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="de053-120">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="de053-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de053-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="de053-121">Remarks</span></span>  
 <span data-ttu-id="de053-122">Esse método retorna uma coleção vazia não é possível popular de código nativo.</span><span class="sxs-lookup"><span data-stu-id="de053-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="de053-123">Você deve usar o <xref:System.Security.Policy.Evidence> método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="de053-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de053-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de053-124">Requirements</span></span>  
 <span data-ttu-id="de053-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de053-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de053-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="de053-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="de053-127">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="de053-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de053-128">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="de053-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de053-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de053-129">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="de053-130">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="de053-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
