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
ms.openlocfilehash: bba0fc039c403d45e8a5b60f2b0231eb24226280
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614949"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="f9d16-102">Método ISymUnmanagedReader::GetMethodsFromDocumentPosition</span><span class="sxs-lookup"><span data-stu-id="f9d16-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>
<span data-ttu-id="f9d16-103">Retorna uma matriz de métodos, cada um contendo o ponto de interrupção na posição especificada em um documento.</span><span class="sxs-lookup"><span data-stu-id="f9d16-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9d16-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9d16-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9d16-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9d16-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="f9d16-106">no O documento especificado.</span><span class="sxs-lookup"><span data-stu-id="f9d16-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="f9d16-107">no A linha do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="f9d16-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="f9d16-108">no A coluna do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="f9d16-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="f9d16-109">no O tamanho da `pRetVal` matriz.</span><span class="sxs-lookup"><span data-stu-id="f9d16-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="f9d16-110">fora Um ponteiro para uma variável que recebe o número de elementos retornados na `pRetVal` matriz.</span><span class="sxs-lookup"><span data-stu-id="f9d16-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="f9d16-111">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) que representa um método que contém o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="f9d16-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9d16-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f9d16-112">Return Value</span></span>  
 <span data-ttu-id="f9d16-113">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="f9d16-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9d16-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9d16-114">Requirements</span></span>  
 <span data-ttu-id="f9d16-115">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f9d16-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9d16-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="f9d16-116">See also</span></span>

- [<span data-ttu-id="f9d16-117">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="f9d16-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
