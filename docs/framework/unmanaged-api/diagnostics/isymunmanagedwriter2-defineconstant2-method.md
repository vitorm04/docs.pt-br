---
title: Método ISymUnmanagedWriter2::DefineConstant2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
ms.openlocfilehash: 70ee853ff657a75dcc4df1454c4354f9d3f8202f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614715"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="12f80-102">Método ISymUnmanagedWriter2::DefineConstant2</span><span class="sxs-lookup"><span data-stu-id="12f80-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="12f80-103">Define um nome para um valor constante.</span><span class="sxs-lookup"><span data-stu-id="12f80-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12f80-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12f80-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12f80-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="12f80-106">no O nome da constante.</span><span class="sxs-lookup"><span data-stu-id="12f80-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="12f80-107">no O valor da constante.</span><span class="sxs-lookup"><span data-stu-id="12f80-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="12f80-108">no O token de metadados da constante.</span><span class="sxs-lookup"><span data-stu-id="12f80-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12f80-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="12f80-109">Return Value</span></span>  
 <span data-ttu-id="12f80-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="12f80-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f80-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12f80-111">Requirements</span></span>  
 <span data-ttu-id="12f80-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="12f80-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f80-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="12f80-113">See also</span></span>

- [<span data-ttu-id="12f80-114">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="12f80-114">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="12f80-115">Método DefineConstant</span><span class="sxs-lookup"><span data-stu-id="12f80-115">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)
