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
ms.openlocfilehash: 0ec3f94d290423130e3718b32cd8058f59d797d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694510"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="9a992-102">Método ISymUnmanagedWriter::RemapToken</span><span class="sxs-lookup"><span data-stu-id="9a992-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="9a992-103">Notifica o gravador de símbolo que um token de metadados foi remapeado, pois os metadados foi emitido.</span><span class="sxs-lookup"><span data-stu-id="9a992-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="9a992-104">Se o gravador de símbolo tiver armazenado o token antigo no repositório de símbolos, ele deve atualizar que o token armazenado com o novo valor, ou ele deve salvar o mapa para o leitor de símbolo correspondente remapear durante a fase de leitura.</span><span class="sxs-lookup"><span data-stu-id="9a992-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a992-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a992-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a992-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a992-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="9a992-107">[in] O token de metadados que remapeado.</span><span class="sxs-lookup"><span data-stu-id="9a992-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="9a992-108">[in] O novo token de metadados para o qual `oldToken` remapeado.</span><span class="sxs-lookup"><span data-stu-id="9a992-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a992-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9a992-109">Return Value</span></span>  
 <span data-ttu-id="9a992-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="9a992-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a992-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a992-111">Requirements</span></span>  
 <span data-ttu-id="9a992-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9a992-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a992-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a992-113">See also</span></span>
- [<span data-ttu-id="9a992-114">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="9a992-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
