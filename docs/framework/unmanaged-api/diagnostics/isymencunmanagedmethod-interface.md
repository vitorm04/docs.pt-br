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
ms.openlocfilehash: 575c732cf1b1caf4700568a9d168463359d1ad7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="c2d67-102">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="c2d67-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="c2d67-103">Fornece informações para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="c2d67-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c2d67-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c2d67-104">Methods</span></span>  
  
|<span data-ttu-id="c2d67-105">Método</span><span class="sxs-lookup"><span data-stu-id="c2d67-105">Method</span></span>|<span data-ttu-id="c2d67-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2d67-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c2d67-107">Método GetDocumentsForMethod</span><span class="sxs-lookup"><span data-stu-id="c2d67-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="c2d67-108">Obtém os documentos que esse método tem linhas em.</span><span class="sxs-lookup"><span data-stu-id="c2d67-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="c2d67-109">Método GetDocumentsForMethodCount</span><span class="sxs-lookup"><span data-stu-id="c2d67-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="c2d67-110">Obtém o número de documentos que esse método tem linhas em.</span><span class="sxs-lookup"><span data-stu-id="c2d67-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="c2d67-111">Método GetFileNameFromOffset</span><span class="sxs-lookup"><span data-stu-id="c2d67-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="c2d67-112">Obtém o nome do arquivo para a linha associada a um deslocamento.</span><span class="sxs-lookup"><span data-stu-id="c2d67-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="c2d67-113">Método GetLineFromOffset</span><span class="sxs-lookup"><span data-stu-id="c2d67-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="c2d67-114">Obtém as informações de linha associadas com um deslocamento.</span><span class="sxs-lookup"><span data-stu-id="c2d67-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="c2d67-115">Método GetSourceExtentInDocument</span><span class="sxs-lookup"><span data-stu-id="c2d67-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="c2d67-116">Obtém o menor início linha e maior final para o método em um documento específico.</span><span class="sxs-lookup"><span data-stu-id="c2d67-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2d67-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2d67-117">Requirements</span></span>  
 <span data-ttu-id="c2d67-118">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c2d67-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d67-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2d67-119">See Also</span></span>  
 [<span data-ttu-id="c2d67-120">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="c2d67-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
