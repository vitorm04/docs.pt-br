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
ms.workload: dotnet
ms.openlocfilehash: 1124b57bed16e349c753be872c1b709a287e6237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="64329-102">Método ISymUnmanagedWriter2::DefineLocalVariable2</span><span class="sxs-lookup"><span data-stu-id="64329-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="64329-103">Define uma única variável no escopo léxico atual.</span><span class="sxs-lookup"><span data-stu-id="64329-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="64329-104">Esse método pode ser chamado várias vezes para uma variável de mesmo nome que tem várias casas ao longo de um escopo.</span><span class="sxs-lookup"><span data-stu-id="64329-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="64329-105">Nesse caso, no entanto, os valores de `startOffset` e `endOffset` parâmetros não devem se sobrepor.</span><span class="sxs-lookup"><span data-stu-id="64329-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64329-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64329-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="64329-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="64329-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="64329-108">[in] O nome da variável local.</span><span class="sxs-lookup"><span data-stu-id="64329-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="64329-109">[in] Os atributos de variável locais.</span><span class="sxs-lookup"><span data-stu-id="64329-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="64329-110">[in] O token de metadados da assinatura.</span><span class="sxs-lookup"><span data-stu-id="64329-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="64329-111">[in] O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="64329-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="64329-112">[in] O primeiro endereço para a especificação do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="64329-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="64329-113">[in] O segundo endereço para a especificação do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="64329-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="64329-114">[in] O terceiro endereço para a especificação do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="64329-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="64329-115">[in] O deslocamento de início para a variável.</span><span class="sxs-lookup"><span data-stu-id="64329-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="64329-116">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="64329-116">This parameter is optional.</span></span> <span data-ttu-id="64329-117">Se for 0, esse parâmetro é ignorado e a variável é definida em toda a todo o escopo.</span><span class="sxs-lookup"><span data-stu-id="64329-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="64329-118">Se for um valor diferente de zero, a variável está dentro de deslocamentos do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="64329-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="64329-119">[in] O deslocamento de fim para a variável.</span><span class="sxs-lookup"><span data-stu-id="64329-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="64329-120">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="64329-120">This parameter is optional.</span></span> <span data-ttu-id="64329-121">Se for 0, esse parâmetro é ignorado e a variável é definida em toda a todo o escopo.</span><span class="sxs-lookup"><span data-stu-id="64329-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="64329-122">Se for um valor diferente de zero, a variável está dentro de deslocamentos do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="64329-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64329-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="64329-123">Return Value</span></span>  
 <span data-ttu-id="64329-124">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="64329-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64329-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64329-125">Requirements</span></span>  
 <span data-ttu-id="64329-126">**Cabeçalho:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="64329-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64329-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64329-127">See Also</span></span>  
 [<span data-ttu-id="64329-128">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="64329-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="64329-129">Método DefineLocalVariable</span><span class="sxs-lookup"><span data-stu-id="64329-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
