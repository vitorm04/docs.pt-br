---
title: Função GetAssemblyIdentityFromFile
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dfb0b404413351761d269c800be19e75acfb41f
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258687"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="1b17b-102">Função GetAssemblyIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="1b17b-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="1b17b-103">Obtém um ponteiro para um `IUnknown` objeto com especificado `IID` no assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="1b17b-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b17b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b17b-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b17b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b17b-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="1b17b-106">[in] Um caminho válido para o assembly solicitado.</span><span class="sxs-lookup"><span data-stu-id="1b17b-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="1b17b-107">[in] O `IID` da interface para retornar.</span><span class="sxs-lookup"><span data-stu-id="1b17b-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="1b17b-108">[out] O ponteiro de interface retornada.</span><span class="sxs-lookup"><span data-stu-id="1b17b-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b17b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b17b-109">Requirements</span></span>  
 <span data-ttu-id="1b17b-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b17b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b17b-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="1b17b-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1b17b-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b17b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b17b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b17b-113">See Also</span></span>  
 [<span data-ttu-id="1b17b-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="1b17b-114">IUnknown</span></span>](/cpp/atl/iunknown)  
 [<span data-ttu-id="1b17b-115">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="1b17b-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
