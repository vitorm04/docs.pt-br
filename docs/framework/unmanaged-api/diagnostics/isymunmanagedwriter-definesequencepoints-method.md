---
title: "Método ISymUnmanagedWriter::DefineSequencePoints"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e1dcc427a6d034ce108ca66f71cc24b1050a72f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="4cbc1-102">Método ISymUnmanagedWriter::DefineSequencePoints</span><span class="sxs-lookup"><span data-stu-id="4cbc1-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="4cbc1-103">Define um grupo de pontos de sequência dentro do método atual.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="4cbc1-104">Cada linha de início e a coluna de início definem o início de uma instrução dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="4cbc1-105">Cada final de linha e coluna de término definem o fim de uma instrução dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="4cbc1-106">As matrizes devem ser classificadas em ordem crescente de deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="4cbc1-107">O deslocamento é sempre medido desde o início do método, em bytes.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cbc1-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4cbc1-108">Syntax</span></span>  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cbc1-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4cbc1-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="4cbc1-110">[in] O objeto de documento para o qual os pontos de sequência estão sendo definidos.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="4cbc1-111">[in] Um `ULONG32` que indica o tamanho de cada uma da `offsets`, `lines`, `columns`, `endLines`, e `endColumns` buffers.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-111">[in] A `ULONG32` that that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="4cbc1-112">[in] O deslocamento dos pontos de sequência é medido desde o início do método.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="4cbc1-113">[in] Os números de linha inicial dos pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="4cbc1-114">[in] Os números da coluna inicial dos pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="4cbc1-115">[in] Os números de linha final dos pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="4cbc1-116">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="4cbc1-117">[in] Os números da coluna final dos pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="4cbc1-118">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cbc1-119">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4cbc1-119">Return Value</span></span>  
 <span data-ttu-id="4cbc1-120">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="4cbc1-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cbc1-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4cbc1-121">Requirements</span></span>  
 <span data-ttu-id="4cbc1-122">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4cbc1-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cbc1-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4cbc1-123">See Also</span></span>  
 [<span data-ttu-id="4cbc1-124">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="4cbc1-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
