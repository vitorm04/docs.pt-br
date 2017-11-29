---
title: Interface IAppIdAuthority
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppIdAuthority
api_location: fusion.dll
api_type: COM
f1_keywords: IAppIdAuthority
helpviewer_keywords: IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07bfd26a43d264babc9854b0fd0da909dd329405
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="2aecd-102">Interface IAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="2aecd-102">IAppIdAuthority Interface</span></span>
<span data-ttu-id="2aecd-103">Fornece métodos que geram e comparam as chaves de identidades de aplicativo e referências.</span><span class="sxs-lookup"><span data-stu-id="2aecd-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2aecd-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2aecd-104">Methods</span></span>  
  
|<span data-ttu-id="2aecd-105">Método</span><span class="sxs-lookup"><span data-stu-id="2aecd-105">Method</span></span>|<span data-ttu-id="2aecd-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2aecd-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="2aecd-107">Obtém um valor que indica se os dois especificada [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instâncias são iguais.</span><span class="sxs-lookup"><span data-stu-id="2aecd-107">Gets a value that indicates whether the two specified [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="2aecd-108">Você pode passar o valor de sinalizador IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION para ignorar as informações de versão do respectivos.</span><span class="sxs-lookup"><span data-stu-id="2aecd-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="2aecd-109">Obtém um valor que indica se os dois especificada [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instâncias são iguais.</span><span class="sxs-lookup"><span data-stu-id="2aecd-109">Gets a value that indicates whether the two specified [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="2aecd-110">Você pode passar o valor de sinalizador IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION para ignorar as informações de versão do respectivos.</span><span class="sxs-lookup"><span data-stu-id="2aecd-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="2aecd-111">Obtém um valor que indica se as duas definições de cadeia de caracteres especificada são iguais.</span><span class="sxs-lookup"><span data-stu-id="2aecd-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="2aecd-112">Você pode passar o valor de sinalizador IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION para ignorar as informações de versão do respectivos.</span><span class="sxs-lookup"><span data-stu-id="2aecd-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="2aecd-113">Obtém um valor que indica se as duas referências de cadeia de caracteres especificada são iguais.</span><span class="sxs-lookup"><span data-stu-id="2aecd-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="2aecd-114">Você pode passar o valor de sinalizador IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION para ignorar as informações de versão do respectivos.</span><span class="sxs-lookup"><span data-stu-id="2aecd-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="2aecd-115">Obtém um ponteiro de interface para um recém-gerado `IDefinitionAppId` instância que representa o assembly no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="2aecd-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="2aecd-116">Obtém um ponteiro de interface recém-criado para um `IReferenceAppId` que representa o assembly no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="2aecd-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="2aecd-117">Obtém uma versão de cadeia de caracteres especificada `IDefinitionAppId`, usando os valores de sinalizador especificado.</span><span class="sxs-lookup"><span data-stu-id="2aecd-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="2aecd-118">Obtém um valor que indica se o especificado `IDefinitionAppId` e `IReferenceAppId` representar o mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="2aecd-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="2aecd-119">Obtém um valor que indica se a cadeia de caracteres de definição especificado e a cadeia de caracteres de referência representam o mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="2aecd-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="2aecd-120">Obtém uma chave de cadeia de caracteres que representa a `IDefinitionAppId` instância.</span><span class="sxs-lookup"><span data-stu-id="2aecd-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="2aecd-121">Obtém uma chave de cadeia de caracteres que representa a `IReferenceAppId` instância.</span><span class="sxs-lookup"><span data-stu-id="2aecd-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="2aecd-122">Obtém uma chave de hash especificado `IDefinitionAppId` instância.</span><span class="sxs-lookup"><span data-stu-id="2aecd-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="2aecd-123">Obtém uma chave de hash especificado `IReferenceAppId` instância.</span><span class="sxs-lookup"><span data-stu-id="2aecd-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="2aecd-124">Obtém uma versão de cadeia de caracteres especificada `IReferenceAppId`, usando os valores de sinalizador especificado.</span><span class="sxs-lookup"><span data-stu-id="2aecd-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="2aecd-125">Obtém um ponteiro de interface para um `IDefinitionAppId` instância que representa o assembly referenciado pela chave de cadeia de caracteres especificada.</span><span class="sxs-lookup"><span data-stu-id="2aecd-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="2aecd-126">Obtém um ponteiro de interface para um `IReferenceAppId` instância que representa o assembly referenciado pela chave de cadeia de caracteres especificada.</span><span class="sxs-lookup"><span data-stu-id="2aecd-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2aecd-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2aecd-127">Requirements</span></span>  
 <span data-ttu-id="2aecd-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2aecd-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2aecd-129">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="2aecd-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="2aecd-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2aecd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aecd-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2aecd-131">See Also</span></span>  
 [<span data-ttu-id="2aecd-132">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="2aecd-132">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
