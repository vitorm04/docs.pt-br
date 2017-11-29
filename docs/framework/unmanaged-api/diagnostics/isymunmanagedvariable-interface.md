---
title: Interface ISymUnmanagedVariable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable
helpviewer_keywords: ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c32d5b66c575a21b4d390cff560b71f93aa31927
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="55621-102">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="55621-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="55621-103">Representa uma variável, como um parâmetro, uma variável local ou um campo.</span><span class="sxs-lookup"><span data-stu-id="55621-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55621-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="55621-104">Methods</span></span>  
  
|<span data-ttu-id="55621-105">Método</span><span class="sxs-lookup"><span data-stu-id="55621-105">Method</span></span>|<span data-ttu-id="55621-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="55621-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55621-107">Método GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="55621-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="55621-108">Obtém o primeiro campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="55621-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="55621-109">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="55621-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="55621-110">Método GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="55621-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="55621-111">Obtém o segundo campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="55621-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="55621-112">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="55621-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="55621-113">Método GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="55621-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="55621-114">Obtém o terceiro campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="55621-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="55621-115">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="55621-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="55621-116">Método GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="55621-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="55621-117">Obtém o tipo de endereço dessa variável.</span><span class="sxs-lookup"><span data-stu-id="55621-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="55621-118">Método GetAttributes</span><span class="sxs-lookup"><span data-stu-id="55621-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="55621-119">Obtém os sinalizadores de atributo para essa variável.</span><span class="sxs-lookup"><span data-stu-id="55621-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="55621-120">Método GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="55621-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="55621-121">Obtém o deslocamento de fim desta variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="55621-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="55621-122">Método GetName</span><span class="sxs-lookup"><span data-stu-id="55621-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="55621-123">Obtém o nome dessa variável.</span><span class="sxs-lookup"><span data-stu-id="55621-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="55621-124">Método GetSignature</span><span class="sxs-lookup"><span data-stu-id="55621-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="55621-125">Obtém a assinatura dessa variável.</span><span class="sxs-lookup"><span data-stu-id="55621-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="55621-126">Método GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="55621-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="55621-127">Obtém o deslocamento do início dessa variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="55621-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55621-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55621-128">Requirements</span></span>  
 <span data-ttu-id="55621-129">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="55621-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55621-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55621-130">See Also</span></span>  
 [<span data-ttu-id="55621-131">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="55621-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
