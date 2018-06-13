---
title: Método ICLRRuntimeInfo::LoadErrorString
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43a00d687c6a9ec42cb8573e70d181b4dc2c7d0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433211"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="c9d91-102">Método ICLRRuntimeInfo::LoadErrorString</span><span class="sxs-lookup"><span data-stu-id="c9d91-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="c9d91-103">Converte um valor HRESULT em uma mensagem de erro apropriada para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="c9d91-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="c9d91-104">Esse método substitui as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="c9d91-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="c9d91-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="c9d91-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="c9d91-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="c9d91-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="c9d91-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9d91-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9d91-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9d91-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="c9d91-109">[in] O HRESULT para traduzir.</span><span class="sxs-lookup"><span data-stu-id="c9d91-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="c9d91-110">[out] A cadeia de caracteres de mensagem associada o determinado HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c9d91-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="c9d91-111">[out no] O tamanho de `pwzbuffer` para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="c9d91-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="c9d91-112">Se `pwzbuffer` for nulo, `pcchBuffer` fornece o tamanho esperado do `pwzbuffer` para permitir a pré-alocação.</span><span class="sxs-lookup"><span data-stu-id="c9d91-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="c9d91-113">[in] O identificador de cultura.</span><span class="sxs-lookup"><span data-stu-id="c9d91-113">[in] The culture identifier.</span></span> <span data-ttu-id="c9d91-114">Para usar a cultura padrão, você deve especificar -1.</span><span class="sxs-lookup"><span data-stu-id="c9d91-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9d91-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c9d91-115">Return Value</span></span>  
 <span data-ttu-id="c9d91-116">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="c9d91-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c9d91-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9d91-117">HRESULT</span></span>|<span data-ttu-id="c9d91-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9d91-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9d91-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9d91-119">S_OK</span></span>|<span data-ttu-id="c9d91-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="c9d91-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="c9d91-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="c9d91-121">E_POINTER</span></span>|<span data-ttu-id="c9d91-122">`pcchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="c9d91-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="c9d91-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c9d91-123">E_INVALIDARG</span></span>|<span data-ttu-id="c9d91-124">`pwzBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="c9d91-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9d91-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9d91-125">Requirements</span></span>  
 <span data-ttu-id="c9d91-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9d91-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9d91-127">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c9d91-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c9d91-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c9d91-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9d91-129">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9d91-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d91-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9d91-130">See Also</span></span>  
 [<span data-ttu-id="c9d91-131">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="c9d91-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="c9d91-132">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="c9d91-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="c9d91-133">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="c9d91-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
