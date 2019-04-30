---
title: Método ISymUnmanagedReader::GetMethodFromDocumentPosition
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ed13397748b2668c275b221e38bd75c0dd37f03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969176"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="a3ef6-102">Método ISymUnmanagedReader::GetMethodFromDocumentPosition</span><span class="sxs-lookup"><span data-stu-id="a3ef6-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="a3ef6-103">Retorna o método que contém o ponto de interrupção na posição especificada em um documento.</span><span class="sxs-lookup"><span data-stu-id="a3ef6-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3ef6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3ef6-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3ef6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a3ef6-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="a3ef6-106">[in] O documento especificado.</span><span class="sxs-lookup"><span data-stu-id="a3ef6-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="a3ef6-107">[in] A linha do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="a3ef6-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="a3ef6-108">[in] A coluna do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="a3ef6-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a3ef6-109">[out] Um ponteiro para o endereço de uma [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objeto que representa o método que contém o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="a3ef6-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3ef6-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a3ef6-110">Return Value</span></span>  
 <span data-ttu-id="a3ef6-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="a3ef6-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3ef6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3ef6-112">Requirements</span></span>  
 <span data-ttu-id="a3ef6-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a3ef6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ef6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3ef6-114">See also</span></span>

- [<span data-ttu-id="a3ef6-115">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="a3ef6-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
