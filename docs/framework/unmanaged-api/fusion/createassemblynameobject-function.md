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
ms.openlocfilehash: ed26df6580aeaf2936bd50c9f1855a08ac68b90b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778428"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="f27ef-102">Função CreateAssemblyNameObject</span><span class="sxs-lookup"><span data-stu-id="f27ef-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="f27ef-103">Obtém um ponteiro de interface para um [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instância que representa a identidade exclusiva do assembly com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="f27ef-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f27ef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f27ef-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f27ef-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f27ef-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="f27ef-106">[out] Retornado `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="f27ef-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="f27ef-107">[in] O nome do assembly para o qual criar o novo `IAssemblyName` instância.</span><span class="sxs-lookup"><span data-stu-id="f27ef-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f27ef-108">[in] Sinalizadores a serem passados para o construtor do objeto.</span><span class="sxs-lookup"><span data-stu-id="f27ef-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f27ef-109">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="f27ef-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f27ef-110">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="f27ef-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f27ef-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f27ef-111">Requirements</span></span>  
 <span data-ttu-id="f27ef-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f27ef-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f27ef-113">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f27ef-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f27ef-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f27ef-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f27ef-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f27ef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f27ef-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f27ef-116">See also</span></span>

- [<span data-ttu-id="f27ef-117">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="f27ef-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="f27ef-118">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="f27ef-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
