---
title: "Método ISymUnmanagedScope::GetEndOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetEndOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dd3b7c78c3a43109c3508487aa34650f0f16d196
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="2d87a-102">Método ISymUnmanagedScope::GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="2d87a-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="2d87a-103">Obtém o deslocamento de fim para esse escopo.</span><span class="sxs-lookup"><span data-stu-id="2d87a-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d87a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d87a-104">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d87a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2d87a-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2d87a-106">[out] Um ponteiro para um `ULONG32` que recebe o deslocamento de fim.</span><span class="sxs-lookup"><span data-stu-id="2d87a-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d87a-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2d87a-107">Return Value</span></span>  
 <span data-ttu-id="2d87a-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="2d87a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d87a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d87a-109">Requirements</span></span>  
 <span data-ttu-id="2d87a-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2d87a-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d87a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d87a-111">See Also</span></span>  
 [<span data-ttu-id="2d87a-112">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="2d87a-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="2d87a-113">Método GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="2d87a-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)
