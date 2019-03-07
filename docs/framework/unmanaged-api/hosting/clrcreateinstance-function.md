---
title: Função CLRCreateInstance
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9b4e9149fa50a951f2a56c83412e42fe86b9563
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501195"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="db170-102">Função CLRCreateInstance</span><span class="sxs-lookup"><span data-stu-id="db170-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="db170-103">Fornece uma das três interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), ou [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="db170-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db170-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db170-104">Syntax</span></span>  
  
```  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db170-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db170-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="db170-106">[in] Um dos três identificadores de classe: Argumentos CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy ou CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="db170-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="db170-107">[in] Um dos três identificadores de interface (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy ou IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="db170-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="db170-108">[out] Uma das três interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), ou [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="db170-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db170-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="db170-109">Return Value</span></span>  
 <span data-ttu-id="db170-110">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="db170-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="db170-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db170-111">HRESULT</span></span>|<span data-ttu-id="db170-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="db170-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db170-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="db170-113">S_OK</span></span>|<span data-ttu-id="db170-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="db170-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="db170-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="db170-115">E_POINTER</span></span>|<span data-ttu-id="db170-116">`ppInterface` é nulo.</span><span class="sxs-lookup"><span data-stu-id="db170-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db170-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="db170-117">Remarks</span></span>  
 <span data-ttu-id="db170-118">A tabela a seguir mostra as combinações com suporte para `clsid` e `riid`.</span><span class="sxs-lookup"><span data-stu-id="db170-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="db170-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="db170-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="db170-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="db170-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="db170-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="db170-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="db170-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="db170-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="db170-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="db170-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="db170-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="db170-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="db170-125">O código a seguir mostra como usar `CLRCreateInstance` para obter todos os três interfaces:</span><span class="sxs-lookup"><span data-stu-id="db170-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="db170-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db170-126">Requirements</span></span>  
 <span data-ttu-id="db170-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db170-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db170-128">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="db170-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="db170-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="db170-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db170-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db170-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db170-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db170-131">See also</span></span>
- [<span data-ttu-id="db170-132">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="db170-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
