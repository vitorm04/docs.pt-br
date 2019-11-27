---
title: Interface ISymUnmanagedScope2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
ms.openlocfilehash: 3374097c8d343fed6badf046742ca556d2a92f3e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446221"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="206a5-102">Interface ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="206a5-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="206a5-103">Representa um escopo léxico dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="206a5-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="206a5-104">Essa interface estende a interface [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) com métodos que obtêm informações sobre constantes definidas no escopo.</span><span class="sxs-lookup"><span data-stu-id="206a5-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="206a5-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="206a5-105">Methods</span></span>  
  
|<span data-ttu-id="206a5-106">Método</span><span class="sxs-lookup"><span data-stu-id="206a5-106">Method</span></span>|<span data-ttu-id="206a5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="206a5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="206a5-108">Método GetConstantCount</span><span class="sxs-lookup"><span data-stu-id="206a5-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="206a5-109">Obtém uma contagem das constantes definidas neste escopo.</span><span class="sxs-lookup"><span data-stu-id="206a5-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="206a5-110">Método GetConstants</span><span class="sxs-lookup"><span data-stu-id="206a5-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="206a5-111">Obtém as constantes locais definidas neste escopo.</span><span class="sxs-lookup"><span data-stu-id="206a5-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="206a5-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="206a5-112">Requirements</span></span>  
 <span data-ttu-id="206a5-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="206a5-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="206a5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="206a5-114">See also</span></span>

- [<span data-ttu-id="206a5-115">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="206a5-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="206a5-116">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="206a5-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
