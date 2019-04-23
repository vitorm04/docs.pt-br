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
ms.openlocfilehash: b60dde31707175a27d2dc6c50484d6089adaeaa6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229610"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="c555d-102">Função GetHistoryFileDirectory</span><span class="sxs-lookup"><span data-stu-id="c555d-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="c555d-103">Recupera o caminho do diretório de histórico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c555d-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c555d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c555d-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c555d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c555d-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="c555d-106">[out] Um buffer para armazenar o caminho para o diretório de histórico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c555d-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="c555d-107">[no, out] O comprimento do buffer.</span><span class="sxs-lookup"><span data-stu-id="c555d-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c555d-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c555d-108">Return Value</span></span>  
 <span data-ttu-id="c555d-109">Esse método retorna códigos de erro COM padrão, conforme definido no arquivo Winerror h, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="c555d-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="c555d-110">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="c555d-110">Return code</span></span>|<span data-ttu-id="c555d-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c555d-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c555d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c555d-112">S_OK</span></span>|<span data-ttu-id="c555d-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="c555d-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="c555d-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c555d-114">E_INVALIDARG</span></span>|<span data-ttu-id="c555d-115">`wzDir` ou `pdwSize` é nulo ou a versão de cadeia de caracteres está incorreta.</span><span class="sxs-lookup"><span data-stu-id="c555d-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c555d-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="c555d-116">Remarks</span></span>  
 <span data-ttu-id="c555d-117">Após a conclusão bem-sucedida, o `pdwSize` argumento é definido como o comprimento da cadeia de caracteres de caminho.</span><span class="sxs-lookup"><span data-stu-id="c555d-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c555d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c555d-118">Requirements</span></span>  
 <span data-ttu-id="c555d-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c555d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c555d-120">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c555d-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c555d-121">**Biblioteca:** Fusion e mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="c555d-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="c555d-122">Use Fusion em vez de mscorwks. dll para garantir que você direcione a versão correta do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c555d-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="c555d-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c555d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c555d-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c555d-124">See also</span></span>

- [<span data-ttu-id="c555d-125">Função CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="c555d-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="c555d-126">Função NukeDownloadedCache</span><span class="sxs-lookup"><span data-stu-id="c555d-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)
- [<span data-ttu-id="c555d-127">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="c555d-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
