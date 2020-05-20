---
title: Método ISymUnmanagedScope::GetLocalCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
ms.openlocfilehash: 9ffba23e3821c48c9b0708e4b6b617db4ddc5959
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83611257"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="22ea9-102">Método ISymUnmanagedScope::GetLocalCount</span><span class="sxs-lookup"><span data-stu-id="22ea9-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="22ea9-103">Obtém uma contagem das variáveis locais definidas neste escopo.</span><span class="sxs-lookup"><span data-stu-id="22ea9-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22ea9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22ea9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22ea9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="22ea9-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="22ea9-106">fora Um ponteiro para um `ULONG32` que recebe a contagem de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="22ea9-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22ea9-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="22ea9-107">Return Value</span></span>  
 <span data-ttu-id="22ea9-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="22ea9-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22ea9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22ea9-109">Requirements</span></span>  
 <span data-ttu-id="22ea9-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="22ea9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ea9-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="22ea9-111">See also</span></span>

- [<span data-ttu-id="22ea9-112">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="22ea9-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
