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
ms.openlocfilehash: 20f2041599e85b8df20a7a9cf44680da9f17244e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195938"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="a145f-102">Método ICLRRuntimeInfo::LoadErrorString</span><span class="sxs-lookup"><span data-stu-id="a145f-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="a145f-103">Traduz um valor HRESULT em uma mensagem de erro apropriada para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="a145f-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="a145f-104">Esse método substitui as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="a145f-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="a145f-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="a145f-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
- [<span data-ttu-id="a145f-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="a145f-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="a145f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a145f-107">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a145f-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a145f-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="a145f-109">no O HRESULT a ser traduzido.</span><span class="sxs-lookup"><span data-stu-id="a145f-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="a145f-110">fora A cadeia de caracteres da mensagem associada ao HRESULT fornecido.</span><span class="sxs-lookup"><span data-stu-id="a145f-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="a145f-111">[entrada, saída] O tamanho de `pwzbuffer` para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="a145f-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="a145f-112">Se `pwzbuffer` for NULL, `pcchBuffer` fornecerá o tamanho esperado de `pwzbuffer` para permitir a prealocação.</span><span class="sxs-lookup"><span data-stu-id="a145f-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="a145f-113">no O identificador de cultura.</span><span class="sxs-lookup"><span data-stu-id="a145f-113">[in] The culture identifier.</span></span> <span data-ttu-id="a145f-114">Para usar a cultura padrão, você deve especificar-1.</span><span class="sxs-lookup"><span data-stu-id="a145f-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a145f-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a145f-115">Return Value</span></span>  
 <span data-ttu-id="a145f-116">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="a145f-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a145f-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a145f-117">HRESULT</span></span>|<span data-ttu-id="a145f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="a145f-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a145f-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="a145f-119">S_OK</span></span>|<span data-ttu-id="a145f-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="a145f-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="a145f-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a145f-121">E_POINTER</span></span>|<span data-ttu-id="a145f-122">`pcchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="a145f-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="a145f-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a145f-123">E_INVALIDARG</span></span>|<span data-ttu-id="a145f-124">`pwzBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="a145f-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a145f-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a145f-125">Requirements</span></span>  
 <span data-ttu-id="a145f-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a145f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a145f-127">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="a145f-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a145f-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a145f-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a145f-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a145f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a145f-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a145f-130">See also</span></span>

- [<span data-ttu-id="a145f-131">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="a145f-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="a145f-132">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="a145f-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="a145f-133">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="a145f-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
