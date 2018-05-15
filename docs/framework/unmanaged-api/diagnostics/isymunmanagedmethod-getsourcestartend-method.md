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
ms.openlocfilehash: 1e15bab136540c73f8e1cff0e6bb52ec1d6c0063
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="3e395-102">Método ISymUnmanagedMethod::GetSourceStartEnd</span><span class="sxs-lookup"><span data-stu-id="3e395-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="3e395-103">Obtém as posições de documento de início e término para a fonte deste método.</span><span class="sxs-lookup"><span data-stu-id="3e395-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="3e395-104">A primeira posição de matriz é o início e a segunda posição de matriz é o final.</span><span class="sxs-lookup"><span data-stu-id="3e395-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e395-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e395-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e395-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3e395-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="3e395-107">[in] O início e término documentos de origem.</span><span class="sxs-lookup"><span data-stu-id="3e395-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="3e395-108">[in] Documentos de origem inicial e final de linhas no correspondente.</span><span class="sxs-lookup"><span data-stu-id="3e395-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="3e395-109">[in] Documentos de origem inicial e final de colunas no correspondente.</span><span class="sxs-lookup"><span data-stu-id="3e395-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="3e395-110">[out] `true` se posições foram definidos; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="3e395-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e395-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3e395-111">Return Value</span></span>  
 <span data-ttu-id="3e395-112">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="3e395-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e395-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e395-113">Requirements</span></span>  
 <span data-ttu-id="3e395-114">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3e395-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e395-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e395-115">See Also</span></span>  
 [<span data-ttu-id="3e395-116">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="3e395-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
