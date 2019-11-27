---
title: Método ISymUnmanagedDocument::GetSourceLength
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
ms.openlocfilehash: 0551e8b4f381f76e7bbac06ca7b5f6aea5bbb61f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449155"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="e90a3-102">Método ISymUnmanagedDocument::GetSourceLength</span><span class="sxs-lookup"><span data-stu-id="e90a3-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="e90a3-103">Obtém o comprimento, em bytes, da origem inserida.</span><span class="sxs-lookup"><span data-stu-id="e90a3-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e90a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e90a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e90a3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e90a3-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e90a3-106">fora Um ponteiro para uma variável que indica o comprimento, em bytes, da fonte inserida.</span><span class="sxs-lookup"><span data-stu-id="e90a3-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e90a3-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e90a3-107">Return Value</span></span>  
 <span data-ttu-id="e90a3-108">S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="e90a3-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e90a3-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e90a3-109">See also</span></span>

- [<span data-ttu-id="e90a3-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="e90a3-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
