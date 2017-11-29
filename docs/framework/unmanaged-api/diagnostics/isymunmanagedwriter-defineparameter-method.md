---
title: "Método ISymUnmanagedWriter::DefineParameter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineParameter
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 166087a27d0aa7b100da563c25f7e5a52612ce50
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="76ff7-102">Método ISymUnmanagedWriter::DefineParameter</span><span class="sxs-lookup"><span data-stu-id="76ff7-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="76ff7-103">Define um único parâmetro no método atual.</span><span class="sxs-lookup"><span data-stu-id="76ff7-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="76ff7-104">O tipo de parâmetro é obtido da posição do parâmetro (sequência) na assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="76ff7-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="76ff7-105">Se os parâmetros são definidos nos metadados para um determinado método, não é necessário defini-los novamente usando esse método.</span><span class="sxs-lookup"><span data-stu-id="76ff7-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="76ff7-106">Os leitores de símbolo devem verificar os metadados normal para os parâmetros antes de verificar se o armazenamento de símbolo.</span><span class="sxs-lookup"><span data-stu-id="76ff7-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76ff7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76ff7-107">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="76ff7-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76ff7-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="76ff7-109">[in] O nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="76ff7-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="76ff7-110">[in] Os atributos de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="76ff7-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="76ff7-111">[in] A assinatura do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="76ff7-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="76ff7-112">[in] O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="76ff7-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="76ff7-113">[in] O primeiro endereço para a especificação do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="76ff7-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="76ff7-114">[in] O segundo endereço para a especificação do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="76ff7-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="76ff7-115">[in] O terceiro endereço para a especificação do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="76ff7-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76ff7-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="76ff7-116">Return Value</span></span>  
 <span data-ttu-id="76ff7-117">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="76ff7-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76ff7-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76ff7-118">Requirements</span></span>  
 <span data-ttu-id="76ff7-119">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="76ff7-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ff7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76ff7-120">See Also</span></span>  
 [<span data-ttu-id="76ff7-121">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="76ff7-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
