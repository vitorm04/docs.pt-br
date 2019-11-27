---
title: Método ISymUnmanagedWriter2::DefineLocalVariable2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
ms.openlocfilehash: 73f536b4ab98aa596c2395810cb8b616ffd309e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438300"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="b7fd5-102">Método ISymUnmanagedWriter2::DefineLocalVariable2</span><span class="sxs-lookup"><span data-stu-id="b7fd5-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="b7fd5-103">Define uma única variável no escopo léxico atual.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="b7fd5-104">Esse método pode ser chamado várias vezes para uma variável do mesmo nome que tem várias casas em um escopo.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="b7fd5-105">Nesse caso, no entanto, os valores dos parâmetros `startOffset` e `endOffset` não devem se sobrepor.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7fd5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7fd5-106">Syntax</span></span>  
  
```cpp  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7fd5-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7fd5-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b7fd5-108">no O nome da variável local.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="b7fd5-109">no Os atributos da variável local.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="b7fd5-110">no O token de metadados da assinatura.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="b7fd5-111">no O tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="b7fd5-112">no O primeiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="b7fd5-113">no O segundo endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="b7fd5-114">no O terceiro endereço para a especificação de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="b7fd5-115">no O deslocamento de início da variável.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="b7fd5-116">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-116">This parameter is optional.</span></span> <span data-ttu-id="b7fd5-117">Se for 0, esse parâmetro será ignorado e a variável será definida em todo o escopo.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="b7fd5-118">Se for um valor diferente de zero, a variável se enquadrará dentro dos deslocamentos do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="b7fd5-119">no O deslocamento de fim da variável.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="b7fd5-120">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-120">This parameter is optional.</span></span> <span data-ttu-id="b7fd5-121">Se for 0, esse parâmetro será ignorado e a variável será definida em todo o escopo.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="b7fd5-122">Se for um valor diferente de zero, a variável se enquadrará dentro dos deslocamentos do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7fd5-123">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b7fd5-123">Return Value</span></span>  
 <span data-ttu-id="b7fd5-124">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b7fd5-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7fd5-125">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b7fd5-125">Requirements</span></span>  
 <span data-ttu-id="b7fd5-126">**Cabeçalho:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="b7fd5-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7fd5-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7fd5-127">See also</span></span>

- [<span data-ttu-id="b7fd5-128">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="b7fd5-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="b7fd5-129">Método DefineLocalVariable</span><span class="sxs-lookup"><span data-stu-id="b7fd5-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
