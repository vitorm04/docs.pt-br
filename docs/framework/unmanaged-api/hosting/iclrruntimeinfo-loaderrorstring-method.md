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
ms.openlocfilehash: b485811b0e7d2f657ff2d2c1d7a2aa135e48a335
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154681"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="e330d-102">Método ICLRRuntimeInfo::LoadErrorString</span><span class="sxs-lookup"><span data-stu-id="e330d-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="e330d-103">Converte um valor HRESULT em uma mensagem de erro apropriada para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="e330d-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="e330d-104">Esse método substitui as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="e330d-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="e330d-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="e330d-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="e330d-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="e330d-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="e330d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e330d-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e330d-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e330d-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="e330d-109">[in] O HRESULT para traduzir.</span><span class="sxs-lookup"><span data-stu-id="e330d-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="e330d-110">[out] A cadeia de caracteres de mensagem associada com o HRESULT fornecido.</span><span class="sxs-lookup"><span data-stu-id="e330d-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="e330d-111">[no, out] O tamanho de `pwzbuffer` para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="e330d-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="e330d-112">Se `pwzbuffer` for nulo, `pcchBuffer` fornece o tamanho esperado do `pwzbuffer` para permitir a pré-alocação.</span><span class="sxs-lookup"><span data-stu-id="e330d-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="e330d-113">[in] O identificador de cultura.</span><span class="sxs-lookup"><span data-stu-id="e330d-113">[in] The culture identifier.</span></span> <span data-ttu-id="e330d-114">Para usar a cultura padrão, você deverá especificar -1.</span><span class="sxs-lookup"><span data-stu-id="e330d-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e330d-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e330d-115">Return Value</span></span>  
 <span data-ttu-id="e330d-116">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="e330d-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e330d-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e330d-117">HRESULT</span></span>|<span data-ttu-id="e330d-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e330d-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e330d-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="e330d-119">S_OK</span></span>|<span data-ttu-id="e330d-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="e330d-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="e330d-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e330d-121">E_POINTER</span></span>|<span data-ttu-id="e330d-122">`pcchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="e330d-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="e330d-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e330d-123">E_INVALIDARG</span></span>|<span data-ttu-id="e330d-124">`pwzBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="e330d-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e330d-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e330d-125">Requirements</span></span>  
 <span data-ttu-id="e330d-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e330d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e330d-127">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e330d-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e330d-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e330d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e330d-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e330d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e330d-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e330d-130">See also</span></span>

- [<span data-ttu-id="e330d-131">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="e330d-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="e330d-132">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="e330d-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="e330d-133">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="e330d-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
