---
title: Método ISymUnmanagedScope::GetParent
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetParent
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 606b9b496380a00ab9615ab7fe7febdc749b3ee2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663525"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="1aed6-102">Método ISymUnmanagedScope::GetParent</span><span class="sxs-lookup"><span data-stu-id="1aed6-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="1aed6-103">Obtém o escopo pai desse escopo.</span><span class="sxs-lookup"><span data-stu-id="1aed6-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aed6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1aed6-104">Syntax</span></span>  
  
```  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1aed6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1aed6-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1aed6-106">[out] Um ponteiro para retornado [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="1aed6-106">[out] A pointer to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1aed6-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1aed6-107">Return Value</span></span>  
 <span data-ttu-id="1aed6-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="1aed6-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aed6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1aed6-109">Requirements</span></span>  
 <span data-ttu-id="1aed6-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1aed6-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aed6-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1aed6-111">See also</span></span>
- [<span data-ttu-id="1aed6-112">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="1aed6-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="1aed6-113">Método GetChildren</span><span class="sxs-lookup"><span data-stu-id="1aed6-113">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)
