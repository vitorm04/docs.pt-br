---
title: "Função CLRCreateInstance"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type: COM
f1_keywords: CLRCreateInstance
helpviewer_keywords: CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d95815dd0b2a1cdbddcb28a2e176bc12d3270ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="f7630-102">Função CLRCreateInstance</span><span class="sxs-lookup"><span data-stu-id="f7630-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="f7630-103">Fornece uma das três interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), ou [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f7630-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7630-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7630-104">Syntax</span></span>  
  
```  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7630-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f7630-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="f7630-106">[in] Um dos três identificadores de classe: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy ou CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="f7630-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="f7630-107">[in] Um dos três identificadores de interface (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy ou IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="f7630-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="f7630-108">[out] Um dos três interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), ou [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f7630-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7630-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f7630-109">Return Value</span></span>  
 <span data-ttu-id="f7630-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="f7630-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f7630-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7630-111">HRESULT</span></span>|<span data-ttu-id="f7630-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7630-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7630-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7630-113">S_OK</span></span>|<span data-ttu-id="f7630-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="f7630-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="f7630-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f7630-115">E_POINTER</span></span>|<span data-ttu-id="f7630-116">`ppInterface` é nulo.</span><span class="sxs-lookup"><span data-stu-id="f7630-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7630-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7630-117">Remarks</span></span>  
 <span data-ttu-id="f7630-118">A tabela a seguir mostra as combinações com suporte para `clsid` e `riid`.</span><span class="sxs-lookup"><span data-stu-id="f7630-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="f7630-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="f7630-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="f7630-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="f7630-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="f7630-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="f7630-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="f7630-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="f7630-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="f7630-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="f7630-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="f7630-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="f7630-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="f7630-125">O código a seguir mostra como usar `CLRCreateInstance` para obter todos os três interfaces:</span><span class="sxs-lookup"><span data-stu-id="f7630-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f7630-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7630-126">Requirements</span></span>  
 <span data-ttu-id="f7630-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7630-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7630-128">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f7630-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f7630-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f7630-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7630-130">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7630-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7630-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7630-131">See Also</span></span>  
 [<span data-ttu-id="f7630-132">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="f7630-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
