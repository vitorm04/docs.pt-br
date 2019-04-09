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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d573264bb7a3cac02dd41afacaa2bc4a6f9e6dcd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207537"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="9de4a-102">Interface ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="9de4a-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="9de4a-103">Fornece métodos que obtêm informações sobre o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="9de4a-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="9de4a-104">Obtenha essa interface chamando `QueryInterface` em um objeto que implementa o [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="9de4a-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9de4a-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="9de4a-105">Methods</span></span>  
  
|<span data-ttu-id="9de4a-106">Método</span><span class="sxs-lookup"><span data-stu-id="9de4a-106">Method</span></span>|<span data-ttu-id="9de4a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9de4a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9de4a-108">Método GetHRESULT</span><span class="sxs-lookup"><span data-stu-id="9de4a-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="9de4a-109">Obtém o HRESULT.</span><span class="sxs-lookup"><span data-stu-id="9de4a-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="9de4a-110">Método GetSearchPath</span><span class="sxs-lookup"><span data-stu-id="9de4a-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="9de4a-111">Obtém o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="9de4a-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="9de4a-112">Método GetSearchPathLength</span><span class="sxs-lookup"><span data-stu-id="9de4a-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="9de4a-113">Obtém o comprimento do caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="9de4a-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9de4a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9de4a-114">Requirements</span></span>  
 <span data-ttu-id="9de4a-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9de4a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9de4a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9de4a-116">See also</span></span>

- [<span data-ttu-id="9de4a-117">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="9de4a-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
