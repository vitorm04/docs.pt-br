---
title: "Método ISymUnmanagedBinder::GetReaderFromStream"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 36d4d0067cd638eb39ce82eb042242b7b08d3647
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="d0a4e-102">Método ISymUnmanagedBinder::GetReaderFromStream</span><span class="sxs-lookup"><span data-stu-id="d0a4e-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="d0a4e-103">Dado uma interface de metadados e um fluxo que contém o repositório de símbolos, retorna o correto [ISymUnmanagedReader](isymunmanagedreader-interface.md) símbolos de estrutura que lerá a depuração do armazenamento de símbolo dado.</span><span class="sxs-lookup"><span data-stu-id="d0a4e-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0a4e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0a4e-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0a4e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d0a4e-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="d0a4e-106">[in] Um ponteiro para a interface de importação de metadados.</span><span class="sxs-lookup"><span data-stu-id="d0a4e-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="d0a4e-107">[in] Um ponteiro para o fluxo que contém o repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="d0a4e-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d0a4e-108">[out] Um ponteiro que está definido para retornado [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="d0a4e-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0a4e-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d0a4e-109">Return Value</span></span>  
 <span data-ttu-id="d0a4e-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="d0a4e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0a4e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0a4e-111">Requirements</span></span>  
 <span data-ttu-id="d0a4e-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d0a4e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0a4e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0a4e-113">See Also</span></span>  
 [<span data-ttu-id="d0a4e-114">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="d0a4e-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
