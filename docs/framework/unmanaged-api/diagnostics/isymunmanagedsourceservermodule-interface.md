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
ms.openlocfilehash: d90a55b53ba00540137e44fc190790c4710903e3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610789"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="99306-102">Interface ISymUnmanagedSourceServerModule</span><span class="sxs-lookup"><span data-stu-id="99306-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="99306-103">Fornece dados do servidor de origem para um módulo.</span><span class="sxs-lookup"><span data-stu-id="99306-103">Provides source server data for a module.</span></span> <span data-ttu-id="99306-104">Obtenha essa interface chamando `QueryInterface` em um objeto que implementa a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="99306-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99306-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="99306-105">Methods</span></span>  
  
|<span data-ttu-id="99306-106">Método</span><span class="sxs-lookup"><span data-stu-id="99306-106">Method</span></span>|<span data-ttu-id="99306-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="99306-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99306-108">Método GetSourceServerData</span><span class="sxs-lookup"><span data-stu-id="99306-108">GetSourceServerData Method</span></span>](isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="99306-109">Retorna os dados do servidor de origem para o módulo.</span><span class="sxs-lookup"><span data-stu-id="99306-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99306-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="99306-110">Requirements</span></span>  
 <span data-ttu-id="99306-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="99306-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99306-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="99306-112">See also</span></span>

- [<span data-ttu-id="99306-113">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="99306-113">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
