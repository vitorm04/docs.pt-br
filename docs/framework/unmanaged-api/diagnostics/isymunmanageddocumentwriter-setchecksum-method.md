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
ms.openlocfilehash: 06a331e24622e0a155d974ca869818a6532baa1f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615534"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="b070b-102">Método ISymUnmanagedDocumentWriter::SetCheckSum</span><span class="sxs-lookup"><span data-stu-id="b070b-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="b070b-103">Define informações de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="b070b-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b070b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b070b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b070b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b070b-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="b070b-106">no O GUID que representa o identificador do algoritmo.</span><span class="sxs-lookup"><span data-stu-id="b070b-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="b070b-107">no Um `ULONG32` que indica o tamanho, em bytes, do `checkSum` buffer.</span><span class="sxs-lookup"><span data-stu-id="b070b-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="b070b-108">no O buffer que armazena as informações de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="b070b-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b070b-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b070b-109">Return Value</span></span>  
 <span data-ttu-id="b070b-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b070b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b070b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b070b-111">Requirements</span></span>  
 <span data-ttu-id="b070b-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b070b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b070b-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="b070b-113">See also</span></span>

- [<span data-ttu-id="b070b-114">Interface ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="b070b-114">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
