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
ms.openlocfilehash: cba4af737cc6a6441d38ba0f940fffe54f5c4f09
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449066"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="f9ad5-102">Método ISymUnmanagedENCUpdate::GetLocalVariableCount</span><span class="sxs-lookup"><span data-stu-id="f9ad5-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="f9ad5-103">Obtém o número de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="f9ad5-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9ad5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9ad5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9ad5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9ad5-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="f9ad5-106">no O token de metadados dos métodos.</span><span class="sxs-lookup"><span data-stu-id="f9ad5-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="f9ad5-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o número de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="f9ad5-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9ad5-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f9ad5-108">Return Value</span></span>  
 <span data-ttu-id="f9ad5-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="f9ad5-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9ad5-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f9ad5-110">Requirements</span></span>  
 <span data-ttu-id="f9ad5-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f9ad5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ad5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9ad5-112">See also</span></span>

- [<span data-ttu-id="f9ad5-113">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="f9ad5-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
