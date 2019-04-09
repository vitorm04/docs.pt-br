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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127394"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="b5348-102">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="b5348-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="b5348-103">Representa um gravador de símbolo e fornece métodos para definir pontos de sequência, documentos, escopos léxicos e variáveis.</span><span class="sxs-lookup"><span data-stu-id="b5348-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="b5348-104">Essa interface estende o [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="b5348-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b5348-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b5348-105">Methods</span></span>  
  
|<span data-ttu-id="b5348-106">Método</span><span class="sxs-lookup"><span data-stu-id="b5348-106">Method</span></span>|<span data-ttu-id="b5348-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5348-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5348-108">Método DefineConstant2</span><span class="sxs-lookup"><span data-stu-id="b5348-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="b5348-109">Define um nome para um valor constante.</span><span class="sxs-lookup"><span data-stu-id="b5348-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="b5348-110">Método DefineGlobalVariable2</span><span class="sxs-lookup"><span data-stu-id="b5348-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="b5348-111">Define uma única variável global.</span><span class="sxs-lookup"><span data-stu-id="b5348-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="b5348-112">Método DefineLocalVariable2</span><span class="sxs-lookup"><span data-stu-id="b5348-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="b5348-113">Define uma única variável no escopo léxico atual.</span><span class="sxs-lookup"><span data-stu-id="b5348-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5348-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5348-114">Requirements</span></span>  
 <span data-ttu-id="b5348-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b5348-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5348-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5348-116">See also</span></span>

- [<span data-ttu-id="b5348-117">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="b5348-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="b5348-118">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="b5348-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="b5348-119">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="b5348-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
