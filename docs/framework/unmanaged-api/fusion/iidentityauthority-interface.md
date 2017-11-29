---
title: Interface IIdentityAuthority
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IIdentityAuthority
api_location: fusion.dll
api_type: COM
f1_keywords: IIdentityAuthority
helpviewer_keywords: IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c3f38d932fa0376186e2c22232d21857d5fa128f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="f024a-102">Interface IIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="f024a-102">IIdentityAuthority Interface</span></span>
<span data-ttu-id="f024a-103">Gerencia chaves de identidade para objetos de código.</span><span class="sxs-lookup"><span data-stu-id="f024a-103">Manages identity keys for code objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f024a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f024a-104">Methods</span></span>  
  
|<span data-ttu-id="f024a-105">Método</span><span class="sxs-lookup"><span data-stu-id="f024a-105">Method</span></span>|<span data-ttu-id="f024a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f024a-106">Description</span></span>|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="f024a-107">Obtém um valor que indica se os dois especificada [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instâncias são iguais.</span><span class="sxs-lookup"><span data-stu-id="f024a-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="f024a-108">Obtém um valor que indica se os dois especificada [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instâncias são iguais.</span><span class="sxs-lookup"><span data-stu-id="f024a-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="f024a-109">Obtém um valor que indica se as duas representações de identidade de definição de cadeia de caracteres especificada são iguais.</span><span class="sxs-lookup"><span data-stu-id="f024a-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|  
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="f024a-110">Obtém um valor que indica se as duas representações de identidade de referência de cadeia de caracteres especificada são iguais.</span><span class="sxs-lookup"><span data-stu-id="f024a-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|  
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="f024a-111">Obtém um ponteiro para um novo `IDefinitionIdentity` instância que representa o objeto de código no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="f024a-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="f024a-112">Obtém um ponteiro para um novo `IReferenceIdentity` instância que representa o objeto de código no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="f024a-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="f024a-113">Obtém uma versão de cadeia de caracteres formatada especificada `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="f024a-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="f024a-114">Preenche o buffer de caractere largo especificado com uma versão de cadeia de caracteres especificada `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="f024a-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="f024a-115">Obtém um valor que indica se o especificado `IDefinitionIdentity` e `IReferenceIdentity` instâncias façam referência ao mesmo objeto de código.</span><span class="sxs-lookup"><span data-stu-id="f024a-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="f024a-116">Obtém um valor que indica se as cadeias de caracteres especificadas se referem ao mesmo objeto de código.</span><span class="sxs-lookup"><span data-stu-id="f024a-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|  
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="f024a-117">Obtém um ponteiro para uma chave de cadeia de caracteres recém-criado especificado `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="f024a-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="f024a-118">Obtém um ponteiro para uma chave de cadeia de caracteres recém-criado especificado `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="f024a-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="f024a-119">Obtém um valor de hash especificado `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="f024a-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::HashReference`|<span data-ttu-id="f024a-120">Obtém um valor de hash especificado `IreferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="f024a-120">Gets a hash value for the specified `IreferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="f024a-121">Obtém uma versão de cadeia de caracteres formatada especificada `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="f024a-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="f024a-122">Preenche o buffer de caractere largo especificado com uma versão de cadeia de caracteres especificada `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="f024a-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="f024a-123">Obtém um ponteiro de interface para um `IDefinitionIdentity` cadeia de caracteres formatada de instância gerada especificado.</span><span class="sxs-lookup"><span data-stu-id="f024a-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|  
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="f024a-124">Obtém um ponteiro de interface para um `IReferenceIdentity` cadeia de caracteres formatada de instância gerada especificado.</span><span class="sxs-lookup"><span data-stu-id="f024a-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f024a-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f024a-125">Requirements</span></span>  
 <span data-ttu-id="f024a-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f024a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f024a-127">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="f024a-127">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="f024a-128">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f024a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f024a-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f024a-129">See Also</span></span>  
 [<span data-ttu-id="f024a-130">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="f024a-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
