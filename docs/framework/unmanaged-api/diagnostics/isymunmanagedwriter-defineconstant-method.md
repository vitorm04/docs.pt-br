---
title: Método ISymUnmanagedWriter::DefineConstant
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
ms.openlocfilehash: 200e68abb3f176c267045bf2a5e7e35d18400519
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610087"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="fefd5-102">Método ISymUnmanagedWriter::DefineConstant</span><span class="sxs-lookup"><span data-stu-id="fefd5-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="fefd5-103">Define um nome para um valor constante.</span><span class="sxs-lookup"><span data-stu-id="fefd5-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fefd5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fefd5-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fefd5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fefd5-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="fefd5-106">no Um ponteiro para um `WCHAR` que define o nome da constante.</span><span class="sxs-lookup"><span data-stu-id="fefd5-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="fefd5-107">no O valor da constante.</span><span class="sxs-lookup"><span data-stu-id="fefd5-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="fefd5-108">no O tamanho da `signature` matriz.</span><span class="sxs-lookup"><span data-stu-id="fefd5-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="fefd5-109">no A assinatura de tipo para a constante.</span><span class="sxs-lookup"><span data-stu-id="fefd5-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fefd5-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="fefd5-110">Return Value</span></span>  
 <span data-ttu-id="fefd5-111">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="fefd5-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fefd5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fefd5-112">Requirements</span></span>  
 <span data-ttu-id="fefd5-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fefd5-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fefd5-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="fefd5-114">See also</span></span>

- [<span data-ttu-id="fefd5-115">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="fefd5-115">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="fefd5-116">Método DefineConstant2</span><span class="sxs-lookup"><span data-stu-id="fefd5-116">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)
