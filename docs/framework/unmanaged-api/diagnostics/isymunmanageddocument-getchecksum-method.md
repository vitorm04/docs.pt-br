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
ms.openlocfilehash: a60bf279c143559e7410d8dfd8213d3da1d05a6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939900"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="eee17-102">Método ISymUnmanagedDocument::GetCheckSum</span><span class="sxs-lookup"><span data-stu-id="eee17-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="eee17-103">Obtém a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="eee17-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eee17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eee17-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eee17-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eee17-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="eee17-106">[in] O comprimento do buffer fornecido pelo `data` parâmetro</span><span class="sxs-lookup"><span data-stu-id="eee17-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="eee17-107">[out] O tamanho e o comprimento da soma de verificação, em bytes.</span><span class="sxs-lookup"><span data-stu-id="eee17-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="eee17-108">[out] O buffer que recebe a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="eee17-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eee17-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="eee17-109">Return Value</span></span>  
 <span data-ttu-id="eee17-110">S_OK se o método for bem-sucedido; Caso contrário, um código de erro.</span><span class="sxs-lookup"><span data-stu-id="eee17-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee17-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eee17-111">See also</span></span>

- [<span data-ttu-id="eee17-112">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="eee17-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
