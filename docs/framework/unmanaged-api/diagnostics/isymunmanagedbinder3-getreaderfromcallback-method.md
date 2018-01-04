---
title: "Método ISymUnmanagedBinder3::GetReaderFromCallback"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder3.GetReaderFromCallback
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 648559936259e7412011f9fb7613bd0e938e4ecb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="29e26-102">Método ISymUnmanagedBinder3::GetReaderFromCallback</span><span class="sxs-lookup"><span data-stu-id="29e26-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="29e26-103">Permite que o usuário implementa ou fornecer por meio do retorno de chamada ou uma `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` para obter as informações de diretório de depuração da memória.</span><span class="sxs-lookup"><span data-stu-id="29e26-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29e26-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29e26-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29e26-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29e26-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="29e26-106">[in] Um ponteiro para a interface de importação de metadados.</span><span class="sxs-lookup"><span data-stu-id="29e26-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="29e26-107">[in] Um ponteiro para o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="29e26-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="29e26-108">[in] Um ponteiro para o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="29e26-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="29e26-109">[in] Um valor de [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeração que especifica a política a ser usado ao fazer uma pesquisa de um leitor de símbolo.</span><span class="sxs-lookup"><span data-stu-id="29e26-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="29e26-110">[in] Um ponteiro para a função de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="29e26-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="29e26-111">[out] Um ponteiro que está definido para retornado [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="29e26-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29e26-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="29e26-112">Return Value</span></span>  
 <span data-ttu-id="29e26-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="29e26-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29e26-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29e26-114">Requirements</span></span>  
 <span data-ttu-id="29e26-115">**Cabeçalho:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="29e26-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e26-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29e26-116">See Also</span></span>  
 [<span data-ttu-id="29e26-117">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="29e26-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
