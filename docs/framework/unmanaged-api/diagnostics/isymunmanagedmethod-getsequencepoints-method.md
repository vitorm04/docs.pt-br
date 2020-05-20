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
ms.openlocfilehash: 451cfecde7e14fad9d3fed3367112e1fb59796e5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615138"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="f660d-102">Método ISymUnmanagedMethod::GetSequencePoints</span><span class="sxs-lookup"><span data-stu-id="f660d-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="f660d-103">Obtém todos os pontos de sequência dentro deste método.</span><span class="sxs-lookup"><span data-stu-id="f660d-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f660d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f660d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f660d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f660d-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="f660d-106">no Um `ULONG32` que recebe o tamanho das `offsets` `documents` matrizes,, `lines` ,, `columns` `endLines` e `endColumns` .</span><span class="sxs-lookup"><span data-stu-id="f660d-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="f660d-107">fora Um ponteiro para um `ULONG32` que recebe o comprimento do buffer necessário para conter os pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="f660d-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="f660d-108">no Uma matriz na qual armazenar os deslocamentos da MSIL (Microsoft Intermediate Language) do início do método para os pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="f660d-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="f660d-109">no Uma matriz na qual armazenar os documentos nos quais os pontos de sequência estão localizados.</span><span class="sxs-lookup"><span data-stu-id="f660d-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="f660d-110">no Uma matriz na qual armazenar as linhas nos documentos nos quais os pontos de sequência estão localizados.</span><span class="sxs-lookup"><span data-stu-id="f660d-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="f660d-111">no Uma matriz na qual armazenar as colunas nos documentos nos quais os pontos de sequência estão localizados.</span><span class="sxs-lookup"><span data-stu-id="f660d-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="f660d-112">no A matriz de linhas nos documentos em que os pontos de sequência terminam.</span><span class="sxs-lookup"><span data-stu-id="f660d-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="f660d-113">no A matriz de colunas nos documentos em que os pontos de sequência terminam.</span><span class="sxs-lookup"><span data-stu-id="f660d-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f660d-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f660d-114">Return Value</span></span>  
 <span data-ttu-id="f660d-115">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="f660d-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f660d-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f660d-116">Requirements</span></span>  
 <span data-ttu-id="f660d-117">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f660d-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f660d-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="f660d-118">See also</span></span>

- [<span data-ttu-id="f660d-119">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="f660d-119">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
