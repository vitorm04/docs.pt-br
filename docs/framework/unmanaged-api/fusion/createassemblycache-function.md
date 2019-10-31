---
title: Função CreateAssemblyCache
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
ms.openlocfilehash: 5ef100680328e9ad6261bb9188d7509efa9ab479
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108862"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="52025-102">Função CreateAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="52025-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="52025-103">Obtém um ponteiro para uma nova instância [IAssemblyCache](iassemblycache-interface.md) que representa o cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="52025-103">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52025-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52025-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="52025-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="52025-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="52025-106">fora O ponteiro de `IAssemblyCache` retornado.</span><span class="sxs-lookup"><span data-stu-id="52025-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="52025-107">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="52025-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="52025-108">`dwReserved` deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="52025-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52025-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52025-109">Requirements</span></span>  
 <span data-ttu-id="52025-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52025-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52025-111">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="52025-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="52025-112">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="52025-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52025-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52025-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52025-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52025-114">See also</span></span>

- [<span data-ttu-id="52025-115">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="52025-115">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="52025-116">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="52025-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="52025-117">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="52025-117">Global Assembly Cache</span></span>](../../app-domains/gac.md)
