---
title: '&lt;cryptoClasses&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e3bc8fbb103d59b825e07cc52b155f1ea8061f31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649369"
---
# <a name="ltcryptoclassesgt-element"></a><span data-ttu-id="f7c4d-102">&lt;cryptoClasses&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="f7c4d-102">&lt;cryptoClasses&gt; Element</span></span>
<span data-ttu-id="f7c4d-103">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no elemento [ \<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="f7c4d-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="f7c4d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f7c4d-104">\<configuration></span></span>  
<span data-ttu-id="f7c4d-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="f7c4d-105">\<mscorlib></span></span>  
<span data-ttu-id="f7c4d-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="f7c4d-106">\<cryptographySettings></span></span>  
<span data-ttu-id="f7c4d-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="f7c4d-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="f7c4d-108">\<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="f7c4d-108">\<cryptoClasses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7c4d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7c4d-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7c4d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f7c4d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f7c4d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f7c4d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7c4d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f7c4d-112">Attributes</span></span>  
 <span data-ttu-id="f7c4d-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f7c4d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f7c4d-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f7c4d-114">Child Elements</span></span>  
  
|<span data-ttu-id="f7c4d-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f7c4d-115">Element</span></span>|<span data-ttu-id="f7c4d-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7c4d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7c4d-117">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="f7c4d-117">\<cryptoClass></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="f7c4d-118">Contém uma classe de criptografia que tem um mapeamento para um nome amigável no elemento **\<nameEntry>**.</span><span class="sxs-lookup"><span data-stu-id="f7c4d-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f7c4d-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f7c4d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f7c4d-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="f7c4d-120">Element</span></span>|<span data-ttu-id="f7c4d-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7c4d-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f7c4d-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7c4d-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="f7c4d-123">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="f7c4d-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="f7c4d-124">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="f7c4d-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="f7c4d-125">Contém o `cryptographySettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="f7c4d-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f7c4d-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7c4d-126">Example</span></span>  
 <span data-ttu-id="f7c4d-127">O exemplo a seguir mostra como usar o  **\<cryptoClass >** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f7c4d-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="f7c4d-128">Em seguida, você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e o uso de <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="f7c4d-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7c4d-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7c4d-129">See also</span></span>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="f7c4d-130">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="f7c4d-130">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f7c4d-131">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="f7c4d-131">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="f7c4d-132">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="f7c4d-132">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="f7c4d-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="f7c4d-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [<span data-ttu-id="f7c4d-134">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="f7c4d-134">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
