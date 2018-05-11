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
ms.openlocfilehash: 660da82f1e6d6d3ea8ba084885331c895bc64542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="5a08a-102">Método ISymUnmanagedDocument::GetCheckSum</span><span class="sxs-lookup"><span data-stu-id="5a08a-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="5a08a-103">Obtém a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="5a08a-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a08a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a08a-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a08a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5a08a-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="5a08a-106">[in] O comprimento do buffer fornecido pelo `data` parâmetro</span><span class="sxs-lookup"><span data-stu-id="5a08a-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="5a08a-107">[out] O tamanho e o comprimento da soma de verificação, em bytes.</span><span class="sxs-lookup"><span data-stu-id="5a08a-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="5a08a-108">[out] O buffer que recebe a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="5a08a-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a08a-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5a08a-109">Return Value</span></span>  
 <span data-ttu-id="5a08a-110">S_OK se o método for bem-sucedido; Caso contrário, um código de erro.</span><span class="sxs-lookup"><span data-stu-id="5a08a-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a08a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a08a-111">See Also</span></span>  
 [<span data-ttu-id="5a08a-112">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="5a08a-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
