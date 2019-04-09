---
title: <cryptoNameMapping> Elemento
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: bcf7894dba66736fcc1a30af9b5557549ef25e7d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092455"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="95eb8-102">\<cryptoNameMapping > elemento</span><span class="sxs-lookup"><span data-stu-id="95eb8-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="95eb8-103">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="95eb8-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="95eb8-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="95eb8-104">\<configuration></span></span>  
<span data-ttu-id="95eb8-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="95eb8-105">\<mscorlib></span></span>  
<span data-ttu-id="95eb8-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="95eb8-106">\<cryptographySettings></span></span>  
<span data-ttu-id="95eb8-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="95eb8-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95eb8-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95eb8-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95eb8-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="95eb8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="95eb8-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="95eb8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95eb8-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="95eb8-111">Attributes</span></span>  
 <span data-ttu-id="95eb8-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="95eb8-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="95eb8-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="95eb8-113">Child Elements</span></span>  
  
|<span data-ttu-id="95eb8-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="95eb8-114">Element</span></span>|<span data-ttu-id="95eb8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="95eb8-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="95eb8-116">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no elemento  **\<nameEntry>**.</span><span class="sxs-lookup"><span data-stu-id="95eb8-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="95eb8-117">Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="95eb8-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95eb8-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="95eb8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="95eb8-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="95eb8-119">Element</span></span>|<span data-ttu-id="95eb8-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="95eb8-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="95eb8-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95eb8-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="95eb8-122">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="95eb8-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="95eb8-123">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="95eb8-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="95eb8-124">Contém o \<cryptographySettings > elemento.</span><span class="sxs-lookup"><span data-stu-id="95eb8-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="95eb8-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95eb8-125">Example</span></span>  
 <span data-ttu-id="95eb8-126">O exemplo a seguir mostra como usar o  **\<cryptoNameMapping >** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="95eb8-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="95eb8-127">Em seguida, você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e o uso de <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="95eb8-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95eb8-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95eb8-128">See also</span></span>

- [<span data-ttu-id="95eb8-129">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="95eb8-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="95eb8-130">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="95eb8-130">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="95eb8-131">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="95eb8-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="95eb8-132">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="95eb8-132">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
