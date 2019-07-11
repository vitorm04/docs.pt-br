---
title: Método ISymUnmanagedDocument::GetCheckSum
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b34f985f199542612bcdb9b30ebae28649438e1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776773"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="b21b1-102">Método ISymUnmanagedDocument::GetCheckSum</span><span class="sxs-lookup"><span data-stu-id="b21b1-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="b21b1-103">Obtém a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="b21b1-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b21b1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b21b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b21b1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b21b1-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="b21b1-106">[in] O comprimento do buffer fornecido pelo `data` parâmetro</span><span class="sxs-lookup"><span data-stu-id="b21b1-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="b21b1-107">[out] O tamanho e o comprimento da soma de verificação, em bytes.</span><span class="sxs-lookup"><span data-stu-id="b21b1-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="b21b1-108">[out] O buffer que recebe a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="b21b1-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b21b1-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b21b1-109">Return Value</span></span>  
 <span data-ttu-id="b21b1-110">S_OK se o método for bem-sucedido; Caso contrário, um código de erro.</span><span class="sxs-lookup"><span data-stu-id="b21b1-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b21b1-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b21b1-111">See also</span></span>

- [<span data-ttu-id="b21b1-112">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="b21b1-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
