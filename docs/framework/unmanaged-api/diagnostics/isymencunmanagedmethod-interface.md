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
ms.openlocfilehash: 54c8c7f5c3ba6b4afd4ff352a8afb947a92e2d61
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441871"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="660f0-102">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="660f0-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="660f0-103">Fornece informações para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="660f0-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="660f0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="660f0-104">Methods</span></span>  
  
|<span data-ttu-id="660f0-105">Método</span><span class="sxs-lookup"><span data-stu-id="660f0-105">Method</span></span>|<span data-ttu-id="660f0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="660f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="660f0-107">Método GetDocumentsForMethod</span><span class="sxs-lookup"><span data-stu-id="660f0-107">GetDocumentsForMethod Method</span></span>](isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="660f0-108">Obtém os documentos em que este método tem linhas.</span><span class="sxs-lookup"><span data-stu-id="660f0-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="660f0-109">Método GetDocumentsForMethodCount</span><span class="sxs-lookup"><span data-stu-id="660f0-109">GetDocumentsForMethodCount Method</span></span>](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="660f0-110">Obtém o número de documentos em que esse método tem linhas.</span><span class="sxs-lookup"><span data-stu-id="660f0-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="660f0-111">Método GetFileNameFromOffset</span><span class="sxs-lookup"><span data-stu-id="660f0-111">GetFileNameFromOffset Method</span></span>](isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="660f0-112">Obtém o nome do arquivo da linha associada a um deslocamento.</span><span class="sxs-lookup"><span data-stu-id="660f0-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="660f0-113">Método GetLineFromOffset</span><span class="sxs-lookup"><span data-stu-id="660f0-113">GetLineFromOffset Method</span></span>](isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="660f0-114">Obtém as informações de linha associadas a um deslocamento.</span><span class="sxs-lookup"><span data-stu-id="660f0-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="660f0-115">Método GetSourceExtentInDocument</span><span class="sxs-lookup"><span data-stu-id="660f0-115">GetSourceExtentInDocument Method</span></span>](isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="660f0-116">Obtém a menor linha inicial e a linha final maior para o método em um documento específico.</span><span class="sxs-lookup"><span data-stu-id="660f0-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="660f0-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="660f0-117">Requirements</span></span>  
 <span data-ttu-id="660f0-118">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="660f0-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="660f0-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="660f0-119">See also</span></span>

- [<span data-ttu-id="660f0-120">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="660f0-120">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
