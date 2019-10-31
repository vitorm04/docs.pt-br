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
ms.openlocfilehash: 00345f6c95c67f0494aa721c662f56a9e98cdd7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108708"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="12e26-102">Função CreateAssemblyNameObject</span><span class="sxs-lookup"><span data-stu-id="12e26-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="12e26-103">Obtém um ponteiro de interface para uma instância de [IAssemblyName](iassemblyname-interface.md) que representa a identidade exclusiva do assembly com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="12e26-103">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12e26-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12e26-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="12e26-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12e26-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="12e26-106">fora O `IAssemblyName`retornado.</span><span class="sxs-lookup"><span data-stu-id="12e26-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="12e26-107">no O nome do assembly para o qual criar a nova instância de `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="12e26-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="12e26-108">no Sinalizadores a serem passados para o construtor de objeto.</span><span class="sxs-lookup"><span data-stu-id="12e26-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="12e26-109">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="12e26-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="12e26-110">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="12e26-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12e26-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12e26-111">Requirements</span></span>  
 <span data-ttu-id="12e26-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12e26-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12e26-113">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="12e26-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="12e26-114">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="12e26-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12e26-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12e26-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e26-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12e26-116">See also</span></span>

- [<span data-ttu-id="12e26-117">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="12e26-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="12e26-118">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="12e26-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
