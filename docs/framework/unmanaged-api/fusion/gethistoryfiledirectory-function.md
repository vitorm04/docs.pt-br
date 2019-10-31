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
ms.openlocfilehash: 1aabfad14ee2eb35916bbf115631602276cd1fc3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109888"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="31f67-102">Função GetHistoryFileDirectory</span><span class="sxs-lookup"><span data-stu-id="31f67-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="31f67-103">Recupera o caminho do diretório de histórico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="31f67-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31f67-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31f67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31f67-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="31f67-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="31f67-106">fora Um buffer para manter o caminho para o diretório de histórico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="31f67-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="31f67-107">[entrada, saída] O comprimento do buffer.</span><span class="sxs-lookup"><span data-stu-id="31f67-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31f67-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="31f67-108">Return Value</span></span>  
 <span data-ttu-id="31f67-109">Esse método retorna códigos de erro COM padrão, conforme definido no arquivo WinError. h, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="31f67-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="31f67-110">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="31f67-110">Return code</span></span>|<span data-ttu-id="31f67-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="31f67-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="31f67-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="31f67-112">S_OK</span></span>|<span data-ttu-id="31f67-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="31f67-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="31f67-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="31f67-114">E_INVALIDARG</span></span>|<span data-ttu-id="31f67-115">`wzDir` ou `pdwSize` é nulo ou a cadeia de caracteres da versão está incorreta.</span><span class="sxs-lookup"><span data-stu-id="31f67-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31f67-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="31f67-116">Remarks</span></span>  
 <span data-ttu-id="31f67-117">Após a conclusão bem-sucedida, o argumento `pdwSize` é definido como o comprimento da cadeia de caracteres do caminho.</span><span class="sxs-lookup"><span data-stu-id="31f67-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31f67-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31f67-118">Requirements</span></span>  
 <span data-ttu-id="31f67-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31f67-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31f67-120">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="31f67-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="31f67-121">**Biblioteca:** Fusion. dll e mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="31f67-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="31f67-122">Use Fusion. dll em vez de mscorwks. dll para garantir que você direcione a versão correta do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="31f67-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="31f67-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31f67-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f67-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31f67-124">See also</span></span>

- [<span data-ttu-id="31f67-125">Função CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="31f67-125">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="31f67-126">Função NukeDownloadedCache</span><span class="sxs-lookup"><span data-stu-id="31f67-126">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)
- [<span data-ttu-id="31f67-127">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="31f67-127">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
