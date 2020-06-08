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
ms.openlocfilehash: 4aeacc718632c133550ed8de6649716c5d8b7423
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504436"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="d151c-102">Função CLRCreateInstance</span><span class="sxs-lookup"><span data-stu-id="d151c-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="d151c-103">Fornece uma das três interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)ou [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d151c-103">Provides one of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d151c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d151c-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d151c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d151c-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="d151c-106">no Um dos três identificadores de classe: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy ou CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="d151c-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="d151c-107">no Um dos três identificadores de interface (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy ou IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="d151c-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="d151c-108">fora Uma das três interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)ou [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d151c-108">[out] One of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d151c-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="d151c-109">Return Value</span></span>  
 <span data-ttu-id="d151c-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="d151c-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d151c-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d151c-111">HRESULT</span></span>|<span data-ttu-id="d151c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d151c-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d151c-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d151c-113">S_OK</span></span>|<span data-ttu-id="d151c-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="d151c-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="d151c-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d151c-115">E_POINTER</span></span>|<span data-ttu-id="d151c-116">`ppInterface` é nulo.</span><span class="sxs-lookup"><span data-stu-id="d151c-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d151c-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="d151c-117">Remarks</span></span>  
 <span data-ttu-id="d151c-118">A tabela a seguir mostra as combinações com suporte para o `clsid` e o `riid` .</span><span class="sxs-lookup"><span data-stu-id="d151c-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="d151c-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="d151c-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="d151c-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="d151c-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="d151c-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="d151c-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="d151c-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="d151c-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="d151c-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="d151c-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="d151c-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="d151c-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="d151c-125">O código a seguir mostra como usar o `CLRCreateInstance` para obter todas as três interfaces:</span><span class="sxs-lookup"><span data-stu-id="d151c-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```cpp  
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
  
## <a name="requirements"></a><span data-ttu-id="d151c-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d151c-126">Requirements</span></span>  
 <span data-ttu-id="d151c-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d151c-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d151c-128">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d151c-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d151c-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d151c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d151c-130">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d151c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d151c-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="d151c-131">See also</span></span>

- [<span data-ttu-id="d151c-132">Hosting</span><span class="sxs-lookup"><span data-stu-id="d151c-132">Hosting</span></span>](index.md)
