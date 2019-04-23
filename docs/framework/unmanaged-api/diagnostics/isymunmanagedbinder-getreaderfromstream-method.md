---
title: Método ISymUnmanagedBinder::GetReaderFromStream
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21e147860c6859ea23409de31fed972c4f2bb432
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220910"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="1ebd6-102">Método ISymUnmanagedBinder::GetReaderFromStream</span><span class="sxs-lookup"><span data-stu-id="1ebd6-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="1ebd6-103">Dado uma interface de metadados e um fluxo que contém o repositório de símbolos, retorna a correta [ISymUnmanagedReader](isymunmanagedreader-interface.md) símbolos de estrutura que será lido a depuração do armazenamento de símbolo dado.</span><span class="sxs-lookup"><span data-stu-id="1ebd6-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ebd6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ebd6-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ebd6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ebd6-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="1ebd6-106">[in] Um ponteiro para a interface de importação de metadados.</span><span class="sxs-lookup"><span data-stu-id="1ebd6-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="1ebd6-107">[in] Um ponteiro para o fluxo que contém o repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="1ebd6-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1ebd6-108">[out] Um ponteiro que é definido para retornado [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="1ebd6-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ebd6-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1ebd6-109">Return Value</span></span>  
 <span data-ttu-id="1ebd6-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="1ebd6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ebd6-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ebd6-111">Requirements</span></span>  
 <span data-ttu-id="1ebd6-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1ebd6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ebd6-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ebd6-113">See also</span></span>

- [<span data-ttu-id="1ebd6-114">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="1ebd6-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
