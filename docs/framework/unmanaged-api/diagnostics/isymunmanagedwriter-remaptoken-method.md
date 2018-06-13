---
title: Método ISymUnmanagedWriter::RemapToken
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f37630c9631e2e76d9b98730b84086b8b86ec55d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427828"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="5c24c-102">Método ISymUnmanagedWriter::RemapToken</span><span class="sxs-lookup"><span data-stu-id="5c24c-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="5c24c-103">Notifica o gravador de símbolo que um token de metadados foi remapeado como os metadados foi emitido.</span><span class="sxs-lookup"><span data-stu-id="5c24c-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="5c24c-104">Se o gravador de símbolo armazenou o token antigo no repositório de símbolos, ele deverá atualizar que o token armazenado com o novo valor, ou salve o mapa para o leitor de símbolo correspondente remapear durante a fase de leitura.</span><span class="sxs-lookup"><span data-stu-id="5c24c-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c24c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c24c-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c24c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5c24c-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="5c24c-107">[in] O token de metadados que remapeado.</span><span class="sxs-lookup"><span data-stu-id="5c24c-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="5c24c-108">[in] O novo token de metadados para o qual `oldToken` remapeado.</span><span class="sxs-lookup"><span data-stu-id="5c24c-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c24c-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5c24c-109">Return Value</span></span>  
 <span data-ttu-id="5c24c-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="5c24c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c24c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c24c-111">Requirements</span></span>  
 <span data-ttu-id="5c24c-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5c24c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c24c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c24c-113">See Also</span></span>  
 [<span data-ttu-id="5c24c-114">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="5c24c-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
