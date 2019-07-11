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
ms.openlocfilehash: 581c675cfb69503e6366471a469ffed1a2d13b1a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745233"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="ca036-102">Função GetAssemblyIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="ca036-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="ca036-103">Obtém um ponteiro para um `IUnknown` objeto com especificado `IID` no assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="ca036-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca036-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca036-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca036-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca036-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="ca036-106">[in] Um caminho válido para o assembly solicitado.</span><span class="sxs-lookup"><span data-stu-id="ca036-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="ca036-107">[in] O `IID` da interface para retornar.</span><span class="sxs-lookup"><span data-stu-id="ca036-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="ca036-108">[out] O ponteiro de interface retornada.</span><span class="sxs-lookup"><span data-stu-id="ca036-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca036-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca036-109">Requirements</span></span>  
 <span data-ttu-id="ca036-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca036-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca036-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ca036-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ca036-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca036-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca036-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca036-113">See also</span></span>

- [<span data-ttu-id="ca036-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="ca036-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="ca036-115">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="ca036-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
