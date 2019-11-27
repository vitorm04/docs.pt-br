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
ms.openlocfilehash: 8da4da38d23ed65a0fdc44a0f919ee8cad2fe18e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446269"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="07345-102">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="07345-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="07345-103">Representa um escopo léxico dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="07345-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="07345-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="07345-104">Methods</span></span>  
  
|<span data-ttu-id="07345-105">Método</span><span class="sxs-lookup"><span data-stu-id="07345-105">Method</span></span>|<span data-ttu-id="07345-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="07345-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="07345-107">Método GetChildren</span><span class="sxs-lookup"><span data-stu-id="07345-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="07345-108">Obtém os filhos deste escopo.</span><span class="sxs-lookup"><span data-stu-id="07345-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="07345-109">Método GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="07345-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="07345-110">Obtém o deslocamento de fim deste escopo.</span><span class="sxs-lookup"><span data-stu-id="07345-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="07345-111">Método GetLocalCount</span><span class="sxs-lookup"><span data-stu-id="07345-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="07345-112">Obtém uma contagem das variáveis locais definidas neste escopo.</span><span class="sxs-lookup"><span data-stu-id="07345-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="07345-113">Método GetLocals</span><span class="sxs-lookup"><span data-stu-id="07345-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="07345-114">Obtém as variáveis locais definidas nesse escopo.</span><span class="sxs-lookup"><span data-stu-id="07345-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="07345-115">Método GetMethod</span><span class="sxs-lookup"><span data-stu-id="07345-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="07345-116">Obtém o método que contém esse escopo.</span><span class="sxs-lookup"><span data-stu-id="07345-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="07345-117">Método GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="07345-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="07345-118">Obtém os namespaces que estão sendo usados nesse escopo.</span><span class="sxs-lookup"><span data-stu-id="07345-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="07345-119">Método GetParent</span><span class="sxs-lookup"><span data-stu-id="07345-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="07345-120">Obtém o escopo pai deste escopo.</span><span class="sxs-lookup"><span data-stu-id="07345-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="07345-121">Método GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="07345-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="07345-122">Obtém o deslocamento inicial para este escopo.</span><span class="sxs-lookup"><span data-stu-id="07345-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07345-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07345-123">Requirements</span></span>  
 <span data-ttu-id="07345-124">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="07345-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07345-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07345-125">See also</span></span>

- [<span data-ttu-id="07345-126">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="07345-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="07345-127">Interface ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="07345-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
