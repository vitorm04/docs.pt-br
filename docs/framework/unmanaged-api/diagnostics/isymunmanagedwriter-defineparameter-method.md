---
title: Método ISymUnmanagedWriter::DefineParameter
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0fb35f5d7fec0c79a31cd8d7b77cf2b1c043f60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986070"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="6f15d-102">Método ISymUnmanagedWriter::DefineParameter</span><span class="sxs-lookup"><span data-stu-id="6f15d-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="6f15d-103">Define um único parâmetro no método atual.</span><span class="sxs-lookup"><span data-stu-id="6f15d-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="6f15d-104">O tipo de parâmetro é obtido a posição do parâmetro (sequência) dentro da assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="6f15d-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="6f15d-105">Se os parâmetros são definidos nos metadados para um determinado método, você não precisa defini-los novamente usando esse método.</span><span class="sxs-lookup"><span data-stu-id="6f15d-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="6f15d-106">Os leitores de símbolo devem verificar os metadados normal para os parâmetros antes de verificar se o repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="6f15d-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f15d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f15d-107">Syntax</span></span>  
  
```  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f15d-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6f15d-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6f15d-109">[in] O nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6f15d-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="6f15d-110">[in] Os atributos de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6f15d-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="6f15d-111">[in] A assinatura do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6f15d-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="6f15d-112">[in] O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="6f15d-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="6f15d-113">[in] O primeiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6f15d-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="6f15d-114">[in] O segundo endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6f15d-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="6f15d-115">[in] O terceiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6f15d-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f15d-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6f15d-116">Return Value</span></span>  
 <span data-ttu-id="6f15d-117">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="6f15d-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f15d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f15d-118">Requirements</span></span>  
 <span data-ttu-id="6f15d-119">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6f15d-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f15d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f15d-120">See also</span></span>

- [<span data-ttu-id="6f15d-121">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="6f15d-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
