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
ms.openlocfilehash: 47477bb473df8b568844d07bea704df681c9b95d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448602"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="199dd-102">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="199dd-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="199dd-103">Fornece informações para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="199dd-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="199dd-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="199dd-104">Methods</span></span>  
  
|<span data-ttu-id="199dd-105">Método</span><span class="sxs-lookup"><span data-stu-id="199dd-105">Method</span></span>|<span data-ttu-id="199dd-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="199dd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="199dd-107">Método GetDocumentsForMethod</span><span class="sxs-lookup"><span data-stu-id="199dd-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="199dd-108">Obtém os documentos em que este método tem linhas.</span><span class="sxs-lookup"><span data-stu-id="199dd-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="199dd-109">Método GetDocumentsForMethodCount</span><span class="sxs-lookup"><span data-stu-id="199dd-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="199dd-110">Obtém o número de documentos em que esse método tem linhas.</span><span class="sxs-lookup"><span data-stu-id="199dd-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="199dd-111">Método GetFileNameFromOffset</span><span class="sxs-lookup"><span data-stu-id="199dd-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="199dd-112">Obtém o nome do arquivo da linha associada a um deslocamento.</span><span class="sxs-lookup"><span data-stu-id="199dd-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="199dd-113">Método GetLineFromOffset</span><span class="sxs-lookup"><span data-stu-id="199dd-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="199dd-114">Obtém as informações de linha associadas a um deslocamento.</span><span class="sxs-lookup"><span data-stu-id="199dd-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="199dd-115">Método GetSourceExtentInDocument</span><span class="sxs-lookup"><span data-stu-id="199dd-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="199dd-116">Obtém a menor linha inicial e a linha final maior para o método em um documento específico.</span><span class="sxs-lookup"><span data-stu-id="199dd-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="199dd-117">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="199dd-117">Requirements</span></span>  
 <span data-ttu-id="199dd-118">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="199dd-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="199dd-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="199dd-119">See also</span></span>

- [<span data-ttu-id="199dd-120">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="199dd-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
