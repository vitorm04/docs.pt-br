---
title: Método ISymENCUnmanagedMethod::GetFileNameFromOffset
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
ms.openlocfilehash: 74002ce9c76eebaa3ea5860b09cd3e7c9a884f8d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448661"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="8ff72-102">Método ISymENCUnmanagedMethod::GetFileNameFromOffset</span><span class="sxs-lookup"><span data-stu-id="8ff72-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="8ff72-103">Obtém o nome do arquivo da linha associada a um deslocamento.</span><span class="sxs-lookup"><span data-stu-id="8ff72-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff72-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ff72-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ff72-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ff72-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="8ff72-106">no Um `ULONG32` que contém o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="8ff72-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8ff72-107">no Um `ULONG32` que indica o tamanho do buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="8ff72-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8ff72-108">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter os nomes de arquivo.</span><span class="sxs-lookup"><span data-stu-id="8ff72-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="8ff72-109">fora O buffer que contém os nomes de arquivo.</span><span class="sxs-lookup"><span data-stu-id="8ff72-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ff72-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8ff72-110">Return Value</span></span>  
 <span data-ttu-id="8ff72-111">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="8ff72-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ff72-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8ff72-112">Requirements</span></span>  
 <span data-ttu-id="8ff72-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8ff72-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff72-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ff72-114">See also</span></span>

- [<span data-ttu-id="8ff72-115">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="8ff72-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
