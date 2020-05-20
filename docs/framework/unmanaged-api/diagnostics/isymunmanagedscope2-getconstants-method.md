---
title: Método ISymUnmanagedScope2::GetConstants
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: f558d209d13fae93bd3a6f5e0e653afb91371a6a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615326"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="8138e-102">Método ISymUnmanagedScope2::GetConstants</span><span class="sxs-lookup"><span data-stu-id="8138e-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="8138e-103">Obtém as constantes locais definidas neste escopo.</span><span class="sxs-lookup"><span data-stu-id="8138e-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8138e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8138e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8138e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8138e-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="8138e-106">no O comprimento do buffer para o qual o `pcConstants` parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="8138e-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="8138e-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter as constantes.</span><span class="sxs-lookup"><span data-stu-id="8138e-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="8138e-108">fora O buffer que armazena as constantes.</span><span class="sxs-lookup"><span data-stu-id="8138e-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8138e-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8138e-109">Return Value</span></span>  
 <span data-ttu-id="8138e-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="8138e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8138e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8138e-111">Requirements</span></span>  
 <span data-ttu-id="8138e-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8138e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8138e-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="8138e-113">See also</span></span>

- [<span data-ttu-id="8138e-114">Interface ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="8138e-114">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
