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
ms.openlocfilehash: 6d88e9279f70c36fd8a9c626972e33305cded5fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="74a4f-102">Método ISymUnmanagedMethod::GetOffset</span><span class="sxs-lookup"><span data-stu-id="74a4f-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="74a4f-103">Retorna o deslocamento dentro desse método que corresponde à posição especificada dentro de um documento.</span><span class="sxs-lookup"><span data-stu-id="74a4f-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74a4f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74a4f-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74a4f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="74a4f-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="74a4f-106">[in] Um ponteiro para o documento para o qual o deslocamento é solicitado.</span><span class="sxs-lookup"><span data-stu-id="74a4f-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="74a4f-107">[in] A linha do documento para o qual o deslocamento é solicitado.</span><span class="sxs-lookup"><span data-stu-id="74a4f-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="74a4f-108">[in] A coluna de documento para o qual o deslocamento é solicitado.</span><span class="sxs-lookup"><span data-stu-id="74a4f-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="74a4f-109">[out] Um ponteiro para um `ULONG32` que recebe os deslocamentos.</span><span class="sxs-lookup"><span data-stu-id="74a4f-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74a4f-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="74a4f-110">Return Value</span></span>  
 <span data-ttu-id="74a4f-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="74a4f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74a4f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74a4f-112">Requirements</span></span>  
 <span data-ttu-id="74a4f-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="74a4f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a4f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74a4f-114">See Also</span></span>  
 [<span data-ttu-id="74a4f-115">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="74a4f-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
