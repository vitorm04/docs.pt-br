---
title: Interface ISymUnmanagedENCUpdate
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
ms.openlocfilehash: f3305a7bb003fc50f772f1100f8a17d385e4d5fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449009"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="5e446-102">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="5e446-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="5e446-103">Provides functions for the Edit and Continue feature.</span><span class="sxs-lookup"><span data-stu-id="5e446-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e446-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5e446-104">Methods</span></span>  
  
|<span data-ttu-id="5e446-105">Método</span><span class="sxs-lookup"><span data-stu-id="5e446-105">Method</span></span>|<span data-ttu-id="5e446-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e446-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e446-107">Método GetLocalVariableCount</span><span class="sxs-lookup"><span data-stu-id="5e446-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="5e446-108">Gets the number of local variables.</span><span class="sxs-lookup"><span data-stu-id="5e446-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="5e446-109">Método GetLocalVariables</span><span class="sxs-lookup"><span data-stu-id="5e446-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="5e446-110">Gets the local variables.</span><span class="sxs-lookup"><span data-stu-id="5e446-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="5e446-111">Método InitializeForEnc</span><span class="sxs-lookup"><span data-stu-id="5e446-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="5e446-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="5e446-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="5e446-113">Método UpdateMethodLines</span><span class="sxs-lookup"><span data-stu-id="5e446-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="5e446-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span><span class="sxs-lookup"><span data-stu-id="5e446-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="5e446-115">A delta for each statement is allowed.</span><span class="sxs-lookup"><span data-stu-id="5e446-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="5e446-116">Método UpdateSymbolStore2</span><span class="sxs-lookup"><span data-stu-id="5e446-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="5e446-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span><span class="sxs-lookup"><span data-stu-id="5e446-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="5e446-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span><span class="sxs-lookup"><span data-stu-id="5e446-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e446-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e446-119">Requirements</span></span>  
 <span data-ttu-id="5e446-120">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5e446-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e446-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e446-121">See also</span></span>

- [<span data-ttu-id="5e446-122">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="5e446-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
