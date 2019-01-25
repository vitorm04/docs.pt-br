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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 50c38c5a9e1799a460c5be1f7234b36968dc3da2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706885"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="16d05-102">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="16d05-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="16d05-103">Representa uma variável, como um parâmetro, uma variável local ou um campo.</span><span class="sxs-lookup"><span data-stu-id="16d05-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16d05-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="16d05-104">Methods</span></span>  
  
|<span data-ttu-id="16d05-105">Método</span><span class="sxs-lookup"><span data-stu-id="16d05-105">Method</span></span>|<span data-ttu-id="16d05-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="16d05-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="16d05-107">Método GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="16d05-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="16d05-108">Obtém o primeiro campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="16d05-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="16d05-109">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="16d05-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="16d05-110">Método GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="16d05-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="16d05-111">Obtém o segundo campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="16d05-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="16d05-112">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="16d05-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="16d05-113">Método GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="16d05-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="16d05-114">Obtém o terceiro campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="16d05-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="16d05-115">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="16d05-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="16d05-116">Método GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="16d05-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="16d05-117">Obtém o tipo de endereço dessa variável.</span><span class="sxs-lookup"><span data-stu-id="16d05-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="16d05-118">Método GetAttributes</span><span class="sxs-lookup"><span data-stu-id="16d05-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="16d05-119">Obtém os sinalizadores de atributo para essa variável.</span><span class="sxs-lookup"><span data-stu-id="16d05-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="16d05-120">Método GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="16d05-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="16d05-121">Obtém o deslocamento final dessa variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="16d05-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="16d05-122">Método GetName</span><span class="sxs-lookup"><span data-stu-id="16d05-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="16d05-123">Obtém o nome dessa variável.</span><span class="sxs-lookup"><span data-stu-id="16d05-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="16d05-124">Método GetSignature</span><span class="sxs-lookup"><span data-stu-id="16d05-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="16d05-125">Obtém a assinatura dessa variável.</span><span class="sxs-lookup"><span data-stu-id="16d05-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="16d05-126">Método GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="16d05-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="16d05-127">Obtém o deslocamento do início dessa variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="16d05-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16d05-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16d05-128">Requirements</span></span>  
 <span data-ttu-id="16d05-129">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="16d05-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16d05-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16d05-130">See also</span></span>
- [<span data-ttu-id="16d05-131">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="16d05-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
