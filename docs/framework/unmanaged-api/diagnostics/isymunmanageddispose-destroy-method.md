---
title: "Método ISymUnmanagedDispose::Destroy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDispose.Destroy
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d808392d883d1168d6aad8d16ab50ce072b1d9f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="f9283-102">Método ISymUnmanagedDispose::Destroy</span><span class="sxs-lookup"><span data-stu-id="f9283-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="f9283-103">Faz com que o objeto subjacente liberar todas as referências internas e retornar falha em todas as chamadas método subsequentes.</span><span class="sxs-lookup"><span data-stu-id="f9283-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9283-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9283-104">Syntax</span></span>  
  
```  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f9283-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f9283-105">Return Value</span></span>  
 <span data-ttu-id="f9283-106">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="f9283-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9283-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9283-107">Requirements</span></span>  
 <span data-ttu-id="f9283-108">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f9283-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9283-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9283-109">See Also</span></span>  
 [<span data-ttu-id="f9283-110">Interface ISymUnmanagedDispose</span><span class="sxs-lookup"><span data-stu-id="f9283-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
