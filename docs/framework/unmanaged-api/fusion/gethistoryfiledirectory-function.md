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
ms.openlocfilehash: 21742881c5aef7384be318297aa3432411c3d57c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479273"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="f59f7-102">Função GetHistoryFileDirectory</span><span class="sxs-lookup"><span data-stu-id="f59f7-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="f59f7-103">Recupera o caminho do diretório de histórico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f59f7-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f59f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f59f7-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f59f7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f59f7-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="f59f7-106">[out] Um buffer para armazenar o caminho para o diretório de histórico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f59f7-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="f59f7-107">[no, out] O comprimento do buffer.</span><span class="sxs-lookup"><span data-stu-id="f59f7-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f59f7-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f59f7-108">Return Value</span></span>  
 <span data-ttu-id="f59f7-109">Esse método retorna códigos de erro COM padrão, conforme definido no arquivo Winerror h, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="f59f7-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="f59f7-110">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="f59f7-110">Return code</span></span>|<span data-ttu-id="f59f7-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f59f7-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f59f7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f59f7-112">S_OK</span></span>|<span data-ttu-id="f59f7-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="f59f7-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="f59f7-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f59f7-114">E_INVALIDARG</span></span>|<span data-ttu-id="f59f7-115">`wzDir` ou `pdwSize` é nulo ou a versão de cadeia de caracteres está incorreta.</span><span class="sxs-lookup"><span data-stu-id="f59f7-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f59f7-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="f59f7-116">Remarks</span></span>  
 <span data-ttu-id="f59f7-117">Após a conclusão bem-sucedida, o `pdwSize` argumento é definido como o comprimento da cadeia de caracteres de caminho.</span><span class="sxs-lookup"><span data-stu-id="f59f7-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f59f7-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f59f7-118">Requirements</span></span>  
 <span data-ttu-id="f59f7-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f59f7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f59f7-120">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f59f7-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f59f7-121">**Biblioteca:** Fusion e mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="f59f7-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="f59f7-122">Use Fusion em vez de mscorwks. dll para garantir que você direcione a versão correta do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f59f7-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="f59f7-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f59f7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f59f7-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f59f7-124">See also</span></span>
- [<span data-ttu-id="f59f7-125">Função CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="f59f7-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="f59f7-126">Função NukeDownloadedCache</span><span class="sxs-lookup"><span data-stu-id="f59f7-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)
- [<span data-ttu-id="f59f7-127">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="f59f7-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
