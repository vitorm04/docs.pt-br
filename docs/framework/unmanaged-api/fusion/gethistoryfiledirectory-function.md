---
title: Função GetHistoryFileDirectory
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bba40acf7bfd20897ece4de285fe7a9175be83e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="91a71-102">Função GetHistoryFileDirectory</span><span class="sxs-lookup"><span data-stu-id="91a71-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="91a71-103">Recupera o caminho do diretório de histórico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91a71-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91a71-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91a71-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="91a71-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="91a71-106">[out] Um buffer para armazenar o caminho para o diretório de histórico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91a71-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="91a71-107">[out no] O comprimento do buffer.</span><span class="sxs-lookup"><span data-stu-id="91a71-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91a71-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="91a71-108">Return Value</span></span>  
 <span data-ttu-id="91a71-109">Esse método retorna códigos de erro COM padrão, conforme definido no arquivo de Winerror. H, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="91a71-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="91a71-110">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="91a71-110">Return code</span></span>|<span data-ttu-id="91a71-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="91a71-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="91a71-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="91a71-112">S_OK</span></span>|<span data-ttu-id="91a71-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="91a71-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="91a71-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="91a71-114">E_INVALIDARG</span></span>|<span data-ttu-id="91a71-115">`wzDir` ou `pdwSize` é nulo ou a versão de cadeia de caracteres está incorreta.</span><span class="sxs-lookup"><span data-stu-id="91a71-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91a71-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="91a71-116">Remarks</span></span>  
 <span data-ttu-id="91a71-117">Após a conclusão bem-sucedida, o `pdwSize` argumento é definido como o comprimento da cadeia de caracteres de caminho.</span><span class="sxs-lookup"><span data-stu-id="91a71-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91a71-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91a71-118">Requirements</span></span>  
 <span data-ttu-id="91a71-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91a71-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91a71-120">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="91a71-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="91a71-121">**Biblioteca:** Fusion e arquivo Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="91a71-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="91a71-122">Use Fusion em vez do arquivo Mscorwks.dll para garantir que você a versão correta do .NET Framework de destino.</span><span class="sxs-lookup"><span data-stu-id="91a71-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="91a71-123">**Versões do .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91a71-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a71-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91a71-124">See Also</span></span>  
 [<span data-ttu-id="91a71-125">Função CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="91a71-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="91a71-126">Função NukeDownloadedCache</span><span class="sxs-lookup"><span data-stu-id="91a71-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [<span data-ttu-id="91a71-127">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="91a71-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
