---
title: Função CreateAssemblyNameObject
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd8609bedcea28c1cb8559d378b5e171f3ad568e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224987"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="d6053-102">Função CreateAssemblyNameObject</span><span class="sxs-lookup"><span data-stu-id="d6053-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="d6053-103">Obtém um ponteiro de interface para um [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instância que representa a identidade exclusiva do assembly com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d6053-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6053-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6053-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6053-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6053-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="d6053-106">[out] Retornado `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="d6053-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="d6053-107">[in] O nome do assembly para o qual criar o novo `IAssemblyName` instância.</span><span class="sxs-lookup"><span data-stu-id="d6053-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d6053-108">[in] Sinalizadores a serem passados para o construtor do objeto.</span><span class="sxs-lookup"><span data-stu-id="d6053-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d6053-109">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="d6053-109">[in] Reserved for future extensibility.</span></span> `pvReserved` <span data-ttu-id="d6053-110">deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="d6053-110">must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6053-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6053-111">Requirements</span></span>  
 <span data-ttu-id="d6053-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6053-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6053-113">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d6053-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d6053-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d6053-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="d6053-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d6053-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d6053-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6053-116">See also</span></span>

- [<span data-ttu-id="d6053-117">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="d6053-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="d6053-118">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="d6053-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
