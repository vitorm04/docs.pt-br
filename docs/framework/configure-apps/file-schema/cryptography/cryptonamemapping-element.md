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
manager: markl
ms.openlocfilehash: f6811a2dbd8859a8765c5e855e0fe423bd31f287
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359381"
---
# <a name="ltcryptonamemappinggt-element"></a><span data-ttu-id="a4233-102">&lt;cryptoNameMapping&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="a4233-102">&lt;cryptoNameMapping&gt; Element</span></span>
<span data-ttu-id="a4233-103">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="a4233-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="a4233-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a4233-104">\<configuration></span></span>  
<span data-ttu-id="a4233-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="a4233-105">\<mscorlib></span></span>  
<span data-ttu-id="a4233-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="a4233-106">\<cryptographySettings></span></span>  
<span data-ttu-id="a4233-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="a4233-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4233-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4233-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4233-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a4233-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a4233-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a4233-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4233-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="a4233-111">Attributes</span></span>  
 <span data-ttu-id="a4233-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a4233-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a4233-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a4233-113">Child Elements</span></span>  
  
|<span data-ttu-id="a4233-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="a4233-114">Element</span></span>|<span data-ttu-id="a4233-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4233-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="a4233-116">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no elemento  **\<nameEntry>**.</span><span class="sxs-lookup"><span data-stu-id="a4233-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="a4233-117">Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="a4233-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4233-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a4233-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a4233-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="a4233-119">Element</span></span>|<span data-ttu-id="a4233-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4233-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a4233-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a4233-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="a4233-122">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="a4233-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="a4233-123">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="a4233-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="a4233-124">Contém o \<cryptographySettings > elemento.</span><span class="sxs-lookup"><span data-stu-id="a4233-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a4233-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a4233-125">Example</span></span>  
 <span data-ttu-id="a4233-126">O exemplo a seguir mostra como usar o  **\<cryptoNameMapping >** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a4233-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="a4233-127">Você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e o uso de <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="a4233-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a4233-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4233-128">See Also</span></span>  
 [<span data-ttu-id="a4233-129">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="a4233-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="a4233-130">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="a4233-130">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="a4233-131">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="a4233-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="a4233-132">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="a4233-132">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
