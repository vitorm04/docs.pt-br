---
title: Interface ISymENCUnmanagedMethod
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4474269688094ea6c81b06659727acfb9c2ad6c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095705"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="9366d-102">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="9366d-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="9366d-103">Fornece informações para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="9366d-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9366d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9366d-104">Methods</span></span>  
  
|<span data-ttu-id="9366d-105">Método</span><span class="sxs-lookup"><span data-stu-id="9366d-105">Method</span></span>|<span data-ttu-id="9366d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9366d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9366d-107">Método GetDocumentsForMethod</span><span class="sxs-lookup"><span data-stu-id="9366d-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="9366d-108">Obtém os documentos que esse método tem linhas em.</span><span class="sxs-lookup"><span data-stu-id="9366d-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="9366d-109">Método GetDocumentsForMethodCount</span><span class="sxs-lookup"><span data-stu-id="9366d-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="9366d-110">Obtém o número de documentos que esse método tem linhas em.</span><span class="sxs-lookup"><span data-stu-id="9366d-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="9366d-111">Método GetFileNameFromOffset</span><span class="sxs-lookup"><span data-stu-id="9366d-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="9366d-112">Obtém o nome do arquivo para a linha associada a um deslocamento.</span><span class="sxs-lookup"><span data-stu-id="9366d-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="9366d-113">Método GetLineFromOffset</span><span class="sxs-lookup"><span data-stu-id="9366d-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="9366d-114">Obtém as informações de linha associadas com um deslocamento.</span><span class="sxs-lookup"><span data-stu-id="9366d-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="9366d-115">Método GetSourceExtentInDocument</span><span class="sxs-lookup"><span data-stu-id="9366d-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="9366d-116">Obtém o menor início maior final de linha para o método e de linha em um documento específico.</span><span class="sxs-lookup"><span data-stu-id="9366d-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9366d-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9366d-117">Requirements</span></span>  
 <span data-ttu-id="9366d-118">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9366d-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9366d-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9366d-119">See also</span></span>

- [<span data-ttu-id="9366d-120">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="9366d-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
