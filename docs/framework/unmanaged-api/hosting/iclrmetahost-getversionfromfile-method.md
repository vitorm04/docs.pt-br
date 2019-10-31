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
ms.openlocfilehash: a237dff63015cda2cf2ca86a64bb4028ec9b6e2c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140922"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="1dfa6-102">Método ICLRMetaHost::GetVersionFromFile</span><span class="sxs-lookup"><span data-stu-id="1dfa6-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="1dfa6-103">Obtém a versão de compilação de .NET Framework original de um assembly (armazenada nos metadados), dado seu caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="1dfa6-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="1dfa6-104">Esse método substitui a função [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="1dfa6-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dfa6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1dfa6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dfa6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1dfa6-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="1dfa6-107">no O caminho completo do arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="1dfa6-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="1dfa6-108">fora A versão de compilação .NET Framework armazenada nos metadados, no formato "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="1dfa6-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="1dfa6-109">*A*, *B*e *X* são números decimais que correspondem à versão principal, à versão secundária e ao número da compilação.</span><span class="sxs-lookup"><span data-stu-id="1dfa6-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="1dfa6-110">O comprimento dessa cadeia de caracteres é limitado a MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="1dfa6-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1dfa6-111">Essa saída corresponde ao nome do diretório para a versão .NET Framework, como aparece em C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="1dfa6-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="1dfa6-112">Os valores de exemplo são "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" e "v 4.0. *X*", em que *x* depende do número de Build instalado.</span><span class="sxs-lookup"><span data-stu-id="1dfa6-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="1dfa6-113">Observe que o prefixo "v" é necessário.</span><span class="sxs-lookup"><span data-stu-id="1dfa6-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="1dfa6-114">[entrada, saída] O tamanho de `pwzbuffer` para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="1dfa6-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dfa6-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1dfa6-115">Return Value</span></span>  
 <span data-ttu-id="1dfa6-116">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="1dfa6-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1dfa6-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1dfa6-117">HRESULT</span></span>|<span data-ttu-id="1dfa6-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dfa6-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1dfa6-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="1dfa6-119">S_OK</span></span>|<span data-ttu-id="1dfa6-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="1dfa6-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="1dfa6-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="1dfa6-121">E_POINTER</span></span>|<span data-ttu-id="1dfa6-122">`pwzbuffer` ou `pcchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="1dfa6-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="1dfa6-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="1dfa6-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="1dfa6-124">O buffer é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="1dfa6-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1dfa6-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1dfa6-125">Requirements</span></span>  
 <span data-ttu-id="1dfa6-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dfa6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dfa6-127">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="1dfa6-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1dfa6-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1dfa6-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dfa6-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dfa6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dfa6-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1dfa6-130">See also</span></span>

- [<span data-ttu-id="1dfa6-131">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="1dfa6-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="1dfa6-132">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="1dfa6-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
