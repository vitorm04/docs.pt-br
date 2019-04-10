---
title: Método ISymUnmanagedWriter::DefineGlobalVariable
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66efe5ae1fe2154684d2ac6791895b7fcbe4f7b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225906"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="b76e0-102">Método ISymUnmanagedWriter::DefineGlobalVariable</span><span class="sxs-lookup"><span data-stu-id="b76e0-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="b76e0-103">Define uma única variável global.</span><span class="sxs-lookup"><span data-stu-id="b76e0-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b76e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b76e0-104">Syntax</span></span>  
  
```  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b76e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b76e0-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b76e0-106">[in] Um ponteiro para um `WCHAR` que define o nome da variável global.</span><span class="sxs-lookup"><span data-stu-id="b76e0-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="b76e0-107">[in] Atributos da variável global.</span><span class="sxs-lookup"><span data-stu-id="b76e0-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="b76e0-108">[in] Um `ULONG32` que indica o tamanho, em caracteres, da `signature` buffer.</span><span class="sxs-lookup"><span data-stu-id="b76e0-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="b76e0-109">[in] A assinatura da variável global.</span><span class="sxs-lookup"><span data-stu-id="b76e0-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="b76e0-110">[in] O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="b76e0-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="b76e0-111">[in] O primeiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b76e0-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="b76e0-112">[in] O segundo endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b76e0-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="b76e0-113">[in] O terceiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b76e0-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b76e0-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b76e0-114">Return Value</span></span>  
 <span data-ttu-id="b76e0-115">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b76e0-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b76e0-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b76e0-116">Requirements</span></span>  
 <span data-ttu-id="b76e0-117">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b76e0-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b76e0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b76e0-118">See also</span></span>

- [<span data-ttu-id="b76e0-119">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="b76e0-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="b76e0-120">Método DefineLocalVariable</span><span class="sxs-lookup"><span data-stu-id="b76e0-120">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="b76e0-121">Método DefineGlobalVariable2</span><span class="sxs-lookup"><span data-stu-id="b76e0-121">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
