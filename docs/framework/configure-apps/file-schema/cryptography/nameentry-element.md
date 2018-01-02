---
title: '&lt;nameEntry&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7c9a4b4532d98b7dfc2484dab1bb57e5a26fa392
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnameentrygt-element"></a><span data-ttu-id="70c52-102">&lt;nameEntry&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="70c52-102">&lt;nameEntry&gt; Element</span></span>
<span data-ttu-id="70c52-103">Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="70c52-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="70c52-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="70c52-104">\<configuration></span></span>  
<span data-ttu-id="70c52-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="70c52-105">\<mscorlib></span></span>  
<span data-ttu-id="70c52-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="70c52-106">\<cryptographySettings></span></span>  
<span data-ttu-id="70c52-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="70c52-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="70c52-108">\<nameEntry ></span><span class="sxs-lookup"><span data-stu-id="70c52-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70c52-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70c52-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70c52-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="70c52-110">Attributes and Elements</span></span>  
 <span data-ttu-id="70c52-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="70c52-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70c52-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="70c52-112">Attributes</span></span>  
  
|<span data-ttu-id="70c52-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="70c52-113">Attribute</span></span>|<span data-ttu-id="70c52-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="70c52-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70c52-115">**name**</span><span class="sxs-lookup"><span data-stu-id="70c52-115">**name**</span></span>|<span data-ttu-id="70c52-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="70c52-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="70c52-117">Especifica o nome amigável do algoritmo que implementa a classe de criptografia.</span><span class="sxs-lookup"><span data-stu-id="70c52-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="70c52-118">**class**</span><span class="sxs-lookup"><span data-stu-id="70c52-118">**class**</span></span>|<span data-ttu-id="70c52-119">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="70c52-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="70c52-120">Especifica o valor para o **nome** atributo o [ \<cryptoClass >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="70c52-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70c52-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="70c52-121">Child Elements</span></span>  
 <span data-ttu-id="70c52-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="70c52-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70c52-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="70c52-123">Parent Elements</span></span>  
  
|<span data-ttu-id="70c52-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="70c52-124">Element</span></span>|<span data-ttu-id="70c52-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="70c52-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="70c52-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70c52-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="70c52-127">Especifica o elemento raiz para a seção de configuração do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="70c52-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70c52-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="70c52-128">Remarks</span></span>  
 <span data-ttu-id="70c52-129">O **nome** atributo pode ser o nome de uma das classes abstratas encontradas no <xref:System.Security.Cryptography> namespace.</span><span class="sxs-lookup"><span data-stu-id="70c52-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="70c52-130">Quando você chama o **criar** método em uma classe abstrata de criptografia, o nome de classe abstrata é passado para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> método.</span><span class="sxs-lookup"><span data-stu-id="70c52-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="70c52-131">**CreateFromName** retorna uma instância do tipo indicado pelo **classe** atributo.</span><span class="sxs-lookup"><span data-stu-id="70c52-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="70c52-132">Se o **nome** atributo é um nome curto, como RSA, você pode usar esse nome ao chamar o **CreateFromName** método.</span><span class="sxs-lookup"><span data-stu-id="70c52-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70c52-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70c52-133">Example</span></span>  
 <span data-ttu-id="70c52-134">O exemplo a seguir mostra como usar o  **\<nameEntry >** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="70c52-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="70c52-135">Você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e o uso de <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="70c52-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70c52-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70c52-136">See Also</span></span>  
 [<span data-ttu-id="70c52-137">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="70c52-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="70c52-138">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="70c52-138">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="70c52-139">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="70c52-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="70c52-140">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="70c52-140">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
