---
title: "Método ISymUnmanagedWriter2::DefineLocalVariable2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2.DefineLocalVariable2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 595cc3d8c503a5a6b2cbcb6665f7ff8aff5044d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="14d86-102">Método ISymUnmanagedWriter2::DefineLocalVariable2</span><span class="sxs-lookup"><span data-stu-id="14d86-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="14d86-103">Define uma única variável no escopo léxico atual.</span><span class="sxs-lookup"><span data-stu-id="14d86-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="14d86-104">Esse método pode ser chamado várias vezes para uma variável de mesmo nome que tem várias casas ao longo de um escopo.</span><span class="sxs-lookup"><span data-stu-id="14d86-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="14d86-105">Nesse caso, no entanto, os valores de `startOffset` e `endOffset` parâmetros não devem se sobrepor.</span><span class="sxs-lookup"><span data-stu-id="14d86-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14d86-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14d86-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="14d86-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="14d86-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="14d86-108">[in] O nome da variável local.</span><span class="sxs-lookup"><span data-stu-id="14d86-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="14d86-109">[in] Os atributos de variável locais.</span><span class="sxs-lookup"><span data-stu-id="14d86-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="14d86-110">[in] O token de metadados da assinatura.</span><span class="sxs-lookup"><span data-stu-id="14d86-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="14d86-111">[in] O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="14d86-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="14d86-112">[in] O primeiro endereço para a especificação do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="14d86-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="14d86-113">[in] O segundo endereço para a especificação do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="14d86-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="14d86-114">[in] O terceiro endereço para a especificação do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="14d86-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="14d86-115">[in] O deslocamento de início para a variável.</span><span class="sxs-lookup"><span data-stu-id="14d86-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="14d86-116">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="14d86-116">This parameter is optional.</span></span> <span data-ttu-id="14d86-117">Se for 0, esse parâmetro é ignorado e a variável é definida em toda a todo o escopo.</span><span class="sxs-lookup"><span data-stu-id="14d86-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="14d86-118">Se for um valor diferente de zero, a variável está dentro de deslocamentos do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="14d86-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="14d86-119">[in] O deslocamento de fim para a variável.</span><span class="sxs-lookup"><span data-stu-id="14d86-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="14d86-120">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="14d86-120">This parameter is optional.</span></span> <span data-ttu-id="14d86-121">Se for 0, esse parâmetro é ignorado e a variável é definida em toda a todo o escopo.</span><span class="sxs-lookup"><span data-stu-id="14d86-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="14d86-122">Se for um valor diferente de zero, a variável está dentro de deslocamentos do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="14d86-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14d86-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="14d86-123">Return Value</span></span>  
 <span data-ttu-id="14d86-124">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="14d86-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14d86-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="14d86-125">Requirements</span></span>  
 <span data-ttu-id="14d86-126">**Cabeçalho:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="14d86-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d86-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14d86-127">See Also</span></span>  
 [<span data-ttu-id="14d86-128">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="14d86-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="14d86-129">Método DefineLocalVariable</span><span class="sxs-lookup"><span data-stu-id="14d86-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
