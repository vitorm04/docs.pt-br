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
ms.openlocfilehash: 4f5dd25ec2a6a1b0b5d6266c3d8e728bd128a9ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697752"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="65d83-102">Função GetAssemblyIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="65d83-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="65d83-103">Obtém um ponteiro para um `IUnknown` objeto com especificado `IID` no assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="65d83-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65d83-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65d83-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="65d83-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65d83-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="65d83-106">[in] Um caminho válido para o assembly solicitado.</span><span class="sxs-lookup"><span data-stu-id="65d83-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="65d83-107">[in] O `IID` da interface para retornar.</span><span class="sxs-lookup"><span data-stu-id="65d83-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="65d83-108">[out] O ponteiro de interface retornada.</span><span class="sxs-lookup"><span data-stu-id="65d83-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65d83-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65d83-109">Requirements</span></span>  
 <span data-ttu-id="65d83-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65d83-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65d83-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="65d83-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="65d83-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65d83-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d83-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65d83-113">See also</span></span>

- [<span data-ttu-id="65d83-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="65d83-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="65d83-115">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="65d83-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
