---
title: "Método ISymUnmanagedWriter::DefineField"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineField
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c44c4ba4a2fd8959299bce6c9f3b4dc361174922
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="cddef-102">Método ISymUnmanagedWriter::DefineField</span><span class="sxs-lookup"><span data-stu-id="cddef-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="cddef-103">Define uma única variável que não está dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="cddef-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="cddef-104">Esse método é usado para determinados campos em classes, campos de bits e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="cddef-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cddef-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cddef-105">Syntax</span></span>  
  
```  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cddef-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cddef-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="cddef-107">[in] O tipo de metadados ou um método de token.</span><span class="sxs-lookup"><span data-stu-id="cddef-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="cddef-108">[in] O nome do campo.</span><span class="sxs-lookup"><span data-stu-id="cddef-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="cddef-109">[in] Os atributos de campo.</span><span class="sxs-lookup"><span data-stu-id="cddef-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="cddef-110">[in] Um `ULONG32` que é o tamanho, em caracteres, do buffer necessário para conter a assinatura de campo.</span><span class="sxs-lookup"><span data-stu-id="cddef-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="cddef-111">[in] A matriz de assinaturas de campo.</span><span class="sxs-lookup"><span data-stu-id="cddef-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="cddef-112">[in] O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="cddef-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="cddef-113">[in] O primeiro endereço para a especificação de campo.</span><span class="sxs-lookup"><span data-stu-id="cddef-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="cddef-114">[in] O segundo endereço para a especificação de campo.</span><span class="sxs-lookup"><span data-stu-id="cddef-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="cddef-115">[in] O terceiro endereço para a especificação de campo.</span><span class="sxs-lookup"><span data-stu-id="cddef-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cddef-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cddef-116">Return Value</span></span>  
 <span data-ttu-id="cddef-117">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="cddef-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cddef-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cddef-118">Requirements</span></span>  
 <span data-ttu-id="cddef-119">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cddef-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cddef-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cddef-120">See Also</span></span>  
 [<span data-ttu-id="cddef-121">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="cddef-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
