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
ms.openlocfilehash: 3e2d2335e37ced9139ea44092f10b19566894681
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127091"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="f7916-102">Interface IIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="f7916-102">IIdentityAuthority Interface</span></span>

<span data-ttu-id="f7916-103">Gerencia chaves de identidade para objetos de código.</span><span class="sxs-lookup"><span data-stu-id="f7916-103">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="f7916-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f7916-104">Methods</span></span>

|<span data-ttu-id="f7916-105">Método</span><span class="sxs-lookup"><span data-stu-id="f7916-105">Method</span></span>|<span data-ttu-id="f7916-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7916-106">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="f7916-107">Obtém um valor que indica se as duas instâncias de [IDefinitionIdentity](idefinitionidentity-interface.md) especificadas são iguais.</span><span class="sxs-lookup"><span data-stu-id="f7916-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="f7916-108">Obtém um valor que indica se as duas instâncias de [IReferenceIdentity](ireferenceidentity-interface.md) especificadas são iguais.</span><span class="sxs-lookup"><span data-stu-id="f7916-108">Gets a value that indicates whether the two specified [IReferenceIdentity](ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="f7916-109">Obtém um valor que indica se as duas representações de identidade de definição de cadeia de caracteres especificadas são iguais.</span><span class="sxs-lookup"><span data-stu-id="f7916-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="f7916-110">Obtém um valor que indica se as duas representações de identidade de referência de cadeia de caracteres especificadas são iguais.</span><span class="sxs-lookup"><span data-stu-id="f7916-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="f7916-111">Obtém um ponteiro para uma nova instância de `IDefinitionIdentity` que representa o objeto de código no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="f7916-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="f7916-112">Obtém um ponteiro para uma nova instância de `IReferenceIdentity` que representa o objeto de código no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="f7916-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="f7916-113">Obtém uma versão de cadeia de caracteres formatada do `IDefinitionIdentity`especificado.</span><span class="sxs-lookup"><span data-stu-id="f7916-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="f7916-114">Preenche o buffer de caracteres largos especificado com uma versão de cadeia de caracteres do `IDefinitionIdentity`especificado.</span><span class="sxs-lookup"><span data-stu-id="f7916-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="f7916-115">Obtém um valor que indica se as instâncias especificadas `IDefinitionIdentity` e `IReferenceIdentity` se referem ao mesmo objeto de código.</span><span class="sxs-lookup"><span data-stu-id="f7916-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="f7916-116">Obtém um valor que indica se as cadeias de caracteres especificadas se referem ao mesmo objeto de código.</span><span class="sxs-lookup"><span data-stu-id="f7916-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="f7916-117">Obtém um ponteiro para uma chave de cadeia de caracteres recém-criada para o `IDefinitionIdentity`especificado.</span><span class="sxs-lookup"><span data-stu-id="f7916-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="f7916-118">Obtém um ponteiro para uma chave de cadeia de caracteres recém-criada para o `IReferenceIdentity`especificado.</span><span class="sxs-lookup"><span data-stu-id="f7916-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="f7916-119">Obtém um valor de hash para o `IDefinitionIdentity`especificado.</span><span class="sxs-lookup"><span data-stu-id="f7916-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="f7916-120">Obtém um valor de hash para o `IReferenceIdentity`especificado.</span><span class="sxs-lookup"><span data-stu-id="f7916-120">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="f7916-121">Obtém uma versão de cadeia de caracteres formatada do `IReferenceIdentity`especificado.</span><span class="sxs-lookup"><span data-stu-id="f7916-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="f7916-122">Preenche o buffer de caracteres largos especificado com uma versão de cadeia de caracteres do `IReferenceIdentity`especificado.</span><span class="sxs-lookup"><span data-stu-id="f7916-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="f7916-123">Obtém um ponteiro de interface para uma instância de `IDefinitionIdentity` gerada a partir da cadeia de caracteres formatada especificada.</span><span class="sxs-lookup"><span data-stu-id="f7916-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="f7916-124">Obtém um ponteiro de interface para uma instância de `IReferenceIdentity` gerada a partir da cadeia de caracteres formatada especificada.</span><span class="sxs-lookup"><span data-stu-id="f7916-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="f7916-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7916-125">Requirements</span></span>

<span data-ttu-id="f7916-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7916-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f7916-127">**Cabeçalho:** Isolamento. h</span><span class="sxs-lookup"><span data-stu-id="f7916-127">**Header:** Isolation.h</span></span>

<span data-ttu-id="f7916-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7916-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f7916-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7916-129">See also</span></span>

- [<span data-ttu-id="f7916-130">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="f7916-130">Fusion Interfaces</span></span>](fusion-interfaces.md)
