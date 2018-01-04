---
title: "Método ICLRRuntimeInfo::LoadErrorString"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.LoadErrorString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6253844e931b7b9126b2df28c7977eaa1d92d70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="d06f3-102">Método ICLRRuntimeInfo::LoadErrorString</span><span class="sxs-lookup"><span data-stu-id="d06f3-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="d06f3-103">Converte um valor HRESULT em uma mensagem de erro apropriada para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="d06f3-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="d06f3-104">Esse método substitui as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="d06f3-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="d06f3-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="d06f3-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="d06f3-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="d06f3-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="d06f3-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d06f3-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d06f3-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d06f3-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="d06f3-109">[in] O HRESULT para traduzir.</span><span class="sxs-lookup"><span data-stu-id="d06f3-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="d06f3-110">[out] A cadeia de caracteres de mensagem associada o determinado HRESULT.</span><span class="sxs-lookup"><span data-stu-id="d06f3-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="d06f3-111">[out no] O tamanho de `pwzbuffer` para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="d06f3-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="d06f3-112">Se `pwzbuffer` for nulo, `pcchBuffer` fornece o tamanho esperado do `pwzbuffer` para permitir a pré-alocação.</span><span class="sxs-lookup"><span data-stu-id="d06f3-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="d06f3-113">[in] O identificador de cultura.</span><span class="sxs-lookup"><span data-stu-id="d06f3-113">[in] The culture identifier.</span></span> <span data-ttu-id="d06f3-114">Para usar a cultura padrão, você deve especificar -1.</span><span class="sxs-lookup"><span data-stu-id="d06f3-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d06f3-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d06f3-115">Return Value</span></span>  
 <span data-ttu-id="d06f3-116">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="d06f3-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d06f3-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d06f3-117">HRESULT</span></span>|<span data-ttu-id="d06f3-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="d06f3-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d06f3-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="d06f3-119">S_OK</span></span>|<span data-ttu-id="d06f3-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="d06f3-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="d06f3-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d06f3-121">E_POINTER</span></span>|<span data-ttu-id="d06f3-122">`pcchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="d06f3-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="d06f3-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d06f3-123">E_INVALIDARG</span></span>|<span data-ttu-id="d06f3-124">`pwzBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="d06f3-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d06f3-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d06f3-125">Requirements</span></span>  
 <span data-ttu-id="d06f3-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d06f3-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d06f3-127">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d06f3-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d06f3-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d06f3-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d06f3-129">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d06f3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06f3-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d06f3-130">See Also</span></span>  
 [<span data-ttu-id="d06f3-131">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="d06f3-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="d06f3-132">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="d06f3-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="d06f3-133">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="d06f3-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
