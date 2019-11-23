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
ms.openlocfilehash: 89f1d89ea397794e366b53205ac23b94d7892869
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699751"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="c4871-102">\<elemento de > cryptoClasses</span><span class="sxs-lookup"><span data-stu-id="c4871-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="c4871-103">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no elemento [ \<nameEntry>](nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="c4871-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="c4871-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="c4871-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="c4871-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c4871-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="c4871-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="c4871-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="c4871-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="c4871-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="c4871-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptoClasses >**</span><span class="sxs-lookup"><span data-stu-id="c4871-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4871-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4871-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4871-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c4871-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c4871-111">As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.</span><span class="sxs-lookup"><span data-stu-id="c4871-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4871-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="c4871-112">Attributes</span></span>  
 <span data-ttu-id="c4871-113">None.</span><span class="sxs-lookup"><span data-stu-id="c4871-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c4871-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c4871-114">Child Elements</span></span>  
  
|<span data-ttu-id="c4871-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="c4871-115">Element</span></span>|<span data-ttu-id="c4871-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4871-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4871-117">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="c4871-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="c4871-118">Contém uma classe de criptografia que tem um mapeamento para um nome amigável no elemento **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="c4871-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4871-119">Elementos Pai</span><span class="sxs-lookup"><span data-stu-id="c4871-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c4871-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="c4871-120">Element</span></span>|<span data-ttu-id="c4871-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4871-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c4871-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4871-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="c4871-123">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="c4871-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="c4871-124">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="c4871-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="c4871-125">Contém o elemento `cryptographySettings`.</span><span class="sxs-lookup"><span data-stu-id="c4871-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c4871-126">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c4871-126">Example</span></span>  
 <span data-ttu-id="c4871-127">O exemplo a seguir mostra como usar o elemento **\<cryptoClass >** para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c4871-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="c4871-128">Em seguida, você pode passar a cadeia de caracteres "RSA" para o método <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> e usar o método <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> para retornar um objeto `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="c4871-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c4871-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4871-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="c4871-130">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="c4871-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c4871-131">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="c4871-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c4871-132">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="c4871-132">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="c4871-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="c4871-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [<span data-ttu-id="c4871-134">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="c4871-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
