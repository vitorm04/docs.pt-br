---
title: Método ISymUnmanagedMethod::GetSourceStartEnd
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d32e3ac0ff3179a9bb32f82e5ca33fd89c4ec410
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151184"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="ea4c9-102">Método ISymUnmanagedMethod::GetSourceStartEnd</span><span class="sxs-lookup"><span data-stu-id="ea4c9-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="ea4c9-103">Obtém as posições inicial e final no documento para a fonte deste método.</span><span class="sxs-lookup"><span data-stu-id="ea4c9-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="ea4c9-104">A primeira posição de matriz é o início e a segunda posição de matriz é o fim.</span><span class="sxs-lookup"><span data-stu-id="ea4c9-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea4c9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea4c9-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea4c9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ea4c9-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="ea4c9-107">[in] O inicial e final documentos de origem.</span><span class="sxs-lookup"><span data-stu-id="ea4c9-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="ea4c9-108">[in] Documentos de origem inicial e final de linhas nas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="ea4c9-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="ea4c9-109">[in] Documentos de origem inicial e final colunas nas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="ea4c9-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ea4c9-110">[out] `true` se as posições foram definidas, caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="ea4c9-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea4c9-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ea4c9-111">Return Value</span></span>  
 <span data-ttu-id="ea4c9-112">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="ea4c9-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea4c9-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea4c9-113">Requirements</span></span>  
 <span data-ttu-id="ea4c9-114">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ea4c9-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea4c9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea4c9-115">See also</span></span>

- [<span data-ttu-id="ea4c9-116">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="ea4c9-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
