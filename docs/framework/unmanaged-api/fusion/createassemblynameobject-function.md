---
title: "Função CreateAssemblyNameObject"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d2616bd7aee878ebbc1d196cb1ac5f90ae7bd04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="f2dc2-102">Função CreateAssemblyNameObject</span><span class="sxs-lookup"><span data-stu-id="f2dc2-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="f2dc2-103">Obtém um ponteiro de interface para um [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instância que representa a identidade exclusiva do assembly com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="f2dc2-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2dc2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2dc2-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2dc2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2dc2-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="f2dc2-106">[out] Retornado `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="f2dc2-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="f2dc2-107">[in] O nome do assembly para o qual criar o novo `IAssemblyName` instância.</span><span class="sxs-lookup"><span data-stu-id="f2dc2-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f2dc2-108">[in] Sinalizadores para passar para o construtor do objeto.</span><span class="sxs-lookup"><span data-stu-id="f2dc2-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f2dc2-109">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="f2dc2-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f2dc2-110">`pvReserved`deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="f2dc2-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2dc2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2dc2-111">Requirements</span></span>  
 <span data-ttu-id="f2dc2-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2dc2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2dc2-113">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f2dc2-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f2dc2-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f2dc2-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2dc2-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2dc2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2dc2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2dc2-116">See Also</span></span>  
 [<span data-ttu-id="f2dc2-117">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="f2dc2-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="f2dc2-118">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="f2dc2-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
