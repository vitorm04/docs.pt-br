---
title: "Esquema de configurações de criptografia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6b6d9eeacb38531ced5768f29bf26de3c9294b71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="f8220-102">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="f8220-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="f8220-103">O esquema de configurações de criptografia contém elementos que especificam como mapear nomes de algoritmo amigáveis para classes que implementam algoritmos de criptografia.</span><span class="sxs-lookup"><span data-stu-id="f8220-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="f8220-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="f8220-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="f8220-105">**\<mscorlib>**</span><span class="sxs-lookup"><span data-stu-id="f8220-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="f8220-106">**\<cryptographySettings>**</span><span class="sxs-lookup"><span data-stu-id="f8220-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="f8220-107">**\<cryptoNameMapping>**</span><span class="sxs-lookup"><span data-stu-id="f8220-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="f8220-108">**\<cryptoClasses>**</span><span class="sxs-lookup"><span data-stu-id="f8220-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="f8220-109">**\<cryptoClass>**</span><span class="sxs-lookup"><span data-stu-id="f8220-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="f8220-110">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="f8220-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="f8220-111">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="f8220-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="f8220-112">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="f8220-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="f8220-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f8220-113">Element</span></span>|<span data-ttu-id="f8220-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8220-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8220-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="f8220-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="f8220-116">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no elemento  **\<nameEntry>**.</span><span class="sxs-lookup"><span data-stu-id="f8220-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="f8220-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="f8220-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="f8220-118">Contém uma classe de criptografia que tem um mapeamento para um nome amigável no elemento **\<nameEntry>**.</span><span class="sxs-lookup"><span data-stu-id="f8220-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="f8220-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="f8220-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="f8220-120">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="f8220-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="f8220-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="f8220-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="f8220-122">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="f8220-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="f8220-123">Elemento **\<mscorlib>** para configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="f8220-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="f8220-124">Contém o elemento **\<cryptographySettings>**.</span><span class="sxs-lookup"><span data-stu-id="f8220-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="f8220-125">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="f8220-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="f8220-126">Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="f8220-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="f8220-127">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="f8220-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="f8220-128">Mapeia um OID (identificador de objeto) do ASN.1 para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="f8220-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="f8220-129">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="f8220-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="f8220-130">Contém mapeamentos de OID do ASN.1 para classes.</span><span class="sxs-lookup"><span data-stu-id="f8220-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8220-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8220-131">See Also</span></span>  
 [<span data-ttu-id="f8220-132">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="f8220-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="f8220-133">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="f8220-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
