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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0109b25b1cdc42204fc4873577e495641c4ec4fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131450"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="65cb9-102">Interface ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="65cb9-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="65cb9-103">Representa um escopo léxico dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="65cb9-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="65cb9-104">Essa interface estende o [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface com métodos que obtêm informações sobre constantes definidas dentro do escopo.</span><span class="sxs-lookup"><span data-stu-id="65cb9-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65cb9-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="65cb9-105">Methods</span></span>  
  
|<span data-ttu-id="65cb9-106">Método</span><span class="sxs-lookup"><span data-stu-id="65cb9-106">Method</span></span>|<span data-ttu-id="65cb9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="65cb9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65cb9-108">Método GetConstantCount</span><span class="sxs-lookup"><span data-stu-id="65cb9-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="65cb9-109">Obtém uma contagem das constantes definidas dentro desse escopo.</span><span class="sxs-lookup"><span data-stu-id="65cb9-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="65cb9-110">Método GetConstants</span><span class="sxs-lookup"><span data-stu-id="65cb9-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="65cb9-111">Obtém as constantes locais definidas dentro desse escopo.</span><span class="sxs-lookup"><span data-stu-id="65cb9-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65cb9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65cb9-112">Requirements</span></span>  
 <span data-ttu-id="65cb9-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="65cb9-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65cb9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65cb9-114">See also</span></span>

- [<span data-ttu-id="65cb9-115">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="65cb9-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="65cb9-116">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="65cb9-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
