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
ms.openlocfilehash: ac3daccfade4f5ae10fe2ebbf83a7a11af34b89b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196977"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="1f7c8-102">Método ISymUnmanagedDocumentWriter::SetCheckSum</span><span class="sxs-lookup"><span data-stu-id="1f7c8-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="1f7c8-103">Define informações de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f7c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1f7c8-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f7c8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1f7c8-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="1f7c8-106">[in] O GUID que representa o identificador de algoritmo.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="1f7c8-107">[in] Um `ULONG32` que indica o tamanho, em bytes, da `checkSum` buffer.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="1f7c8-108">[in] O buffer que armazena as informações de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f7c8-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1f7c8-109">Return Value</span></span>  
 <span data-ttu-id="1f7c8-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f7c8-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1f7c8-111">Requirements</span></span>  
 <span data-ttu-id="1f7c8-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1f7c8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f7c8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f7c8-113">See also</span></span>

- [<span data-ttu-id="1f7c8-114">Interface ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="1f7c8-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
