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
ms.openlocfilehash: d05d4451e8fb75829b22e0a1b9c9afcb0607eb8b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610165"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="e0f31-102">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="e0f31-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="e0f31-103">Representa uma variável, como um parâmetro, uma variável local ou um campo.</span><span class="sxs-lookup"><span data-stu-id="e0f31-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0f31-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e0f31-104">Methods</span></span>  
  
|<span data-ttu-id="e0f31-105">Método</span><span class="sxs-lookup"><span data-stu-id="e0f31-105">Method</span></span>|<span data-ttu-id="e0f31-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0f31-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0f31-107">Método GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="e0f31-107">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="e0f31-108">Obtém o primeiro campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="e0f31-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="e0f31-109">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="e0f31-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="e0f31-110">Método GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="e0f31-110">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="e0f31-111">Obtém o segundo campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="e0f31-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="e0f31-112">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="e0f31-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="e0f31-113">Método GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="e0f31-113">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="e0f31-114">Obtém o terceiro campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="e0f31-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="e0f31-115">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="e0f31-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="e0f31-116">Método GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="e0f31-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="e0f31-117">Obtém o tipo de endereço dessa variável.</span><span class="sxs-lookup"><span data-stu-id="e0f31-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="e0f31-118">Método GetAttributes</span><span class="sxs-lookup"><span data-stu-id="e0f31-118">GetAttributes Method</span></span>](isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="e0f31-119">Obtém os sinalizadores de atributo para essa variável.</span><span class="sxs-lookup"><span data-stu-id="e0f31-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="e0f31-120">Método GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="e0f31-120">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="e0f31-121">Obtém o deslocamento final dessa variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="e0f31-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="e0f31-122">Método GetName</span><span class="sxs-lookup"><span data-stu-id="e0f31-122">GetName Method</span></span>](isymunmanagedvariable-getname-method.md)|<span data-ttu-id="e0f31-123">Obtém o nome dessa variável.</span><span class="sxs-lookup"><span data-stu-id="e0f31-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="e0f31-124">Método GetSignature</span><span class="sxs-lookup"><span data-stu-id="e0f31-124">GetSignature Method</span></span>](isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="e0f31-125">Obtém a assinatura dessa variável.</span><span class="sxs-lookup"><span data-stu-id="e0f31-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="e0f31-126">Método GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="e0f31-126">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="e0f31-127">Obtém o deslocamento inicial dessa variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="e0f31-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0f31-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0f31-128">Requirements</span></span>  
 <span data-ttu-id="e0f31-129">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e0f31-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f31-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="e0f31-130">See also</span></span>

- [<span data-ttu-id="e0f31-131">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="e0f31-131">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
