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
ms.openlocfilehash: 967511238dceb752ab30ce10dcaba8b65f4dd9fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="31722-102">Interface ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="31722-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="31722-103">Fornece métodos que obtêm informações sobre o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="31722-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="31722-104">Obter essa interface chamando `QueryInterface` em um objeto que implementa o [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="31722-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31722-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="31722-105">Methods</span></span>  
  
|<span data-ttu-id="31722-106">Método</span><span class="sxs-lookup"><span data-stu-id="31722-106">Method</span></span>|<span data-ttu-id="31722-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="31722-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31722-108">Método GetHRESULT</span><span class="sxs-lookup"><span data-stu-id="31722-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="31722-109">Obtém o HRESULT.</span><span class="sxs-lookup"><span data-stu-id="31722-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="31722-110">Método GetSearchPath</span><span class="sxs-lookup"><span data-stu-id="31722-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="31722-111">Obtém o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="31722-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="31722-112">Método GetSearchPathLength</span><span class="sxs-lookup"><span data-stu-id="31722-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="31722-113">Obtém o comprimento do caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="31722-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="31722-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31722-114">Requirements</span></span>  
 <span data-ttu-id="31722-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="31722-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31722-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31722-116">See Also</span></span>  
 [<span data-ttu-id="31722-117">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="31722-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
