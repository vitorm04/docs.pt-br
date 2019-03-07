---
title: Método ISymUnmanagedWriter::DefineField
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a385e42ae3a494f6d2196e21b552c6b5679dda9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468878"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="5ea4f-102">Método ISymUnmanagedWriter::DefineField</span><span class="sxs-lookup"><span data-stu-id="5ea4f-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="5ea4f-103">Define uma única variável que não está dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="5ea4f-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="5ea4f-104">Esse método é usado para determinados campos em classes, campos de bits e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="5ea4f-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ea4f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ea4f-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5ea4f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ea4f-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="5ea4f-107">[in] O método ou tipo de metadados de token.</span><span class="sxs-lookup"><span data-stu-id="5ea4f-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="5ea4f-108">[in] O nome do campo.</span><span class="sxs-lookup"><span data-stu-id="5ea4f-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="5ea4f-109">[in] Os atributos de campo.</span><span class="sxs-lookup"><span data-stu-id="5ea4f-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="5ea4f-110">[in] Um `ULONG32` que é o tamanho, em caracteres, do buffer necessário para conter a assinatura de campo.</span><span class="sxs-lookup"><span data-stu-id="5ea4f-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="5ea4f-111">[in] A matriz de assinaturas de campo.</span><span class="sxs-lookup"><span data-stu-id="5ea4f-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="5ea4f-112">[in] O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="5ea4f-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="5ea4f-113">[in] O primeiro endereço para a especificação de campo.</span><span class="sxs-lookup"><span data-stu-id="5ea4f-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="5ea4f-114">[in] O segundo endereço para a especificação de campo.</span><span class="sxs-lookup"><span data-stu-id="5ea4f-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="5ea4f-115">[in] O terceiro endereço para a especificação de campo.</span><span class="sxs-lookup"><span data-stu-id="5ea4f-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ea4f-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5ea4f-116">Return Value</span></span>  
 <span data-ttu-id="5ea4f-117">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="5ea4f-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ea4f-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ea4f-118">Requirements</span></span>  
 <span data-ttu-id="5ea4f-119">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5ea4f-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea4f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ea4f-120">See also</span></span>
- [<span data-ttu-id="5ea4f-121">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="5ea4f-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
