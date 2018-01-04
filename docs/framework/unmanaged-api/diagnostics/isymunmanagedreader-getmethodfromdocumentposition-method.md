---
title: "Método ISymUnmanagedReader::GetMethodFromDocumentPosition"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fa9bfa324254a48d43c4c3df5ecebb91b3f0ae1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="67614-102">Método ISymUnmanagedReader::GetMethodFromDocumentPosition</span><span class="sxs-lookup"><span data-stu-id="67614-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="67614-103">Retorna o método que contém o ponto de interrupção na posição fornecida em um documento.</span><span class="sxs-lookup"><span data-stu-id="67614-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67614-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67614-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67614-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="67614-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="67614-106">[in] O documento especificado.</span><span class="sxs-lookup"><span data-stu-id="67614-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="67614-107">[in] A linha do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="67614-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="67614-108">[in] A coluna do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="67614-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="67614-109">[out] Um ponteiro para o endereço de um [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objeto que representa o método que contém o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="67614-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67614-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="67614-110">Return Value</span></span>  
 <span data-ttu-id="67614-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="67614-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67614-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="67614-112">Requirements</span></span>  
 <span data-ttu-id="67614-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="67614-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67614-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67614-114">See Also</span></span>  
 [<span data-ttu-id="67614-115">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="67614-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
