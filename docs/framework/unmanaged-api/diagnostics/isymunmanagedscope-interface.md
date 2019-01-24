---
title: Interface ISymUnmanagedScope
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 965e8058d44ebb5dc87ade3b6025c6291a9c3bcd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492112"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="c3089-102">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="c3089-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="c3089-103">Representa um escopo léxico dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="c3089-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3089-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c3089-104">Methods</span></span>  
  
|<span data-ttu-id="c3089-105">Método</span><span class="sxs-lookup"><span data-stu-id="c3089-105">Method</span></span>|<span data-ttu-id="c3089-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3089-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c3089-107">Método GetChildren</span><span class="sxs-lookup"><span data-stu-id="c3089-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="c3089-108">Obtém o filho desse escopo.</span><span class="sxs-lookup"><span data-stu-id="c3089-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="c3089-109">Método GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="c3089-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="c3089-110">Obtém o deslocamento de fim para esse escopo.</span><span class="sxs-lookup"><span data-stu-id="c3089-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="c3089-111">Método GetLocalCount</span><span class="sxs-lookup"><span data-stu-id="c3089-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="c3089-112">Obtém uma contagem das variáveis locais definidas dentro desse escopo.</span><span class="sxs-lookup"><span data-stu-id="c3089-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="c3089-113">Método GetLocals</span><span class="sxs-lookup"><span data-stu-id="c3089-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="c3089-114">Obtém as variáveis locais definidas dentro desse escopo.</span><span class="sxs-lookup"><span data-stu-id="c3089-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="c3089-115">Método GetMethod</span><span class="sxs-lookup"><span data-stu-id="c3089-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="c3089-116">Obtém o método que contém esse escopo.</span><span class="sxs-lookup"><span data-stu-id="c3089-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="c3089-117">Método GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="c3089-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="c3089-118">Obtém os namespaces que estão sendo usados dentro desse escopo.</span><span class="sxs-lookup"><span data-stu-id="c3089-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="c3089-119">Método GetParent</span><span class="sxs-lookup"><span data-stu-id="c3089-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="c3089-120">Obtém o escopo pai desse escopo.</span><span class="sxs-lookup"><span data-stu-id="c3089-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="c3089-121">Método GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="c3089-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="c3089-122">Obtém o deslocamento de início para esse escopo.</span><span class="sxs-lookup"><span data-stu-id="c3089-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3089-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3089-123">Requirements</span></span>  
 <span data-ttu-id="c3089-124">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c3089-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3089-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3089-125">See also</span></span>
- [<span data-ttu-id="c3089-126">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="c3089-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="c3089-127">Interface ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="c3089-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
