---
title: Método ISymUnmanagedWriter2::DefineLocalVariable2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0ce6a207f2a7862b0b49f1e68cda9528aa03ca7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667525"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="d1458-102">Método ISymUnmanagedWriter2::DefineLocalVariable2</span><span class="sxs-lookup"><span data-stu-id="d1458-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="d1458-103">Define uma única variável no escopo léxico atual.</span><span class="sxs-lookup"><span data-stu-id="d1458-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="d1458-104">Esse método pode ser chamado várias vezes para uma variável de mesmo nome que tem vários residências ao longo de um escopo.</span><span class="sxs-lookup"><span data-stu-id="d1458-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="d1458-105">Nesse caso, no entanto, os valores de `startOffset` e `endOffset` parâmetros não devem se sobrepor.</span><span class="sxs-lookup"><span data-stu-id="d1458-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1458-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1458-106">Syntax</span></span>  
  
```  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1458-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d1458-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d1458-108">[in] O nome da variável local.</span><span class="sxs-lookup"><span data-stu-id="d1458-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="d1458-109">[in] Atributos da variável local.</span><span class="sxs-lookup"><span data-stu-id="d1458-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="d1458-110">[in] O token de metadados da assinatura.</span><span class="sxs-lookup"><span data-stu-id="d1458-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="d1458-111">[in] O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="d1458-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="d1458-112">[in] O primeiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d1458-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="d1458-113">[in] O segundo endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d1458-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="d1458-114">[in] O terceiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d1458-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="d1458-115">[in] O deslocamento inicial da variável.</span><span class="sxs-lookup"><span data-stu-id="d1458-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="d1458-116">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="d1458-116">This parameter is optional.</span></span> <span data-ttu-id="d1458-117">Se for 0, esse parâmetro será ignorado e a variável será definida ao longo de todo o escopo.</span><span class="sxs-lookup"><span data-stu-id="d1458-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="d1458-118">Se for um valor diferente de zero, a variável estará dentro dos deslocamentos do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="d1458-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="d1458-119">[in] O deslocamento final da variável.</span><span class="sxs-lookup"><span data-stu-id="d1458-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="d1458-120">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="d1458-120">This parameter is optional.</span></span> <span data-ttu-id="d1458-121">Se for 0, esse parâmetro será ignorado e a variável será definida ao longo de todo o escopo.</span><span class="sxs-lookup"><span data-stu-id="d1458-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="d1458-122">Se for um valor diferente de zero, a variável estará dentro dos deslocamentos do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="d1458-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1458-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d1458-123">Return Value</span></span>  
 <span data-ttu-id="d1458-124">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="d1458-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1458-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d1458-125">Requirements</span></span>  
 <span data-ttu-id="d1458-126">**Cabeçalho:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="d1458-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1458-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1458-127">See also</span></span>
- [<span data-ttu-id="d1458-128">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="d1458-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="d1458-129">Método DefineLocalVariable</span><span class="sxs-lookup"><span data-stu-id="d1458-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
