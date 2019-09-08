---
title: Interfaces de fusão
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1605605f8510f7ccf5f0bbf2f3f6b09050a16025
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795306"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="7a9f1-102">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="7a9f1-102">Fusion Interfaces</span></span>
<span data-ttu-id="7a9f1-103">Esta seção descreve as interfaces não gerenciadas que a API do Fusion usa para acessar as propriedades dos recursos de um aplicativo e localizar as versões corretas desses recursos para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7a9f1-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="7a9f1-104">In This Section</span></span>  
 [<span data-ttu-id="7a9f1-105">Interface IAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="7a9f1-105">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)  
 <span data-ttu-id="7a9f1-106">Fornece métodos que geram e comparam chaves para identidades e referências de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="7a9f1-107">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="7a9f1-107">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)  
 <span data-ttu-id="7a9f1-108">Fornece uma representação do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="7a9f1-109">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="7a9f1-109">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)  
 <span data-ttu-id="7a9f1-110">Representa um único assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="7a9f1-111">Interface IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="7a9f1-111">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)  
 <span data-ttu-id="7a9f1-112">Representa um enumerador para uma matriz `IAssemblyName` de objetos.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="7a9f1-113">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="7a9f1-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)  
 <span data-ttu-id="7a9f1-114">Fornece métodos para descrever e trabalhar com a identidade exclusiva de um assembly.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="7a9f1-115">Interface IDefinitionAppId</span><span class="sxs-lookup"><span data-stu-id="7a9f1-115">IDefinitionAppId Interface</span></span>](idefinitionappid-interface.md)  
 <span data-ttu-id="7a9f1-116">Representa um identificador exclusivo para o código que define o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="7a9f1-117">Interface IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="7a9f1-117">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)  
 <span data-ttu-id="7a9f1-118">Representa a assinatura exclusiva do código que define o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="7a9f1-119">Interface IEnumDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="7a9f1-119">IEnumDefinitionIdentity Interface</span></span>](ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="7a9f1-120">Serve como o enumerador para uma coleção `IDefinitionIdentity` de objetos.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="7a9f1-121">Interface IEnumIDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="7a9f1-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)  
 <span data-ttu-id="7a9f1-122">Serve como um enumerador para os atributos do objeto de código no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="7a9f1-123">Interface IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="7a9f1-123">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)  
 <span data-ttu-id="7a9f1-124">Serve como um enumerador para uma coleção `IReferenceIdentity` de objetos.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="7a9f1-125">Interface IIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="7a9f1-125">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)  
 <span data-ttu-id="7a9f1-126">Gerencia chaves de identidade para objetos de código.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="7a9f1-127">Interface IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="7a9f1-127">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)  
 <span data-ttu-id="7a9f1-128">Representa um enumerador para os assemblies referenciados instalados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="7a9f1-129">Interface IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="7a9f1-129">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)  
 <span data-ttu-id="7a9f1-130">Representa um item instalado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="7a9f1-131">Interface IReferenceAppId</span><span class="sxs-lookup"><span data-stu-id="7a9f1-131">IReferenceAppId Interface</span></span>](ireferenceappid-interface.md)  
 <span data-ttu-id="7a9f1-132">Representa uma referência ao identificador exclusivo para o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="7a9f1-133">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="7a9f1-133">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)  
 <span data-ttu-id="7a9f1-134">Representa uma referência à assinatura exclusiva de um objeto de código.</span><span class="sxs-lookup"><span data-stu-id="7a9f1-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7a9f1-135">Referência</span><span class="sxs-lookup"><span data-stu-id="7a9f1-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="7a9f1-136">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="7a9f1-136">Related Sections</span></span>  
 [<span data-ttu-id="7a9f1-137">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="7a9f1-137">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)  
  
 [<span data-ttu-id="7a9f1-138">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="7a9f1-138">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="7a9f1-139">Estruturas de fusão</span><span class="sxs-lookup"><span data-stu-id="7a9f1-139">Fusion Structures</span></span>](fusion-structures.md)
