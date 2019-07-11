---
title: Método ISymUnmanagedWriter::DefineLocalVariable
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9466df3f6413f86eb8558f0037b96c254b2a2e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777347"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="82eb3-102">Método ISymUnmanagedWriter::DefineLocalVariable</span><span class="sxs-lookup"><span data-stu-id="82eb3-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="82eb3-103">Define uma única variável no escopo léxico atual.</span><span class="sxs-lookup"><span data-stu-id="82eb3-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="82eb3-104">Esse método pode ser chamado várias vezes para uma variável de mesmo nome que tem vários residências ao longo de um escopo.</span><span class="sxs-lookup"><span data-stu-id="82eb3-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="82eb3-105">Nesse caso, no entanto, os valores de `startOffset` e `endOffset` parâmetros não devem se sobrepor.</span><span class="sxs-lookup"><span data-stu-id="82eb3-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82eb3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82eb3-106">Syntax</span></span>  
  
```cpp  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82eb3-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82eb3-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="82eb3-108">[in] Um ponteiro para um `WCHAR` que define o nome da variável local.</span><span class="sxs-lookup"><span data-stu-id="82eb3-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="82eb3-109">[in] Atributos da variável local.</span><span class="sxs-lookup"><span data-stu-id="82eb3-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="82eb3-110">[in] Um `ULONG32` que indica o tamanho, em bytes, da `signature` buffer.</span><span class="sxs-lookup"><span data-stu-id="82eb3-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="82eb3-111">[in] A assinatura da variável local.</span><span class="sxs-lookup"><span data-stu-id="82eb3-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="82eb3-112">[in] O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="82eb3-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="82eb3-113">[in] O primeiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="82eb3-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="82eb3-114">[in] O segundo endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="82eb3-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="82eb3-115">[in] O terceiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="82eb3-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="82eb3-116">[in] O deslocamento inicial da variável.</span><span class="sxs-lookup"><span data-stu-id="82eb3-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="82eb3-117">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="82eb3-117">This parameter is optional.</span></span> <span data-ttu-id="82eb3-118">Se for 0, esse parâmetro será ignorado e a variável será definida ao longo de todo o escopo.</span><span class="sxs-lookup"><span data-stu-id="82eb3-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="82eb3-119">Se for um valor diferente de zero, a variável estará dentro dos deslocamentos do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="82eb3-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="82eb3-120">[in] O deslocamento final da variável.</span><span class="sxs-lookup"><span data-stu-id="82eb3-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="82eb3-121">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="82eb3-121">This parameter is optional.</span></span> <span data-ttu-id="82eb3-122">Se for 0, esse parâmetro será ignorado e a variável será definida ao longo de todo o escopo.</span><span class="sxs-lookup"><span data-stu-id="82eb3-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="82eb3-123">Se for um valor diferente de zero, a variável estará dentro dos deslocamentos do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="82eb3-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82eb3-124">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="82eb3-124">Return Value</span></span>  
 <span data-ttu-id="82eb3-125">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="82eb3-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82eb3-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82eb3-126">Requirements</span></span>  
 <span data-ttu-id="82eb3-127">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="82eb3-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82eb3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82eb3-128">See also</span></span>

- [<span data-ttu-id="82eb3-129">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="82eb3-129">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="82eb3-130">Método DefineGlobalVariable</span><span class="sxs-lookup"><span data-stu-id="82eb3-130">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="82eb3-131">Método DefineLocalVariable2</span><span class="sxs-lookup"><span data-stu-id="82eb3-131">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
