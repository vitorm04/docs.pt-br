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
ms.workload: dotnet
ms.openlocfilehash: 77d50f6bac87d5a110b53a69044f96f547c51904
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="f9f4d-102">Método ISymUnmanagedWriter::OpenNamespace</span><span class="sxs-lookup"><span data-stu-id="f9f4d-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="f9f4d-103">Abre um novo namespace.</span><span class="sxs-lookup"><span data-stu-id="f9f4d-103">Opens a new namespace.</span></span> <span data-ttu-id="f9f4d-104">Chame este método antes de definir métodos ou variáveis que ocupam um namespace.</span><span class="sxs-lookup"><span data-stu-id="f9f4d-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="f9f4d-105">Namespaces podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="f9f4d-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9f4d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9f4d-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9f4d-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9f4d-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="f9f4d-108">[in] Um ponteiro para o nome do novo namespace.</span><span class="sxs-lookup"><span data-stu-id="f9f4d-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9f4d-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f9f4d-109">Return Value</span></span>  
 <span data-ttu-id="f9f4d-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="f9f4d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9f4d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9f4d-111">Requirements</span></span>  
 <span data-ttu-id="f9f4d-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f9f4d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9f4d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9f4d-113">See Also</span></span>  
 [<span data-ttu-id="f9f4d-114">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="f9f4d-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="f9f4d-115">Método CloseNamespace</span><span class="sxs-lookup"><span data-stu-id="f9f4d-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
