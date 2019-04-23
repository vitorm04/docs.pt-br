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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207537"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="d03ec-102">Interface ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="d03ec-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="d03ec-103">Fornece métodos que obtêm informações sobre o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="d03ec-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="d03ec-104">Obtenha essa interface chamando `QueryInterface` em um objeto que implementa o [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="d03ec-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d03ec-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d03ec-105">Methods</span></span>  
  
|<span data-ttu-id="d03ec-106">Método</span><span class="sxs-lookup"><span data-stu-id="d03ec-106">Method</span></span>|<span data-ttu-id="d03ec-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d03ec-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d03ec-108">Método GetHRESULT</span><span class="sxs-lookup"><span data-stu-id="d03ec-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="d03ec-109">Obtém o HRESULT.</span><span class="sxs-lookup"><span data-stu-id="d03ec-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="d03ec-110">Método GetSearchPath</span><span class="sxs-lookup"><span data-stu-id="d03ec-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="d03ec-111">Obtém o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="d03ec-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="d03ec-112">Método GetSearchPathLength</span><span class="sxs-lookup"><span data-stu-id="d03ec-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="d03ec-113">Obtém o comprimento do caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="d03ec-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d03ec-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d03ec-114">Requirements</span></span>  
 <span data-ttu-id="d03ec-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d03ec-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d03ec-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d03ec-116">See also</span></span>

- [<span data-ttu-id="d03ec-117">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="d03ec-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
