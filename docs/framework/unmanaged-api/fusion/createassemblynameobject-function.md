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
ms.openlocfilehash: fb53014a28fb291b8463535addfb61e62d32d7d6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795362"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="c63ff-102">Função CreateAssemblyNameObject</span><span class="sxs-lookup"><span data-stu-id="c63ff-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="c63ff-103">Obtém um ponteiro de interface para uma instância de [IAssemblyName](iassemblyname-interface.md) que representa a identidade exclusiva do assembly com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="c63ff-103">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c63ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c63ff-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c63ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c63ff-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="c63ff-106">fora O retornado `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="c63ff-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="c63ff-107">no O nome do assembly para o qual criar a nova `IAssemblyName` instância.</span><span class="sxs-lookup"><span data-stu-id="c63ff-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c63ff-108">no Sinalizadores a serem passados para o construtor de objeto.</span><span class="sxs-lookup"><span data-stu-id="c63ff-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="c63ff-109">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="c63ff-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="c63ff-110">`pvReserved`deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="c63ff-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c63ff-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c63ff-111">Requirements</span></span>  
 <span data-ttu-id="c63ff-112">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c63ff-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c63ff-113">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c63ff-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c63ff-114">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c63ff-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c63ff-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c63ff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c63ff-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c63ff-116">See also</span></span>

- [<span data-ttu-id="c63ff-117">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="c63ff-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="c63ff-118">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="c63ff-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
