---
title: Método ICLRMetaHost::GetVersionFromFile
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 538e596c3a705020150f52c9e55605a49434ce8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434045"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="1f2ca-102">Método ICLRMetaHost::GetVersionFromFile</span><span class="sxs-lookup"><span data-stu-id="1f2ca-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="1f2ca-103">Obtém do .NET Framework compilação versão original um assembly (armazenado nos metadados), dado seu caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="1f2ca-104">Esse método substitui o [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f2ca-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1f2ca-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f2ca-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1f2ca-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="1f2ca-107">[in] O caminho do arquivo de assembly completo.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="1f2ca-108">[out] A versão de compilação do .NET Framework armazenada nos metadados, no formato "v*um*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="1f2ca-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="1f2ca-109">*Um*, *B*, e *X* são números decimais que correspondem a versão principal, a versão secundária, e o número de compilação.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="1f2ca-110">O comprimento da cadeia de caracteres é limitado a MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f2ca-111">Essa saída corresponde ao nome de diretório para a versão do .NET Framework, como ele aparece em C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="1f2ca-112">Os valores de exemplo são "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" e "v 4.0. *X*", onde *X* depende do número de compilação instalado.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="1f2ca-113">Observe que o prefixo "v" é necessário.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="1f2ca-114">[out no] O tamanho de `pwzbuffer` para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f2ca-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1f2ca-115">Return Value</span></span>  
 <span data-ttu-id="1f2ca-116">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1f2ca-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f2ca-117">HRESULT</span></span>|<span data-ttu-id="1f2ca-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="1f2ca-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f2ca-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f2ca-119">S_OK</span></span>|<span data-ttu-id="1f2ca-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="1f2ca-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="1f2ca-121">E_POINTER</span></span>|<span data-ttu-id="1f2ca-122">`pwzbuffer` ou `pcchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="1f2ca-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="1f2ca-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="1f2ca-124">O buffer é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1f2ca-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1f2ca-125">Requirements</span></span>  
 <span data-ttu-id="1f2ca-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f2ca-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f2ca-127">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1f2ca-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1f2ca-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1f2ca-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f2ca-129">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f2ca-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f2ca-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f2ca-130">See Also</span></span>  
 [<span data-ttu-id="1f2ca-131">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="1f2ca-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="1f2ca-132">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="1f2ca-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
