---
title: Método ISymUnmanagedMethod::GetOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a42dc624d4de9cddebad287f6d90590f96b30272
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223648"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="e0990-102">Método ISymUnmanagedMethod::GetOffset</span><span class="sxs-lookup"><span data-stu-id="e0990-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="e0990-103">Retorna o deslocamento dentro desse método que corresponde a uma determinada posição dentro de um documento.</span><span class="sxs-lookup"><span data-stu-id="e0990-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0990-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0990-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0990-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e0990-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="e0990-106">[in] Um ponteiro para o documento para o qual o deslocamento é solicitado.</span><span class="sxs-lookup"><span data-stu-id="e0990-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="e0990-107">[in] A linha de documento para o qual o deslocamento é solicitado.</span><span class="sxs-lookup"><span data-stu-id="e0990-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="e0990-108">[in] A coluna de documento para o qual o deslocamento é solicitado.</span><span class="sxs-lookup"><span data-stu-id="e0990-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e0990-109">[out] Um ponteiro para um `ULONG32` que recebe os deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="e0990-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0990-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e0990-110">Return Value</span></span>  
 <span data-ttu-id="e0990-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="e0990-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0990-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0990-112">Requirements</span></span>  
 <span data-ttu-id="e0990-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e0990-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0990-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0990-114">See also</span></span>

- [<span data-ttu-id="e0990-115">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="e0990-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
