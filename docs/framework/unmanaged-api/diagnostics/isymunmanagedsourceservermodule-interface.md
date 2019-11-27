---
title: Interface ISymUnmanagedSourceServerModule
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule
helpviewer_keywords:
- ISymUnmanagedSourceServerModule interface [.NET Framework debugging]
ms.assetid: a19b23bd-2061-476e-b67d-252f57404f8b
topic_type:
- apiref
ms.openlocfilehash: 9eac87d7627f502b13d805b8c5656e01ac578e7f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446200"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="269df-102">Interface ISymUnmanagedSourceServerModule</span><span class="sxs-lookup"><span data-stu-id="269df-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="269df-103">Fornece dados do servidor de origem para um módulo.</span><span class="sxs-lookup"><span data-stu-id="269df-103">Provides source server data for a module.</span></span> <span data-ttu-id="269df-104">Obtenha essa interface chamando `QueryInterface` em um objeto que implementa a interface [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="269df-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="269df-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="269df-105">Methods</span></span>  
  
|<span data-ttu-id="269df-106">Método</span><span class="sxs-lookup"><span data-stu-id="269df-106">Method</span></span>|<span data-ttu-id="269df-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="269df-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="269df-108">Método GetSourceServerData</span><span class="sxs-lookup"><span data-stu-id="269df-108">GetSourceServerData Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="269df-109">Retorna os dados do servidor de origem para o módulo.</span><span class="sxs-lookup"><span data-stu-id="269df-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="269df-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="269df-110">Requirements</span></span>  
 <span data-ttu-id="269df-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="269df-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="269df-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="269df-112">See also</span></span>

- [<span data-ttu-id="269df-113">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="269df-113">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
