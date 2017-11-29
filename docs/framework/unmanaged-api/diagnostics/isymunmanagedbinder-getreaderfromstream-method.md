---
title: "Método ISymUnmanagedBinder::GetReaderFromStream"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder.GetReaderFromStream
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 96bd12b69b84537415ddf2e0ae992ec179f32493
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="c3e4f-102">Método ISymUnmanagedBinder::GetReaderFromStream</span><span class="sxs-lookup"><span data-stu-id="c3e4f-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="c3e4f-103">Dado uma interface de metadados e um fluxo que contém o repositório de símbolos, retorna o correto <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> símbolos de estrutura que lerá a depuração do armazenamento de símbolo dado.</span><span class="sxs-lookup"><span data-stu-id="c3e4f-103">Given a metadata interface and a stream that contains the symbol store, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3e4f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3e4f-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3e4f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3e4f-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="c3e4f-106">[in] Um ponteiro para a interface de importação de metadados.</span><span class="sxs-lookup"><span data-stu-id="c3e4f-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="c3e4f-107">[in] Um ponteiro para o fluxo que contém o repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="c3e4f-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="c3e4f-108">[out] Um ponteiro que está definido para retornado <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span><span class="sxs-lookup"><span data-stu-id="c3e4f-108">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3e4f-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c3e4f-109">Return Value</span></span>  
 <span data-ttu-id="c3e4f-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="c3e4f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3e4f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3e4f-111">Requirements</span></span>  
 <span data-ttu-id="c3e4f-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c3e4f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3e4f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3e4f-113">See Also</span></span>  
 [<span data-ttu-id="c3e4f-114">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="c3e4f-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
