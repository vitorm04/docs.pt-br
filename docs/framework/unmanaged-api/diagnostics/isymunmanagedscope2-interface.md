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
ms.openlocfilehash: 886ba693183a6b99eb03635e95a9661d105de40e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610854"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="e4d82-102">Interface ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="e4d82-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="e4d82-103">Representa um escopo léxico dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="e4d82-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="e4d82-104">Essa interface estende a interface [ISymUnmanagedScope](isymunmanagedscope-interface.md) com métodos que obtêm informações sobre constantes definidas no escopo.</span><span class="sxs-lookup"><span data-stu-id="e4d82-104">This interface extends the [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4d82-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e4d82-105">Methods</span></span>  
  
|<span data-ttu-id="e4d82-106">Método</span><span class="sxs-lookup"><span data-stu-id="e4d82-106">Method</span></span>|<span data-ttu-id="e4d82-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4d82-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4d82-108">Método GetConstantCount</span><span class="sxs-lookup"><span data-stu-id="e4d82-108">GetConstantCount Method</span></span>](isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="e4d82-109">Obtém uma contagem das constantes definidas neste escopo.</span><span class="sxs-lookup"><span data-stu-id="e4d82-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="e4d82-110">Método GetConstants</span><span class="sxs-lookup"><span data-stu-id="e4d82-110">GetConstants Method</span></span>](isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="e4d82-111">Obtém as constantes locais definidas neste escopo.</span><span class="sxs-lookup"><span data-stu-id="e4d82-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4d82-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4d82-112">Requirements</span></span>  
 <span data-ttu-id="e4d82-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e4d82-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4d82-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="e4d82-114">See also</span></span>

- [<span data-ttu-id="e4d82-115">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="e4d82-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="e4d82-116">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="e4d82-116">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
