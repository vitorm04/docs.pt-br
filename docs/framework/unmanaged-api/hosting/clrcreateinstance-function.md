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
ms.openlocfilehash: 4ab16d78b210c2824bf6172f80d1b15e3533a05b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172130"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="770b7-102">Função CLRCreateInstance</span><span class="sxs-lookup"><span data-stu-id="770b7-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="770b7-103">Fornece uma das três interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), ou [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="770b7-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="770b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="770b7-104">Syntax</span></span>  
  
```  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="770b7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="770b7-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="770b7-106">[in] Um dos três identificadores de classe: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy ou CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="770b7-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="770b7-107">[in] Um dos três identificadores de interface (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy ou IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="770b7-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="770b7-108">[out] Um dos três interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), ou [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="770b7-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="770b7-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="770b7-109">Return Value</span></span>  
 <span data-ttu-id="770b7-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="770b7-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="770b7-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="770b7-111">HRESULT</span></span>|<span data-ttu-id="770b7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="770b7-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="770b7-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="770b7-113">S_OK</span></span>|<span data-ttu-id="770b7-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="770b7-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="770b7-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="770b7-115">E_POINTER</span></span>|<span data-ttu-id="770b7-116">`ppInterface` é nulo.</span><span class="sxs-lookup"><span data-stu-id="770b7-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="770b7-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="770b7-117">Remarks</span></span>  
 <span data-ttu-id="770b7-118">A tabela a seguir mostra as combinações com suporte para `clsid` e `riid`.</span><span class="sxs-lookup"><span data-stu-id="770b7-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="770b7-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="770b7-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="770b7-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="770b7-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="770b7-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="770b7-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="770b7-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="770b7-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="770b7-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="770b7-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="770b7-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="770b7-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="770b7-125">O código a seguir mostra como usar `CLRCreateInstance` para obter todos os três interfaces:</span><span class="sxs-lookup"><span data-stu-id="770b7-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="770b7-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="770b7-126">Requirements</span></span>  
 <span data-ttu-id="770b7-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="770b7-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="770b7-128">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="770b7-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="770b7-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="770b7-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="770b7-130">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="770b7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="770b7-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="770b7-131">See Also</span></span>  
 [<span data-ttu-id="770b7-132">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="770b7-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
