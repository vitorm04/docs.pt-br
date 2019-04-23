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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ba81c208c4b49342c6a055e09ba898871db1851
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157596"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="267f9-102">Interface ISymUnmanagedSourceServerModule</span><span class="sxs-lookup"><span data-stu-id="267f9-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="267f9-103">Fornece dados de servidor de origem para um módulo.</span><span class="sxs-lookup"><span data-stu-id="267f9-103">Provides source server data for a module.</span></span> <span data-ttu-id="267f9-104">Obtenha essa interface chamando `QueryInterface` em um objeto que implementa o [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="267f9-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="267f9-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="267f9-105">Methods</span></span>  
  
|<span data-ttu-id="267f9-106">Método</span><span class="sxs-lookup"><span data-stu-id="267f9-106">Method</span></span>|<span data-ttu-id="267f9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="267f9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="267f9-108">Método GetSourceServerData</span><span class="sxs-lookup"><span data-stu-id="267f9-108">GetSourceServerData Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="267f9-109">Retorna os dados do servidor de origem para o módulo.</span><span class="sxs-lookup"><span data-stu-id="267f9-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="267f9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="267f9-110">Requirements</span></span>  
 <span data-ttu-id="267f9-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="267f9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="267f9-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="267f9-112">See also</span></span>

- [<span data-ttu-id="267f9-113">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="267f9-113">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
