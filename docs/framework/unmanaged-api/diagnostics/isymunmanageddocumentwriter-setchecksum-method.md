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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3343710fbe4f1aba8c38e46a0a720f78944a1c10
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776926"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="18a3b-102">Método ISymUnmanagedDocumentWriter::SetCheckSum</span><span class="sxs-lookup"><span data-stu-id="18a3b-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="18a3b-103">Define informações de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="18a3b-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18a3b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18a3b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18a3b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="18a3b-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="18a3b-106">[in] O GUID que representa o identificador de algoritmo.</span><span class="sxs-lookup"><span data-stu-id="18a3b-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="18a3b-107">[in] Um `ULONG32` que indica o tamanho, em bytes, da `checkSum` buffer.</span><span class="sxs-lookup"><span data-stu-id="18a3b-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="18a3b-108">[in] O buffer que armazena as informações de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="18a3b-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18a3b-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="18a3b-109">Return Value</span></span>  
 <span data-ttu-id="18a3b-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="18a3b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18a3b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="18a3b-111">Requirements</span></span>  
 <span data-ttu-id="18a3b-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="18a3b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a3b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18a3b-113">See also</span></span>

- [<span data-ttu-id="18a3b-114">Interface ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="18a3b-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
