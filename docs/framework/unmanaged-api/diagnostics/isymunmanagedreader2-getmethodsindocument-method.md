---
title: Método ISymUnmanagedReader2::GetMethodsInDocument
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38cbea25c485ff517e3448c4de5245ff36fb5b21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594545"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="bbb13-102">Método ISymUnmanagedReader2::GetMethodsInDocument</span><span class="sxs-lookup"><span data-stu-id="bbb13-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="bbb13-103">Obtém todos os métodos que tem informações de linha no documento fornecido.</span><span class="sxs-lookup"><span data-stu-id="bbb13-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbb13-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbb13-104">Syntax</span></span>  
  
```  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbb13-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bbb13-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="bbb13-106">[in] Um ponteiro para o documento.</span><span class="sxs-lookup"><span data-stu-id="bbb13-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="bbb13-107">[in] Um `ULONG32` que indica o tamanho do `pRetVal` matriz.</span><span class="sxs-lookup"><span data-stu-id="bbb13-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="bbb13-108">[out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os métodos.</span><span class="sxs-lookup"><span data-stu-id="bbb13-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="bbb13-109">[out] Um ponteiro para o buffer que recebe os métodos.</span><span class="sxs-lookup"><span data-stu-id="bbb13-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbb13-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bbb13-110">Return Value</span></span>  
 <span data-ttu-id="bbb13-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="bbb13-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbb13-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bbb13-112">Requirements</span></span>  
 <span data-ttu-id="bbb13-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bbb13-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbb13-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbb13-114">See also</span></span>
- [<span data-ttu-id="bbb13-115">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="bbb13-115">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
