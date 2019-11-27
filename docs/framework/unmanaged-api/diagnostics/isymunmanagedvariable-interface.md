---
title: Interface ISymUnmanagedVariable
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
ms.openlocfilehash: ee57ba14f048032e2cd9d0129089743c0f0304bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445980"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="d8a22-102">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="d8a22-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="d8a22-103">Representa uma variável, como um parâmetro, uma variável local ou um campo.</span><span class="sxs-lookup"><span data-stu-id="d8a22-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8a22-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d8a22-104">Methods</span></span>  
  
|<span data-ttu-id="d8a22-105">Método</span><span class="sxs-lookup"><span data-stu-id="d8a22-105">Method</span></span>|<span data-ttu-id="d8a22-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8a22-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8a22-107">Método GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="d8a22-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="d8a22-108">Obtém o primeiro campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="d8a22-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="d8a22-109">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="d8a22-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="d8a22-110">Método GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="d8a22-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="d8a22-111">Obtém o segundo campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="d8a22-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="d8a22-112">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="d8a22-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="d8a22-113">Método GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="d8a22-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="d8a22-114">Obtém o terceiro campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="d8a22-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="d8a22-115">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="d8a22-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="d8a22-116">Método GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="d8a22-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="d8a22-117">Obtém o tipo de endereço dessa variável.</span><span class="sxs-lookup"><span data-stu-id="d8a22-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="d8a22-118">Método GetAttributes</span><span class="sxs-lookup"><span data-stu-id="d8a22-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="d8a22-119">Obtém os sinalizadores de atributo para essa variável.</span><span class="sxs-lookup"><span data-stu-id="d8a22-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="d8a22-120">Método GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="d8a22-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="d8a22-121">Obtém o deslocamento final dessa variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="d8a22-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="d8a22-122">Método GetName</span><span class="sxs-lookup"><span data-stu-id="d8a22-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="d8a22-123">Obtém o nome dessa variável.</span><span class="sxs-lookup"><span data-stu-id="d8a22-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="d8a22-124">Método GetSignature</span><span class="sxs-lookup"><span data-stu-id="d8a22-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="d8a22-125">Obtém a assinatura dessa variável.</span><span class="sxs-lookup"><span data-stu-id="d8a22-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="d8a22-126">Método GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="d8a22-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="d8a22-127">Obtém o deslocamento inicial dessa variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="d8a22-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8a22-128">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d8a22-128">Requirements</span></span>  
 <span data-ttu-id="d8a22-129">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d8a22-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8a22-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8a22-130">See also</span></span>

- [<span data-ttu-id="d8a22-131">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="d8a22-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
