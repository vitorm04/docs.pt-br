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
ms.openlocfilehash: 7f470dbe4ef2ef0d5f2204ccbdd5fb64730f9a2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159751"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="110db-102">Método ISymUnmanagedWriter::DefineConstant</span><span class="sxs-lookup"><span data-stu-id="110db-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="110db-103">Define um nome para um valor constante.</span><span class="sxs-lookup"><span data-stu-id="110db-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="110db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="110db-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="110db-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="110db-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="110db-106">[in] Um ponteiro para um `WCHAR` que define o nome de constante.</span><span class="sxs-lookup"><span data-stu-id="110db-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="110db-107">[in] O valor da constante.</span><span class="sxs-lookup"><span data-stu-id="110db-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="110db-108">[in] O tamanho do `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="110db-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="110db-109">[in] A assinatura de tipo para a constante.</span><span class="sxs-lookup"><span data-stu-id="110db-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="110db-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="110db-110">Return Value</span></span>  
 <span data-ttu-id="110db-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="110db-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="110db-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="110db-112">Requirements</span></span>  
 <span data-ttu-id="110db-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="110db-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="110db-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="110db-114">See also</span></span>

- [<span data-ttu-id="110db-115">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="110db-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="110db-116">Método DefineConstant2</span><span class="sxs-lookup"><span data-stu-id="110db-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
