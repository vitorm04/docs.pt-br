---
title: Método ISymUnmanagedENCUpdate::GetLocalVariableCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
ms.openlocfilehash: d04c9865d8272bf8d04080f6049ddfb1d4c643bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614572"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="4957a-102">Método ISymUnmanagedENCUpdate::GetLocalVariableCount</span><span class="sxs-lookup"><span data-stu-id="4957a-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="4957a-103">Obtém o número de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="4957a-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4957a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4957a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4957a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4957a-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="4957a-106">no O token de metadados dos métodos.</span><span class="sxs-lookup"><span data-stu-id="4957a-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="4957a-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o número de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="4957a-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4957a-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="4957a-108">Return Value</span></span>  
 <span data-ttu-id="4957a-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="4957a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4957a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4957a-110">Requirements</span></span>  
 <span data-ttu-id="4957a-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4957a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4957a-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="4957a-112">See also</span></span>

- [<span data-ttu-id="4957a-113">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="4957a-113">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
