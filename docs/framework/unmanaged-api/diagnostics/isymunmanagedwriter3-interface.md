---
title: Interface ISymUnmanagedWriter3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter3
helpviewer_keywords: ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3babf8b3a54f07ac4eb14e326f66c70834953dfe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="cdb3d-102">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="cdb3d-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="cdb3d-103">Representa um gravador de símbolo e fornece métodos para definir documentos, pontos de sequência, escopos de léxicos e variáveis.</span><span class="sxs-lookup"><span data-stu-id="cdb3d-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="cdb3d-104">Essa interface estende o [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="cdb3d-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cdb3d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="cdb3d-105">Methods</span></span>  
  
|<span data-ttu-id="cdb3d-106">Método</span><span class="sxs-lookup"><span data-stu-id="cdb3d-106">Method</span></span>|<span data-ttu-id="cdb3d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdb3d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cdb3d-108">Método Commit</span><span class="sxs-lookup"><span data-stu-id="cdb3d-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="cdb3d-109">Confirma as alterações até o momento gravadas no fluxo.</span><span class="sxs-lookup"><span data-stu-id="cdb3d-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="cdb3d-110">Método OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="cdb3d-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="cdb3d-111">Abre um método e fornece seu deslocamento real de seção na imagem.</span><span class="sxs-lookup"><span data-stu-id="cdb3d-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cdb3d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cdb3d-112">Requirements</span></span>  
 <span data-ttu-id="cdb3d-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cdb3d-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb3d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdb3d-114">See Also</span></span>  
 [<span data-ttu-id="cdb3d-115">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="cdb3d-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="cdb3d-116">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="cdb3d-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="cdb3d-117">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="cdb3d-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
