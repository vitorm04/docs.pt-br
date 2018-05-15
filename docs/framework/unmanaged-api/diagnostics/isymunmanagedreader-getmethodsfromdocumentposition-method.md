---
title: Método ISymUnmanagedReader::GetMethodsFromDocumentPosition
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c84aceb0faabd879911e9595a7f3154065e2191
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="9b100-102">Método ISymUnmanagedReader::GetMethodsFromDocumentPosition</span><span class="sxs-lookup"><span data-stu-id="9b100-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>
<span data-ttu-id="9b100-103">Retorna uma matriz de métodos, cada qual contendo o ponto de interrupção na posição fornecida em um documento.</span><span class="sxs-lookup"><span data-stu-id="9b100-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b100-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b100-104">Syntax</span></span>  
  
```  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b100-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9b100-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="9b100-106">[in] O documento especificado.</span><span class="sxs-lookup"><span data-stu-id="9b100-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="9b100-107">[in] A linha do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="9b100-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="9b100-108">[in] A coluna do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="9b100-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="9b100-109">[in] O tamanho do `pRetVal` matriz.</span><span class="sxs-lookup"><span data-stu-id="9b100-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="9b100-110">[out] Um ponteiro para uma variável que recebe o número de elementos retornados no `pRetVal` matriz.</span><span class="sxs-lookup"><span data-stu-id="9b100-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="9b100-111">[out] Uma matriz de ponteiros, cada qual apontando para um [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objeto que representa um método que contém o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="9b100-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b100-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9b100-112">Return Value</span></span>  
 <span data-ttu-id="9b100-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="9b100-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b100-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b100-114">Requirements</span></span>  
 <span data-ttu-id="9b100-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9b100-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b100-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b100-116">See Also</span></span>  
 [<span data-ttu-id="9b100-117">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="9b100-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
