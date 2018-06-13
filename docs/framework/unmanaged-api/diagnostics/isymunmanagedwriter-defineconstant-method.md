---
title: Método ISymUnmanagedWriter::DefineConstant
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c7cf800dafa9f3e213a012f49c73d51c78e7074
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427399"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="d23d7-102">Método ISymUnmanagedWriter::DefineConstant</span><span class="sxs-lookup"><span data-stu-id="d23d7-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="d23d7-103">Define um nome para um valor constante.</span><span class="sxs-lookup"><span data-stu-id="d23d7-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d23d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d23d7-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d23d7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d23d7-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d23d7-106">[in] Um ponteiro para um `WCHAR` que define o nome de constante.</span><span class="sxs-lookup"><span data-stu-id="d23d7-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="d23d7-107">[in] O valor da constante.</span><span class="sxs-lookup"><span data-stu-id="d23d7-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="d23d7-108">[in] O tamanho do `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="d23d7-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="d23d7-109">[in] A assinatura de tipo da constante.</span><span class="sxs-lookup"><span data-stu-id="d23d7-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d23d7-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d23d7-110">Return Value</span></span>  
 <span data-ttu-id="d23d7-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="d23d7-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d23d7-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d23d7-112">Requirements</span></span>  
 <span data-ttu-id="d23d7-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d23d7-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d23d7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d23d7-114">See Also</span></span>  
 [<span data-ttu-id="d23d7-115">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="d23d7-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="d23d7-116">Método DefineConstant2</span><span class="sxs-lookup"><span data-stu-id="d23d7-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
