---
title: '&lt;nameEntry&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1bffb72e7c68d10e2c0edd5ec3cb9bcff10cbc0a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltnameentrygt-element"></a><span data-ttu-id="6efa1-102">&lt;nameEntry&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="6efa1-102">&lt;nameEntry&gt; Element</span></span>
<span data-ttu-id="6efa1-103">Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="6efa1-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="6efa1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6efa1-104">\<configuration></span></span>  
<span data-ttu-id="6efa1-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="6efa1-105">\<mscorlib></span></span>  
<span data-ttu-id="6efa1-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="6efa1-106">\<cryptographySettings></span></span>  
<span data-ttu-id="6efa1-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="6efa1-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="6efa1-108">\<nameEntry ></span><span class="sxs-lookup"><span data-stu-id="6efa1-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6efa1-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6efa1-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6efa1-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6efa1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6efa1-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6efa1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6efa1-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="6efa1-112">Attributes</span></span>  
  
|<span data-ttu-id="6efa1-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="6efa1-113">Attribute</span></span>|<span data-ttu-id="6efa1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6efa1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6efa1-115">**name**</span><span class="sxs-lookup"><span data-stu-id="6efa1-115">**name**</span></span>|<span data-ttu-id="6efa1-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6efa1-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="6efa1-117">Especifica o nome amigável do algoritmo que implementa a classe de criptografia.</span><span class="sxs-lookup"><span data-stu-id="6efa1-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="6efa1-118">**class**</span><span class="sxs-lookup"><span data-stu-id="6efa1-118">**class**</span></span>|<span data-ttu-id="6efa1-119">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6efa1-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="6efa1-120">Especifica o valor para o **nome** atributo o [ \<cryptoClass >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="6efa1-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6efa1-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6efa1-121">Child Elements</span></span>  
 <span data-ttu-id="6efa1-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6efa1-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6efa1-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6efa1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6efa1-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="6efa1-124">Element</span></span>|<span data-ttu-id="6efa1-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="6efa1-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6efa1-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6efa1-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="6efa1-127">Especifica o elemento raiz para a seção de configuração do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6efa1-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6efa1-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="6efa1-128">Remarks</span></span>  
 <span data-ttu-id="6efa1-129">O **nome** atributo pode ser o nome de uma das classes abstratas encontradas no <xref:System.Security.Cryptography> namespace.</span><span class="sxs-lookup"><span data-stu-id="6efa1-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="6efa1-130">Quando você chama o **criar** método em uma classe abstrata de criptografia, o nome de classe abstrata é passado para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> método.</span><span class="sxs-lookup"><span data-stu-id="6efa1-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="6efa1-131">**CreateFromName** retorna uma instância do tipo indicado pelo **classe** atributo.</span><span class="sxs-lookup"><span data-stu-id="6efa1-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="6efa1-132">Se o **nome** atributo é um nome curto, como RSA, você pode usar esse nome ao chamar o **CreateFromName** método.</span><span class="sxs-lookup"><span data-stu-id="6efa1-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6efa1-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6efa1-133">Example</span></span>  
 <span data-ttu-id="6efa1-134">O exemplo a seguir mostra como usar o  **\<nameEntry >** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6efa1-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="6efa1-135">Você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e o uso de <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="6efa1-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6efa1-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6efa1-136">See Also</span></span>  
 [<span data-ttu-id="6efa1-137">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="6efa1-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="6efa1-138">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="6efa1-138">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="6efa1-139">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="6efa1-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="6efa1-140">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="6efa1-140">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
