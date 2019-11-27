---
title: Método ISymUnmanagedWriter3::Commit
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
ms.openlocfilehash: 5985257a186839a297c245b23f093f0b18a798fe
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438270"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="c21ac-102">Método ISymUnmanagedWriter3::Commit</span><span class="sxs-lookup"><span data-stu-id="c21ac-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="c21ac-103">Confirma as alterações gravadas até o fluxo.</span><span class="sxs-lookup"><span data-stu-id="c21ac-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c21ac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c21ac-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c21ac-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c21ac-105">Return Value</span></span>  
 <span data-ttu-id="c21ac-106">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="c21ac-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c21ac-107">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c21ac-107">Requirements</span></span>  
 <span data-ttu-id="c21ac-108">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c21ac-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c21ac-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c21ac-109">See also</span></span>

- [<span data-ttu-id="c21ac-110">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="c21ac-110">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
