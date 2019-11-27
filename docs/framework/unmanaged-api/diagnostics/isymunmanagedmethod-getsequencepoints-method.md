---
title: Método ISymUnmanagedMethod::GetSequencePoints
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
ms.openlocfilehash: 75d477af7395a9b7d3328b2a5787f810733f3749
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448881"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="8f303-102">Método ISymUnmanagedMethod::GetSequencePoints</span><span class="sxs-lookup"><span data-stu-id="8f303-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="8f303-103">Obtém todos os pontos de sequência dentro deste método.</span><span class="sxs-lookup"><span data-stu-id="8f303-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f303-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f303-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f303-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f303-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="8f303-106">no Um `ULONG32` que recebe o tamanho das matrizes `offsets`, `documents`, `lines`, `columns`, `endLines`e `endColumns`.</span><span class="sxs-lookup"><span data-stu-id="8f303-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="8f303-107">fora Um ponteiro para um `ULONG32` que recebe o comprimento do buffer necessário para conter os pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="8f303-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="8f303-108">no Uma matriz na qual armazenar os deslocamentos da MSIL (Microsoft Intermediate Language) do início do método para os pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="8f303-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="8f303-109">no Uma matriz na qual armazenar os documentos nos quais os pontos de sequência estão localizados.</span><span class="sxs-lookup"><span data-stu-id="8f303-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="8f303-110">no Uma matriz na qual armazenar as linhas nos documentos nos quais os pontos de sequência estão localizados.</span><span class="sxs-lookup"><span data-stu-id="8f303-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="8f303-111">no Uma matriz na qual armazenar as colunas nos documentos nos quais os pontos de sequência estão localizados.</span><span class="sxs-lookup"><span data-stu-id="8f303-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="8f303-112">no A matriz de linhas nos documentos em que os pontos de sequência terminam.</span><span class="sxs-lookup"><span data-stu-id="8f303-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="8f303-113">no A matriz de colunas nos documentos em que os pontos de sequência terminam.</span><span class="sxs-lookup"><span data-stu-id="8f303-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f303-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8f303-114">Return Value</span></span>  
 <span data-ttu-id="8f303-115">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="8f303-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f303-116">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8f303-116">Requirements</span></span>  
 <span data-ttu-id="8f303-117">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8f303-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f303-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f303-118">See also</span></span>

- [<span data-ttu-id="8f303-119">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="8f303-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
