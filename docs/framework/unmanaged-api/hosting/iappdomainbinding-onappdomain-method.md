---
title: "Método IAppDomainBinding::OnAppDomain"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppDomainBinding.OnAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f5350b9c44c04a4faee3b5026bc2b97ff549d4b4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="edb17-102">Método IAppDomainBinding::OnAppDomain</span><span class="sxs-lookup"><span data-stu-id="edb17-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="edb17-103">Chamado pelo common language runtime (CLR) para notificar o host que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="edb17-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edb17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="edb17-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edb17-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="edb17-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="edb17-106">[in] Um ponteiro para um [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) objeto de interface que representa o novo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="edb17-106">[in] A pointer to an [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edb17-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="edb17-107">Requirements</span></span>  
 <span data-ttu-id="edb17-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edb17-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edb17-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="edb17-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="edb17-110">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="edb17-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="edb17-111">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edb17-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb17-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edb17-112">See Also</span></span>  
 [<span data-ttu-id="edb17-113">Interface IAppDomainBinding</span><span class="sxs-lookup"><span data-stu-id="edb17-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
