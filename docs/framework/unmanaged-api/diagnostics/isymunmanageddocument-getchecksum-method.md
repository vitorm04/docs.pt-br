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
ms.openlocfilehash: 543bd208e5492460435663c32f276472a763f613
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441091"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="50f8b-102">Método ISymUnmanagedDocument::GetCheckSum</span><span class="sxs-lookup"><span data-stu-id="50f8b-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="50f8b-103">Obtém a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="50f8b-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50f8b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50f8b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50f8b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="50f8b-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="50f8b-106">no O comprimento do buffer fornecido pelo `data` parâmetro</span><span class="sxs-lookup"><span data-stu-id="50f8b-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="50f8b-107">fora O tamanho e o comprimento da soma de verificação, em bytes.</span><span class="sxs-lookup"><span data-stu-id="50f8b-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="50f8b-108">fora O buffer que recebe a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="50f8b-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50f8b-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="50f8b-109">Return Value</span></span>  
 <span data-ttu-id="50f8b-110">S_OK se o método tiver sucesso; caso contrário, um código de erro.</span><span class="sxs-lookup"><span data-stu-id="50f8b-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f8b-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="50f8b-111">See also</span></span>

- [<span data-ttu-id="50f8b-112">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="50f8b-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
