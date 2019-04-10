---
title: Método ISymUnmanagedDocument::GetCheckSumAlgorithmId
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2df98728eec28ffca05b2e246575fc5c882a078
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229635"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="14108-102">Método ISymUnmanagedDocument::GetCheckSumAlgorithmId</span><span class="sxs-lookup"><span data-stu-id="14108-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="14108-103">Obtém o identificador de algoritmo de soma de verificação ou retorna um GUID de todos os zeros se não houver nenhuma soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="14108-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14108-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14108-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14108-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="14108-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="14108-106">[out] Um ponteiro para uma variável que recebe o identificador de algoritmo de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="14108-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14108-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="14108-107">Return Value</span></span>  
 <span data-ttu-id="14108-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="14108-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14108-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14108-109">See also</span></span>

- [<span data-ttu-id="14108-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="14108-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
