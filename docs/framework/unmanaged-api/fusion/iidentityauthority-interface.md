---
title: Interface IIdentityAuthority
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab8965ca5d6c9c96cea5f5b351547ce2d4dfacc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546274"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="2e6cd-102">Interface IIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="2e6cd-102">IIdentityAuthority Interface</span></span>
<span data-ttu-id="2e6cd-103">Gerencia chaves de identidade para objetos de código.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-103">Manages identity keys for code objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e6cd-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2e6cd-104">Methods</span></span>  
  
|<span data-ttu-id="2e6cd-105">Método</span><span class="sxs-lookup"><span data-stu-id="2e6cd-105">Method</span></span>|<span data-ttu-id="2e6cd-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e6cd-106">Description</span></span>|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="2e6cd-107">Obtém um valor que indica se os dois especificada [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instâncias são iguais.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="2e6cd-108">Obtém um valor que indica se os dois especificada [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instâncias são iguais.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="2e6cd-109">Obtém um valor que indica se as duas representações de identidade de definição de cadeia de caracteres especificada são iguais.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|  
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="2e6cd-110">Obtém um valor que indica se as duas representações de identidade de referência de cadeia de caracteres especificada são iguais.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|  
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="2e6cd-111">Obtém um ponteiro para um novo `IDefinitionIdentity` instância que representa o objeto de código no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="2e6cd-112">Obtém um ponteiro para um novo `IReferenceIdentity` instância que representa o objeto de código no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="2e6cd-113">Obtém uma versão de cadeia de caracteres formatada especificada `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="2e6cd-114">Preenche o buffer de caractere largo especificado com uma versão de cadeia de caracteres especificada `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="2e6cd-115">Obtém um valor que indica se a especificada `IDefinitionIdentity` e `IReferenceIdentity` instâncias se referem ao mesmo objeto de código.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="2e6cd-116">Obtém um valor que indica se as cadeias de caracteres especificadas se referem ao mesmo objeto de código.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|  
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="2e6cd-117">Obtém um ponteiro para uma chave de cadeia de caracteres criada recentemente especificado `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="2e6cd-118">Obtém um ponteiro para uma chave de cadeia de caracteres criada recentemente especificado `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="2e6cd-119">Obtém um valor de hash especificado `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::HashReference`|<span data-ttu-id="2e6cd-120">Obtém um valor de hash especificado `IreferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-120">Gets a hash value for the specified `IreferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="2e6cd-121">Obtém uma versão de cadeia de caracteres formatada especificada `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="2e6cd-122">Preenche o buffer de caractere largo especificado com uma versão de cadeia de caracteres especificada `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="2e6cd-123">Obtém um ponteiro de interface para um `IDefinitionIdentity` cadeia de caracteres formatada de instância gerada especificado.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|  
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="2e6cd-124">Obtém um ponteiro de interface para um `IReferenceIdentity` cadeia de caracteres formatada de instância gerada especificado.</span><span class="sxs-lookup"><span data-stu-id="2e6cd-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2e6cd-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e6cd-125">Requirements</span></span>  
 <span data-ttu-id="2e6cd-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e6cd-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e6cd-127">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="2e6cd-127">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="2e6cd-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e6cd-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e6cd-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e6cd-129">See also</span></span>
- [<span data-ttu-id="2e6cd-130">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="2e6cd-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
