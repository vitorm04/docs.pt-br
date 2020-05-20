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
ms.openlocfilehash: 8015056b110fe8a5b5122b1bc81143980b780047
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614975"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="9646f-102">Método ISymUnmanagedReader::GetMethodFromDocumentPosition</span><span class="sxs-lookup"><span data-stu-id="9646f-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="9646f-103">Retorna o método que contém o ponto de interrupção na posição especificada em um documento.</span><span class="sxs-lookup"><span data-stu-id="9646f-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9646f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9646f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9646f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9646f-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="9646f-106">no O documento especificado.</span><span class="sxs-lookup"><span data-stu-id="9646f-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="9646f-107">no A linha do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="9646f-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="9646f-108">no A coluna do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="9646f-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="9646f-109">fora Um ponteiro para o endereço de um objeto de [interface ISymUnmanagedMethod](isymunmanagedmethod-interface.md) que representa o método que contém o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="9646f-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9646f-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9646f-110">Return Value</span></span>  
 <span data-ttu-id="9646f-111">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="9646f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9646f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9646f-112">Requirements</span></span>  
 <span data-ttu-id="9646f-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9646f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9646f-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="9646f-114">See also</span></span>

- [<span data-ttu-id="9646f-115">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="9646f-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
