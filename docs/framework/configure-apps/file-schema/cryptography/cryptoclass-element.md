---
title: '&lt;cryptoClass&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 448e2c83f6897fd876bb79dfb781bcf4ddd2252b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcryptoclassgt-element"></a><span data-ttu-id="906a2-102">&lt;cryptoClass&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="906a2-102">&lt;cryptoClass&gt; Element</span></span>
<span data-ttu-id="906a2-103">Contém uma classe de criptografia que tem um mapeamento para um nome amigável no elemento [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="906a2-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="906a2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="906a2-104">\<configuration></span></span>  
<span data-ttu-id="906a2-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="906a2-105">\<mscorlib></span></span>  
<span data-ttu-id="906a2-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="906a2-106">\<cryptographySettings></span></span>  
<span data-ttu-id="906a2-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="906a2-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="906a2-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="906a2-108">\<cryptoClasses></span></span>  
<span data-ttu-id="906a2-109">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="906a2-109">\<cryptoClass></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="906a2-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="906a2-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="906a2-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="906a2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="906a2-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="906a2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="906a2-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="906a2-113">Attributes</span></span>  
  
|<span data-ttu-id="906a2-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="906a2-114">Attribute</span></span>|<span data-ttu-id="906a2-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="906a2-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="906a2-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="906a2-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="906a2-117">Contém as informações para a classe de criptografia.</span><span class="sxs-lookup"><span data-stu-id="906a2-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="906a2-118">Use esse atributo para fornecer um nome curto para a sua classe.</span><span class="sxs-lookup"><span data-stu-id="906a2-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="906a2-119">Você deve especificar uma cadeia de caracteres que atenda aos requisitos especificados em [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="906a2-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="906a2-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="906a2-120">Child Elements</span></span>  
 <span data-ttu-id="906a2-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="906a2-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="906a2-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="906a2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="906a2-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="906a2-123">Element</span></span>|<span data-ttu-id="906a2-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="906a2-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="906a2-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="906a2-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="906a2-126">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no elemento [ \<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="906a2-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="906a2-127">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="906a2-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="906a2-128">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="906a2-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="906a2-129">Contém o elemento [\<cryptographySettings>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="906a2-129">Contains the [\<cryptographySettings>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="906a2-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="906a2-130">Example</span></span>  
 <span data-ttu-id="906a2-131">O exemplo a seguir mostra como usar o  **\<cryptoClass >** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="906a2-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="906a2-132">Você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e o uso de <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="906a2-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="906a2-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="906a2-133">See Also</span></span>  
 [<span data-ttu-id="906a2-134">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="906a2-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="906a2-135">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="906a2-135">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="906a2-136">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="906a2-136">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="906a2-137">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="906a2-137">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
