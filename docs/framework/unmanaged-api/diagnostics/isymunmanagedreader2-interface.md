---
title: Interface ISymUnmanagedReader2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: a07c75e14244fb5bdf72ff2b0d344ae27672ef89
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448271"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="7e003-102">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="7e003-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="7e003-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span><span class="sxs-lookup"><span data-stu-id="7e003-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="7e003-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="7e003-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e003-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7e003-105">Methods</span></span>  
  
|<span data-ttu-id="7e003-106">Método</span><span class="sxs-lookup"><span data-stu-id="7e003-106">Method</span></span>|<span data-ttu-id="7e003-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e003-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e003-108">Método GetMethodByVersionPreRemap</span><span class="sxs-lookup"><span data-stu-id="7e003-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="7e003-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span><span class="sxs-lookup"><span data-stu-id="7e003-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="7e003-110">Método GetMethodsInDocument</span><span class="sxs-lookup"><span data-stu-id="7e003-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="7e003-111">Gets every method that has line information in the provided document.</span><span class="sxs-lookup"><span data-stu-id="7e003-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="7e003-112">Método GetSymAttributePreRemap</span><span class="sxs-lookup"><span data-stu-id="7e003-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="7e003-113">Gets a custom attribute based upon its name.</span><span class="sxs-lookup"><span data-stu-id="7e003-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7e003-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e003-114">Requirements</span></span>  
 <span data-ttu-id="7e003-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7e003-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e003-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e003-116">See also</span></span>

- [<span data-ttu-id="7e003-117">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="7e003-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="7e003-118">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="7e003-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
