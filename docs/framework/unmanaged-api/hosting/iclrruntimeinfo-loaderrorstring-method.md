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
ms.openlocfilehash: da6efae38cd70a68feea56b12e86be23fde7f0cb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762182"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="461e5-102">Método ICLRRuntimeInfo::LoadErrorString</span><span class="sxs-lookup"><span data-stu-id="461e5-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="461e5-103">Traduz um valor HRESULT em uma mensagem de erro apropriada para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="461e5-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="461e5-104">Esse método substitui as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="461e5-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="461e5-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="461e5-105">LoadStringRC</span></span>](loadstringrc-function.md)  
  
- [<span data-ttu-id="461e5-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="461e5-106">LoadStringRCEx</span></span>](loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="461e5-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="461e5-107">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="461e5-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="461e5-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="461e5-109">no O HRESULT a ser traduzido.</span><span class="sxs-lookup"><span data-stu-id="461e5-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="461e5-110">fora A cadeia de caracteres da mensagem associada ao HRESULT fornecido.</span><span class="sxs-lookup"><span data-stu-id="461e5-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="461e5-111">[entrada, saída] O tamanho de `pwzbuffer` para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="461e5-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="461e5-112">Se `pwzbuffer` for NULL, `pcchBuffer` fornecerá o tamanho esperado de `pwzbuffer` para permitir a prealocação.</span><span class="sxs-lookup"><span data-stu-id="461e5-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="461e5-113">no O identificador de cultura.</span><span class="sxs-lookup"><span data-stu-id="461e5-113">[in] The culture identifier.</span></span> <span data-ttu-id="461e5-114">Para usar a cultura padrão, você deve especificar-1.</span><span class="sxs-lookup"><span data-stu-id="461e5-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="461e5-115">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="461e5-115">Return Value</span></span>  
 <span data-ttu-id="461e5-116">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="461e5-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="461e5-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="461e5-117">HRESULT</span></span>|<span data-ttu-id="461e5-118">Description</span><span class="sxs-lookup"><span data-stu-id="461e5-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="461e5-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="461e5-119">S_OK</span></span>|<span data-ttu-id="461e5-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="461e5-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="461e5-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="461e5-121">E_POINTER</span></span>|<span data-ttu-id="461e5-122">`pcchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="461e5-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="461e5-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="461e5-123">E_INVALIDARG</span></span>|<span data-ttu-id="461e5-124">`pwzBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="461e5-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="461e5-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="461e5-125">Requirements</span></span>  
 <span data-ttu-id="461e5-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="461e5-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="461e5-127">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="461e5-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="461e5-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="461e5-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="461e5-129">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="461e5-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="461e5-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="461e5-130">See also</span></span>

- [<span data-ttu-id="461e5-131">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="461e5-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="461e5-132">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="461e5-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="461e5-133">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="461e5-133">Hosting</span></span>](index.md)
