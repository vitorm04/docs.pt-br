---
title: "Método ISymUnmanagedWriter::OpenNamespace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3dffd9605bd238446156d7a32e8e668ddd80916
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="9ebe7-102">Método ISymUnmanagedWriter::OpenNamespace</span><span class="sxs-lookup"><span data-stu-id="9ebe7-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="9ebe7-103">Abre um novo namespace.</span><span class="sxs-lookup"><span data-stu-id="9ebe7-103">Opens a new namespace.</span></span> <span data-ttu-id="9ebe7-104">Chame este método antes de definir métodos ou variáveis que ocupam um namespace.</span><span class="sxs-lookup"><span data-stu-id="9ebe7-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="9ebe7-105">Namespaces podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="9ebe7-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ebe7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ebe7-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ebe7-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ebe7-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="9ebe7-108">[in] Um ponteiro para o nome do novo namespace.</span><span class="sxs-lookup"><span data-stu-id="9ebe7-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ebe7-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9ebe7-109">Return Value</span></span>  
 <span data-ttu-id="9ebe7-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="9ebe7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ebe7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ebe7-111">Requirements</span></span>  
 <span data-ttu-id="9ebe7-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9ebe7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ebe7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ebe7-113">See Also</span></span>  
 [<span data-ttu-id="9ebe7-114">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="9ebe7-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="9ebe7-115">Método CloseNamespace</span><span class="sxs-lookup"><span data-stu-id="9ebe7-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
