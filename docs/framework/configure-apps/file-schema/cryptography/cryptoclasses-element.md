---
title: Elemento <cryptoClasses>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: c93fadf51297d59ab499e25de283700364903049
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155240"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="382b0-102">\<criptoClasses> Element</span><span class="sxs-lookup"><span data-stu-id="382b0-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="382b0-103">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no [ \<nomeEntry>](nameentry-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="382b0-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="382b0-104">**\<>de configuração**</span><span class="sxs-lookup"><span data-stu-id="382b0-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="382b0-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="382b0-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="382b0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<criptografiaConfigurações>**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="382b0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="382b0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de mapeamento de nomes de cripto**](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="382b0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="382b0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<criptoClasses>**</span><span class="sxs-lookup"><span data-stu-id="382b0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="382b0-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="382b0-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="382b0-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="382b0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="382b0-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="382b0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="382b0-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="382b0-112">Attributes</span></span>  
 <span data-ttu-id="382b0-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="382b0-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="382b0-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="382b0-114">Child Elements</span></span>  
  
|<span data-ttu-id="382b0-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="382b0-115">Element</span></span>|<span data-ttu-id="382b0-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="382b0-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="382b0-117">\<>de criptoclasse</span><span class="sxs-lookup"><span data-stu-id="382b0-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="382b0-118">Contém uma classe de criptografia que tem um mapeamento para um nome amigável no \*\* \<nomeEntry>\*\* elemento.</span><span class="sxs-lookup"><span data-stu-id="382b0-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="382b0-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="382b0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="382b0-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="382b0-120">Element</span></span>|<span data-ttu-id="382b0-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="382b0-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="382b0-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="382b0-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="382b0-123">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="382b0-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="382b0-124">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="382b0-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="382b0-125">Contém `cryptographySettings` o elemento.</span><span class="sxs-lookup"><span data-stu-id="382b0-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="382b0-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="382b0-126">Example</span></span>  
 <span data-ttu-id="382b0-127">O exemplo a seguir \*\* \<\*\* mostra como usar o elemento cryptoClass>para referenciar uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="382b0-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="382b0-128">Em seguida, você pode passar a <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> string "RSA" para o método e usar o <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="382b0-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="382b0-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="382b0-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="382b0-130">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="382b0-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="382b0-131">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="382b0-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="382b0-132">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="382b0-132">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="382b0-133">System.Security.Cryptoography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="382b0-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="382b0-134">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="382b0-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
