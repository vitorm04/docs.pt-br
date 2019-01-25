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
ms.openlocfilehash: d7a3fcd34f8cab6fa3c2949a4ee3270189b3dc77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730029"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="39347-102">Método ISymUnmanagedDocumentWriter::SetCheckSum</span><span class="sxs-lookup"><span data-stu-id="39347-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="39347-103">Define informações de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="39347-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39347-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39347-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39347-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="39347-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="39347-106">[in] O GUID que representa o identificador de algoritmo.</span><span class="sxs-lookup"><span data-stu-id="39347-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="39347-107">[in] Um `ULONG32` que indica o tamanho, em bytes, da `checkSum` buffer.</span><span class="sxs-lookup"><span data-stu-id="39347-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="39347-108">[in] O buffer que armazena as informações de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="39347-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39347-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="39347-109">Return Value</span></span>  
 <span data-ttu-id="39347-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="39347-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39347-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="39347-111">Requirements</span></span>  
 <span data-ttu-id="39347-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="39347-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39347-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39347-113">See also</span></span>
- [<span data-ttu-id="39347-114">Interface ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="39347-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
