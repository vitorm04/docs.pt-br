---
title: "Método ISymUnmanagedWriter::SetSymAttribute"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetSymAttribute
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90360d6fe5a1a95719a9bb09e5e0b6b2a70675a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="730b0-102">Método ISymUnmanagedWriter::SetSymAttribute</span><span class="sxs-lookup"><span data-stu-id="730b0-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="730b0-103">Define um atributo personalizado com base no seu nome.</span><span class="sxs-lookup"><span data-stu-id="730b0-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="730b0-104">Esses atributos são mantidos no repositório de símbolos, ao contrário de atributos personalizados de metadados.</span><span class="sxs-lookup"><span data-stu-id="730b0-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="730b0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="730b0-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="730b0-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="730b0-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="730b0-107">[in] O token de metadados para o qual o atributo é definido.</span><span class="sxs-lookup"><span data-stu-id="730b0-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="730b0-108">[in] Um ponteiro para um `WCHAR` que contém o nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="730b0-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="730b0-109">[in] Um `ULONG32` que indica o tamanho do `data` matriz.</span><span class="sxs-lookup"><span data-stu-id="730b0-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="730b0-110">[in] O valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="730b0-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="730b0-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="730b0-111">Return Value</span></span>  
 <span data-ttu-id="730b0-112">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="730b0-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="730b0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="730b0-113">Requirements</span></span>  
 <span data-ttu-id="730b0-114">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="730b0-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="730b0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="730b0-115">See Also</span></span>  
 [<span data-ttu-id="730b0-116">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="730b0-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
