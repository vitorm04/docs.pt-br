---
title: "Interfaces de fusão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1742025bed977dfd377a78db42df42c1bc43966
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="fusion-interfaces"></a><span data-ttu-id="f3ac2-102">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="f3ac2-102">Fusion Interfaces</span></span>
<span data-ttu-id="f3ac2-103">Esta seção descreve as interfaces não gerenciadas que a fusão API usa para acessar as propriedades de recursos do aplicativo e para localizar as versões corretas desses recursos para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f3ac2-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f3ac2-104">In This Section</span></span>  
 [<span data-ttu-id="f3ac2-105">Interface IAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="f3ac2-105">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 <span data-ttu-id="f3ac2-106">Fornece métodos que geram e comparam as chaves de identidades de aplicativo e referências.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="f3ac2-107">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="f3ac2-107">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 <span data-ttu-id="f3ac2-108">Fornece uma representação de cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="f3ac2-109">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="f3ac2-109">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 <span data-ttu-id="f3ac2-110">Representa um único assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="f3ac2-111">Interface IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="f3ac2-111">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 <span data-ttu-id="f3ac2-112">Representa um enumerador para uma matriz de `IAssemblyName` objetos.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="f3ac2-113">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="f3ac2-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 <span data-ttu-id="f3ac2-114">Fornece métodos para descrever e trabalhar com uma identidade exclusiva de assembly.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="f3ac2-115">Interface IDefinitionAppId</span><span class="sxs-lookup"><span data-stu-id="f3ac2-115">IDefinitionAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)  
 <span data-ttu-id="f3ac2-116">Representa um identificador exclusivo para o código que define o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="f3ac2-117">Interface IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="f3ac2-117">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 <span data-ttu-id="f3ac2-118">Representa a assinatura exclusiva do código que define o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="f3ac2-119">Interface IEnumDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="f3ac2-119">IEnumDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="f3ac2-120">Serve como o enumerador para uma coleção de `IDefinitionIdentity` objetos.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="f3ac2-121">Interface IEnumIDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="f3ac2-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)  
 <span data-ttu-id="f3ac2-122">Serve como um enumerador para os atributos do objeto de código no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="f3ac2-123">Interface IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="f3ac2-123">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 <span data-ttu-id="f3ac2-124">Serve como um enumerador para uma coleção de `IReferenceIdentity` objetos.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="f3ac2-125">Interface IIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="f3ac2-125">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 <span data-ttu-id="f3ac2-126">Gerencia chaves de identidade para objetos de código.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="f3ac2-127">Interface IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="f3ac2-127">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 <span data-ttu-id="f3ac2-128">Representa um enumerador para os assemblies referenciados instalados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="f3ac2-129">Interface IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="f3ac2-129">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 <span data-ttu-id="f3ac2-130">Representa um item instalado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="f3ac2-131">Interface IReferenceAppId</span><span class="sxs-lookup"><span data-stu-id="f3ac2-131">IReferenceAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)  
 <span data-ttu-id="f3ac2-132">Representa uma referência para o identificador exclusivo para o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="f3ac2-133">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="f3ac2-133">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)  
 <span data-ttu-id="f3ac2-134">Representa uma referência para a assinatura exclusiva de um objeto de código.</span><span class="sxs-lookup"><span data-stu-id="f3ac2-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f3ac2-135">Referência</span><span class="sxs-lookup"><span data-stu-id="f3ac2-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="f3ac2-136">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="f3ac2-136">Related Sections</span></span>  
 [<span data-ttu-id="f3ac2-137">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="f3ac2-137">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [<span data-ttu-id="f3ac2-138">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="f3ac2-138">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="f3ac2-139">Estruturas de fusão</span><span class="sxs-lookup"><span data-stu-id="f3ac2-139">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
