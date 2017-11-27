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
ms.openlocfilehash: 26fa051e5c4735307edbb443e6615a57190c0ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="e6515-102">Método ICLRRuntimeInfo::LoadErrorString</span><span class="sxs-lookup"><span data-stu-id="e6515-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="e6515-103">Converte um valor HRESULT em uma mensagem de erro apropriada para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="e6515-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="e6515-104">Esse método substitui as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="e6515-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="e6515-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="e6515-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="e6515-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="e6515-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="e6515-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6515-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6515-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6515-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="e6515-109">[in] O HRESULT para traduzir.</span><span class="sxs-lookup"><span data-stu-id="e6515-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="e6515-110">[out] A cadeia de caracteres de mensagem associada o determinado HRESULT.</span><span class="sxs-lookup"><span data-stu-id="e6515-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="e6515-111">[out no] O tamanho de `pwzbuffer` para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="e6515-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="e6515-112">Se `pwzbuffer` for nulo, `pcchBuffer` fornece o tamanho esperado do `pwzbuffer` para permitir a pré-alocação.</span><span class="sxs-lookup"><span data-stu-id="e6515-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="e6515-113">[in] O identificador de cultura.</span><span class="sxs-lookup"><span data-stu-id="e6515-113">[in] The culture identifier.</span></span> <span data-ttu-id="e6515-114">Para usar a cultura padrão, você deve especificar -1.</span><span class="sxs-lookup"><span data-stu-id="e6515-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6515-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e6515-115">Return Value</span></span>  
 <span data-ttu-id="e6515-116">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="e6515-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e6515-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6515-117">HRESULT</span></span>|<span data-ttu-id="e6515-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6515-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6515-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6515-119">S_OK</span></span>|<span data-ttu-id="e6515-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="e6515-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="e6515-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e6515-121">E_POINTER</span></span>|<span data-ttu-id="e6515-122">`pcchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="e6515-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="e6515-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e6515-123">E_INVALIDARG</span></span>|<span data-ttu-id="e6515-124">`pwzBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="e6515-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6515-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6515-125">Requirements</span></span>  
 <span data-ttu-id="e6515-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6515-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6515-127">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e6515-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e6515-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e6515-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6515-129">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6515-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6515-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6515-130">See Also</span></span>  
 [<span data-ttu-id="e6515-131">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="e6515-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="e6515-132">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="e6515-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="e6515-133">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="e6515-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
