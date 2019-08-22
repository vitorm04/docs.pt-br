---
title: Esquema de configurações de criptografia
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: a2aa56f8b2a92f906293adfae9d23ed8959336fb
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664289"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="679f5-102">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="679f5-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="679f5-103">O esquema de configurações de criptografia contém elementos que especificam como mapear nomes de algoritmo amigáveis para classes que implementam algoritmos de criptografia.</span><span class="sxs-lookup"><span data-stu-id="679f5-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="679f5-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="679f5-104">**\<configuration>**</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="679f5-105"> **\<mscorlib>** </span><span class="sxs-lookup"><span data-stu-id="679f5-105">**\<mscorlib>**</span></span>](mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="679f5-106"> **\<cryptographySettings>** </span><span class="sxs-lookup"><span data-stu-id="679f5-106">**\<cryptographySettings>**</span></span>](cryptographysettings-element.md)  
  
 [<span data-ttu-id="679f5-107"> **\<cryptoNameMapping>** </span><span class="sxs-lookup"><span data-stu-id="679f5-107">**\<cryptoNameMapping>**</span></span>](cryptonamemapping-element.md)  
  
 [<span data-ttu-id="679f5-108"> **\<cryptoClasses>** </span><span class="sxs-lookup"><span data-stu-id="679f5-108">**\<cryptoClasses>**</span></span>](cryptoclasses-element.md)  
  
 [<span data-ttu-id="679f5-109"> **\<cryptoClass>** </span><span class="sxs-lookup"><span data-stu-id="679f5-109">**\<cryptoClass>**</span></span>](cryptoclass-element.md)  
  
 [<span data-ttu-id="679f5-110"> **\<nameEntry>** </span><span class="sxs-lookup"><span data-stu-id="679f5-110">**\<nameEntry>**</span></span>](nameentry-element.md)  
  
 [<span data-ttu-id="679f5-111"> **\<oidMap>** </span><span class="sxs-lookup"><span data-stu-id="679f5-111">**\<oidMap>**</span></span>](oidmap-element.md)  
  
 [<span data-ttu-id="679f5-112"> **\<oidEntry>** </span><span class="sxs-lookup"><span data-stu-id="679f5-112">**\<oidEntry>**</span></span>](oidentry-element.md)  
  
|<span data-ttu-id="679f5-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="679f5-113">Element</span></span>|<span data-ttu-id="679f5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="679f5-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="679f5-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="679f5-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="679f5-116">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no elemento  **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="679f5-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="679f5-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="679f5-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="679f5-118">Contém uma classe de criptografia que tem um mapeamento para um nome amigável no elemento **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="679f5-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="679f5-119"> **\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="679f5-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="679f5-120">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="679f5-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="679f5-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="679f5-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="679f5-122">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="679f5-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="679f5-123">Elemento **\<mscorlib>** para configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="679f5-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="679f5-124">Contém o elemento **\<cryptographySettings>** .</span><span class="sxs-lookup"><span data-stu-id="679f5-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="679f5-125"> **\<nameEntry>** </span><span class="sxs-lookup"><span data-stu-id="679f5-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="679f5-126">Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="679f5-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="679f5-127"> **\<oidEntry>** </span><span class="sxs-lookup"><span data-stu-id="679f5-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="679f5-128">Mapeia um OID (identificador de objeto) do ASN.1 para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="679f5-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="679f5-129"> **\<oidMap>** </span><span class="sxs-lookup"><span data-stu-id="679f5-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="679f5-130">Contém mapeamentos de OID do ASN.1 para classes.</span><span class="sxs-lookup"><span data-stu-id="679f5-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="679f5-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="679f5-131">See also</span></span>

- [<span data-ttu-id="679f5-132">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="679f5-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="679f5-133">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="679f5-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
