---
title: Interface ISymUnmanagedWriter2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97df6d6ec9a446e89eef8a9f8a5e5e8ddc85c0f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127394"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="88f4c-102">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="88f4c-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="88f4c-103">Representa um gravador de símbolo e fornece métodos para definir pontos de sequência, documentos, escopos léxicos e variáveis.</span><span class="sxs-lookup"><span data-stu-id="88f4c-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="88f4c-104">Essa interface estende o [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="88f4c-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88f4c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="88f4c-105">Methods</span></span>  
  
|<span data-ttu-id="88f4c-106">Método</span><span class="sxs-lookup"><span data-stu-id="88f4c-106">Method</span></span>|<span data-ttu-id="88f4c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="88f4c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88f4c-108">Método DefineConstant2</span><span class="sxs-lookup"><span data-stu-id="88f4c-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="88f4c-109">Define um nome para um valor constante.</span><span class="sxs-lookup"><span data-stu-id="88f4c-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="88f4c-110">Método DefineGlobalVariable2</span><span class="sxs-lookup"><span data-stu-id="88f4c-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="88f4c-111">Define uma única variável global.</span><span class="sxs-lookup"><span data-stu-id="88f4c-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="88f4c-112">Método DefineLocalVariable2</span><span class="sxs-lookup"><span data-stu-id="88f4c-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="88f4c-113">Define uma única variável no escopo léxico atual.</span><span class="sxs-lookup"><span data-stu-id="88f4c-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88f4c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88f4c-114">Requirements</span></span>  
 <span data-ttu-id="88f4c-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="88f4c-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f4c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88f4c-116">See also</span></span>

- [<span data-ttu-id="88f4c-117">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="88f4c-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="88f4c-118">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="88f4c-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="88f4c-119">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="88f4c-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
