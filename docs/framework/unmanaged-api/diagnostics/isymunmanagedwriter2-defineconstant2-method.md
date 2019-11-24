---
title: Método ISymUnmanagedWriter2::DefineConstant2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
ms.openlocfilehash: 6600ca7e70ac77ffba0c75812f27d388c354ece6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438321"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="c397a-102">Método ISymUnmanagedWriter2::DefineConstant2</span><span class="sxs-lookup"><span data-stu-id="c397a-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="c397a-103">Defines a name for a constant value.</span><span class="sxs-lookup"><span data-stu-id="c397a-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c397a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c397a-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c397a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c397a-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c397a-106">[in] The constant name.</span><span class="sxs-lookup"><span data-stu-id="c397a-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="c397a-107">[in] The value of the constant.</span><span class="sxs-lookup"><span data-stu-id="c397a-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="c397a-108">[in] The metadata token of the constant.</span><span class="sxs-lookup"><span data-stu-id="c397a-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c397a-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c397a-109">Return Value</span></span>  
 <span data-ttu-id="c397a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="c397a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c397a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c397a-111">Requirements</span></span>  
 <span data-ttu-id="c397a-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c397a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c397a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c397a-113">See also</span></span>

- [<span data-ttu-id="c397a-114">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="c397a-114">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="c397a-115">Método DefineConstant</span><span class="sxs-lookup"><span data-stu-id="c397a-115">DefineConstant Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)
