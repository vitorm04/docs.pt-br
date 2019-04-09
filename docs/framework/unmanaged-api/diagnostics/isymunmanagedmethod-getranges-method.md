---
title: Método ISymUnmanagedMethod::GetRanges
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94ca1db2bf85f42117f686a8cb483907003927c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205843"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="b83df-102">Método ISymUnmanagedMethod::GetRanges</span><span class="sxs-lookup"><span data-stu-id="b83df-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="b83df-103">Dado uma posição em um documento, retorna uma matriz de pares de deslocamento inicial e final que correspondem aos intervalos de Microsoft intermediate language (MSIL) que a posição cobre dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="b83df-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="b83df-104">A matriz é uma matriz de inteiros e tem o formato [início, final, início, fim].</span><span class="sxs-lookup"><span data-stu-id="b83df-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="b83df-105">O número de pares de intervalo é o comprimento da matriz dividido por 2.</span><span class="sxs-lookup"><span data-stu-id="b83df-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b83df-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b83df-106">Syntax</span></span>  
  
```  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b83df-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b83df-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="b83df-108">[in] O documento para o qual o deslocamento é solicitado.</span><span class="sxs-lookup"><span data-stu-id="b83df-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="b83df-109">[in] A linha do documento correspondente a intervalos.</span><span class="sxs-lookup"><span data-stu-id="b83df-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="b83df-110">[in] A coluna de documento correspondente a intervalos.</span><span class="sxs-lookup"><span data-stu-id="b83df-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="b83df-111">[in] O tamanho do `ranges` matriz.</span><span class="sxs-lookup"><span data-stu-id="b83df-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="b83df-112">[out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os intervalos.</span><span class="sxs-lookup"><span data-stu-id="b83df-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="b83df-113">[out] Um ponteiro para o buffer que recebe os intervalos.</span><span class="sxs-lookup"><span data-stu-id="b83df-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b83df-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b83df-114">Return Value</span></span>  
 <span data-ttu-id="b83df-115">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b83df-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b83df-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b83df-116">Requirements</span></span>  
 <span data-ttu-id="b83df-117">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b83df-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b83df-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b83df-118">See also</span></span>

- [<span data-ttu-id="b83df-119">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="b83df-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
