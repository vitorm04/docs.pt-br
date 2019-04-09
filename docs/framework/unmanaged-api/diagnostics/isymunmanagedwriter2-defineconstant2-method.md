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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e9bff5be747c4872554a69dd316de8ca9eb9934
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198927"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="ac2ec-102">Método ISymUnmanagedWriter2::DefineConstant2</span><span class="sxs-lookup"><span data-stu-id="ac2ec-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="ac2ec-103">Define um nome para um valor constante.</span><span class="sxs-lookup"><span data-stu-id="ac2ec-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac2ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac2ec-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac2ec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac2ec-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ac2ec-106">[in] O nome de constante.</span><span class="sxs-lookup"><span data-stu-id="ac2ec-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="ac2ec-107">[in] O valor da constante.</span><span class="sxs-lookup"><span data-stu-id="ac2ec-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="ac2ec-108">[in] O token de metadados da constante.</span><span class="sxs-lookup"><span data-stu-id="ac2ec-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac2ec-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ac2ec-109">Return Value</span></span>  
 <span data-ttu-id="ac2ec-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="ac2ec-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac2ec-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac2ec-111">Requirements</span></span>  
 <span data-ttu-id="ac2ec-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ac2ec-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac2ec-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac2ec-113">See also</span></span>

- [<span data-ttu-id="ac2ec-114">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="ac2ec-114">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="ac2ec-115">Método DefineConstant</span><span class="sxs-lookup"><span data-stu-id="ac2ec-115">DefineConstant Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)
