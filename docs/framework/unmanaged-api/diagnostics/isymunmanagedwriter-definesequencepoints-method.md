---
title: Método ISymUnmanagedWriter::DefineSequencePoints
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 735b33ac1f049f8d4d3740239e7c34a6fa16dd32
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146933"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="6ffd8-102">Método ISymUnmanagedWriter::DefineSequencePoints</span><span class="sxs-lookup"><span data-stu-id="6ffd8-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="6ffd8-103">Define um grupo de pontos de sequência dentro do método atual.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="6ffd8-104">Cada linha de início e a coluna inicial definem o início de uma instrução dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="6ffd8-105">Cada um final de linha e coluna de término definem o final de uma instrução dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="6ffd8-106">As matrizes devem ser classificadas em ordem crescente de deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="6ffd8-107">O deslocamento é sempre medido desde o início do método, em bytes.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ffd8-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ffd8-108">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6ffd8-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ffd8-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="6ffd8-110">[in] O objeto de documento para o qual os pontos de sequência estão sendo definidos.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="6ffd8-111">[in] Um `ULONG32` que indica o tamanho de cada um dos `offsets`, `lines`, `columns`, `endLines`, e `endColumns` buffers.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-111">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="6ffd8-112">[in] O deslocamento dos pontos de sequência medidos do início do método.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="6ffd8-113">[in] Os números de linha inicial dos pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="6ffd8-114">[in] Os números da coluna inicial dos pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="6ffd8-115">[in] Os números de linha finais dos pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="6ffd8-116">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="6ffd8-117">[in] Os números da coluna finais dos pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="6ffd8-118">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ffd8-119">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6ffd8-119">Return Value</span></span>  
 <span data-ttu-id="6ffd8-120">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="6ffd8-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ffd8-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ffd8-121">Requirements</span></span>  
 <span data-ttu-id="6ffd8-122">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6ffd8-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ffd8-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ffd8-123">See also</span></span>

- [<span data-ttu-id="6ffd8-124">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="6ffd8-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
