---
title: '&lt;cryptoNameMapping&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ad1611701dca48244f3b2a93ecc3ea86363081ed
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47230788"
---
# <a name="ltcryptonamemappinggt-element"></a><span data-ttu-id="65bcf-102">&lt;cryptoNameMapping&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="65bcf-102">&lt;cryptoNameMapping&gt; Element</span></span>
<span data-ttu-id="65bcf-103">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="65bcf-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="65bcf-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="65bcf-104">\<configuration></span></span>  
<span data-ttu-id="65bcf-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="65bcf-105">\<mscorlib></span></span>  
<span data-ttu-id="65bcf-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="65bcf-106">\<cryptographySettings></span></span>  
<span data-ttu-id="65bcf-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="65bcf-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65bcf-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65bcf-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65bcf-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="65bcf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="65bcf-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="65bcf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65bcf-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="65bcf-111">Attributes</span></span>  
 <span data-ttu-id="65bcf-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="65bcf-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="65bcf-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="65bcf-113">Child Elements</span></span>  
  
|<span data-ttu-id="65bcf-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="65bcf-114">Element</span></span>|<span data-ttu-id="65bcf-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="65bcf-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="65bcf-116">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no elemento  **\<nameEntry>**.</span><span class="sxs-lookup"><span data-stu-id="65bcf-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="65bcf-117">Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="65bcf-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65bcf-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="65bcf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="65bcf-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="65bcf-119">Element</span></span>|<span data-ttu-id="65bcf-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="65bcf-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="65bcf-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65bcf-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="65bcf-122">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="65bcf-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="65bcf-123">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="65bcf-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="65bcf-124">Contém o \<cryptographySettings > elemento.</span><span class="sxs-lookup"><span data-stu-id="65bcf-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="65bcf-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65bcf-125">Example</span></span>  
 <span data-ttu-id="65bcf-126">O exemplo a seguir mostra como usar o  **\<cryptoNameMapping >** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="65bcf-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="65bcf-127">Em seguida, você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e o uso de <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="65bcf-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="65bcf-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65bcf-128">See Also</span></span>  
 [<span data-ttu-id="65bcf-129">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="65bcf-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="65bcf-130">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="65bcf-130">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="65bcf-131">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="65bcf-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="65bcf-132">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="65bcf-132">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
