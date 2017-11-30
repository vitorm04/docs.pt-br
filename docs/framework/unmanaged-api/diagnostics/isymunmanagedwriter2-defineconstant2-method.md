---
title: "Método ISymUnmanagedWriter2::DefineConstant2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2.DefineConstant2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 998916ab485042ba2f8493afe84ea5375f3eb740
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="b3a62-102">Método ISymUnmanagedWriter2::DefineConstant2</span><span class="sxs-lookup"><span data-stu-id="b3a62-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="b3a62-103">Define um nome para um valor constante.</span><span class="sxs-lookup"><span data-stu-id="b3a62-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3a62-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3a62-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3a62-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b3a62-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b3a62-106">[in] O nome de constante.</span><span class="sxs-lookup"><span data-stu-id="b3a62-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="b3a62-107">[in] O valor da constante.</span><span class="sxs-lookup"><span data-stu-id="b3a62-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="b3a62-108">[in] O token de metadados da constante.</span><span class="sxs-lookup"><span data-stu-id="b3a62-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3a62-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b3a62-109">Return Value</span></span>  
 <span data-ttu-id="b3a62-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b3a62-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3a62-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3a62-111">Requirements</span></span>  
 <span data-ttu-id="b3a62-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b3a62-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a62-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3a62-113">See Also</span></span>  
 [<span data-ttu-id="b3a62-114">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="b3a62-114">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="b3a62-115">Método DefineConstant</span><span class="sxs-lookup"><span data-stu-id="b3a62-115">DefineConstant Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)
