---
title: Interface ISymUnmanagedSymbolSearchInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo
helpviewer_keywords: ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 441330471906a891646ad55eb73ec25b44800cbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="57bcf-102">Interface ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="57bcf-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="57bcf-103">Fornece métodos que obtêm informações sobre o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="57bcf-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="57bcf-104">Obter essa interface chamando `QueryInterface` em um objeto que implementa o [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="57bcf-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57bcf-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="57bcf-105">Methods</span></span>  
  
|<span data-ttu-id="57bcf-106">Método</span><span class="sxs-lookup"><span data-stu-id="57bcf-106">Method</span></span>|<span data-ttu-id="57bcf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="57bcf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57bcf-108">Método GetHRESULT</span><span class="sxs-lookup"><span data-stu-id="57bcf-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="57bcf-109">Obtém o HRESULT.</span><span class="sxs-lookup"><span data-stu-id="57bcf-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="57bcf-110">Método GetSearchPath</span><span class="sxs-lookup"><span data-stu-id="57bcf-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="57bcf-111">Obtém o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="57bcf-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="57bcf-112">Método GetSearchPathLength</span><span class="sxs-lookup"><span data-stu-id="57bcf-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="57bcf-113">Obtém o comprimento do caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="57bcf-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57bcf-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57bcf-114">Requirements</span></span>  
 <span data-ttu-id="57bcf-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="57bcf-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57bcf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57bcf-116">See Also</span></span>  
 [<span data-ttu-id="57bcf-117">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="57bcf-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
