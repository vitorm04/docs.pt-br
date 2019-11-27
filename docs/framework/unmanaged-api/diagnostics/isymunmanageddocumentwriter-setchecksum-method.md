---
title: Método ISymUnmanagedDocumentWriter::SetCheckSum
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
ms.openlocfilehash: dbf876a514ce106c566a168f688eb3a22d3a1ea2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449052"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="c7d4a-102">Método ISymUnmanagedDocumentWriter::SetCheckSum</span><span class="sxs-lookup"><span data-stu-id="c7d4a-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="c7d4a-103">Define informações de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="c7d4a-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7d4a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7d4a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7d4a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7d4a-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="c7d4a-106">no O GUID que representa o identificador do algoritmo.</span><span class="sxs-lookup"><span data-stu-id="c7d4a-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="c7d4a-107">no Um `ULONG32` que indica o tamanho, em bytes, do buffer de `checkSum`.</span><span class="sxs-lookup"><span data-stu-id="c7d4a-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="c7d4a-108">no O buffer que armazena as informações de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="c7d4a-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7d4a-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c7d4a-109">Return Value</span></span>  
 <span data-ttu-id="c7d4a-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="c7d4a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7d4a-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c7d4a-111">Requirements</span></span>  
 <span data-ttu-id="c7d4a-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c7d4a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d4a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7d4a-113">See also</span></span>

- [<span data-ttu-id="c7d4a-114">Interface ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="c7d4a-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
