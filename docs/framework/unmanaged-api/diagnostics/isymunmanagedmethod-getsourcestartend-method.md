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
ms.openlocfilehash: 25e797fdf563a01ab727f16e7173eec2552eeb27
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614416"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="9561b-102">Método ISymUnmanagedMethod::GetSourceStartEnd</span><span class="sxs-lookup"><span data-stu-id="9561b-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="9561b-103">Obtém as posições do documento inicial e final da origem deste método.</span><span class="sxs-lookup"><span data-stu-id="9561b-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="9561b-104">A primeira posição da matriz é o início e a segunda posição da matriz é o final.</span><span class="sxs-lookup"><span data-stu-id="9561b-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9561b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9561b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9561b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9561b-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="9561b-107">no Os documentos de origem inicial e final.</span><span class="sxs-lookup"><span data-stu-id="9561b-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="9561b-108">no As linhas inicial e final nos documentos de origem correspondentes.</span><span class="sxs-lookup"><span data-stu-id="9561b-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="9561b-109">no As colunas inicial e final nos documentos de origem correspondentes.</span><span class="sxs-lookup"><span data-stu-id="9561b-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="9561b-110">[fora] `true` Se as posições foram definidas; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="9561b-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9561b-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9561b-111">Return Value</span></span>  
 <span data-ttu-id="9561b-112">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="9561b-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9561b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9561b-113">Requirements</span></span>  
 <span data-ttu-id="9561b-114">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9561b-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9561b-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="9561b-115">See also</span></span>

- [<span data-ttu-id="9561b-116">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="9561b-116">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
