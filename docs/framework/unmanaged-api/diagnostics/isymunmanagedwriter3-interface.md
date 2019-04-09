---
title: Interface ISymUnmanagedWriter3
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e26d79a5b597b8585f2fffd7f3945f00832ca134
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138444"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="dbd39-102">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="dbd39-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="dbd39-103">Representa um gravador de símbolo e fornece métodos para definir pontos de sequência, documentos, escopos léxicos e variáveis.</span><span class="sxs-lookup"><span data-stu-id="dbd39-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="dbd39-104">Essa interface estende o [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="dbd39-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dbd39-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="dbd39-105">Methods</span></span>  
  
|<span data-ttu-id="dbd39-106">Método</span><span class="sxs-lookup"><span data-stu-id="dbd39-106">Method</span></span>|<span data-ttu-id="dbd39-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbd39-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dbd39-108">Método Commit</span><span class="sxs-lookup"><span data-stu-id="dbd39-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="dbd39-109">Confirma as alterações gravadas no fluxo até o momento.</span><span class="sxs-lookup"><span data-stu-id="dbd39-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="dbd39-110">Método OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="dbd39-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="dbd39-111">Abre um método e fornece seu deslocamento de seção real na imagem.</span><span class="sxs-lookup"><span data-stu-id="dbd39-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dbd39-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dbd39-112">Requirements</span></span>  
 <span data-ttu-id="dbd39-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dbd39-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd39-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbd39-114">See also</span></span>

- [<span data-ttu-id="dbd39-115">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="dbd39-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="dbd39-116">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="dbd39-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="dbd39-117">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="dbd39-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
