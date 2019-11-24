---
title: Interface ISymUnmanagedSymbolSearchInfo
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
ms.openlocfilehash: d7371361b074454e8aa359c49b964193c12f3034
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446153"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="b9d19-102">Interface ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="b9d19-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="b9d19-103">Provides methods that get information about the search path.</span><span class="sxs-lookup"><span data-stu-id="b9d19-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="b9d19-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="b9d19-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9d19-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b9d19-105">Methods</span></span>  
  
|<span data-ttu-id="b9d19-106">Método</span><span class="sxs-lookup"><span data-stu-id="b9d19-106">Method</span></span>|<span data-ttu-id="b9d19-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9d19-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9d19-108">Método GetHRESULT</span><span class="sxs-lookup"><span data-stu-id="b9d19-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="b9d19-109">Gets the HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b9d19-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="b9d19-110">Método GetSearchPath</span><span class="sxs-lookup"><span data-stu-id="b9d19-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="b9d19-111">Gets the search path.</span><span class="sxs-lookup"><span data-stu-id="b9d19-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="b9d19-112">Método GetSearchPathLength</span><span class="sxs-lookup"><span data-stu-id="b9d19-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="b9d19-113">Gets the search path length.</span><span class="sxs-lookup"><span data-stu-id="b9d19-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b9d19-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9d19-114">Requirements</span></span>  
 <span data-ttu-id="b9d19-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b9d19-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d19-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9d19-116">See also</span></span>

- [<span data-ttu-id="b9d19-117">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="b9d19-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
