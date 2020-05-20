---
title: Método ISymENCUnmanagedMethod::GetSourceExtentInDocument
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
ms.openlocfilehash: 3ac8bb3a20ce82b734a572832a9cbb75fa2568c4
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441897"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="c2c5d-102">Método ISymENCUnmanagedMethod::GetSourceExtentInDocument</span><span class="sxs-lookup"><span data-stu-id="c2c5d-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="c2c5d-103">Obtém a menor linha inicial e a linha final maior para o método em um documento específico.</span><span class="sxs-lookup"><span data-stu-id="c2c5d-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c5d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2c5d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2c5d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2c5d-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="c2c5d-106">no Um ponteiro para o documento.</span><span class="sxs-lookup"><span data-stu-id="c2c5d-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="c2c5d-107">fora Um ponteiro para um `ULONG32` que recebe a linha inicial.</span><span class="sxs-lookup"><span data-stu-id="c2c5d-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="c2c5d-108">fora Um ponteiro para um `ULONG32` que recebe a linha final.</span><span class="sxs-lookup"><span data-stu-id="c2c5d-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2c5d-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c2c5d-109">Return Value</span></span>  
 <span data-ttu-id="c2c5d-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="c2c5d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2c5d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2c5d-111">Requirements</span></span>  
 <span data-ttu-id="c2c5d-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c2c5d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c5d-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="c2c5d-113">See also</span></span>

- [<span data-ttu-id="c2c5d-114">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="c2c5d-114">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
