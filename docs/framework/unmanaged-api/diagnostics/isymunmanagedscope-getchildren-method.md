---
title: Método ISymUnmanagedScope::GetChildren
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
ms.openlocfilehash: c7e9d2fe94c33127d8b105333ad6dac9d6cc5af6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446364"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="d0fc6-102">Método ISymUnmanagedScope::GetChildren</span><span class="sxs-lookup"><span data-stu-id="d0fc6-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="d0fc6-103">Gets the children of this scope.</span><span class="sxs-lookup"><span data-stu-id="d0fc6-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0fc6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0fc6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0fc6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d0fc6-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="d0fc6-106">[in] A `ULONG32` that indicates the size of the `children` array.</span><span class="sxs-lookup"><span data-stu-id="d0fc6-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="d0fc6-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span><span class="sxs-lookup"><span data-stu-id="d0fc6-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="d0fc6-108">[out] The returned array of children.</span><span class="sxs-lookup"><span data-stu-id="d0fc6-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0fc6-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d0fc6-109">Return Value</span></span>  
 <span data-ttu-id="d0fc6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="d0fc6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0fc6-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0fc6-111">Requirements</span></span>  
 <span data-ttu-id="d0fc6-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d0fc6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0fc6-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0fc6-113">See also</span></span>

- [<span data-ttu-id="d0fc6-114">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="d0fc6-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="d0fc6-115">Método GetParent</span><span class="sxs-lookup"><span data-stu-id="d0fc6-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
