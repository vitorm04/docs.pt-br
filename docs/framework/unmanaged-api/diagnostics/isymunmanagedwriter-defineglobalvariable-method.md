---
title: Método ISymUnmanagedWriter::DefineGlobalVariable
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
ms.openlocfilehash: 94d1aa5bba87e8ca11b58bdf89a697e1ccf500b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428029"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="4da21-102">Método ISymUnmanagedWriter::DefineGlobalVariable</span><span class="sxs-lookup"><span data-stu-id="4da21-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="4da21-103">Define uma única variável global.</span><span class="sxs-lookup"><span data-stu-id="4da21-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4da21-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4da21-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4da21-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4da21-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="4da21-106">no Um ponteiro para um `WCHAR` que define o nome da variável global.</span><span class="sxs-lookup"><span data-stu-id="4da21-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="4da21-107">no Os atributos da variável global.</span><span class="sxs-lookup"><span data-stu-id="4da21-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="4da21-108">no Um `ULONG32` que indica o tamanho, em caracteres, do buffer de `signature`.</span><span class="sxs-lookup"><span data-stu-id="4da21-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="4da21-109">no A assinatura de variável global.</span><span class="sxs-lookup"><span data-stu-id="4da21-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="4da21-110">no O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="4da21-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="4da21-111">no O primeiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4da21-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="4da21-112">no O segundo endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4da21-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="4da21-113">no O terceiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4da21-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4da21-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="4da21-114">Return Value</span></span>  
 <span data-ttu-id="4da21-115">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="4da21-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4da21-116">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4da21-116">Requirements</span></span>  
 <span data-ttu-id="4da21-117">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4da21-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da21-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4da21-118">See also</span></span>

- [<span data-ttu-id="4da21-119">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="4da21-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="4da21-120">Método DefineLocalVariable</span><span class="sxs-lookup"><span data-stu-id="4da21-120">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="4da21-121">Método DefineGlobalVariable2</span><span class="sxs-lookup"><span data-stu-id="4da21-121">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
