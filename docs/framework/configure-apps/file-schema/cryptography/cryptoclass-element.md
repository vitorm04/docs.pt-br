---
title: Elemento <cryptoClass>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: 4872fbd6fa043902e8c69f158bee5d0c915ec83a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088657"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="ed6b8-102">\<elemento de > cryptoClass</span><span class="sxs-lookup"><span data-stu-id="ed6b8-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="ed6b8-103">Contém uma classe de criptografia que tem um mapeamento para um nome amigável no elemento [\<nameEntry>](nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="ed6b8-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  

<span data-ttu-id="ed6b8-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed6b8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ed6b8-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ed6b8-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="ed6b8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed6b8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="ed6b8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="ed6b8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>\
<span data-ttu-id="ed6b8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClasses**](cryptoclasses-element.md) ></span><span class="sxs-lookup"><span data-stu-id="ed6b8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>\
<span data-ttu-id="ed6b8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptoClass >**</span><span class="sxs-lookup"><span data-stu-id="ed6b8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ed6b8-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed6b8-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed6b8-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ed6b8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ed6b8-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ed6b8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed6b8-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="ed6b8-113">Attributes</span></span>  
  
|<span data-ttu-id="ed6b8-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="ed6b8-114">Attribute</span></span>|<span data-ttu-id="ed6b8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed6b8-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="ed6b8-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ed6b8-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="ed6b8-117">Contém as informações para a classe de criptografia.</span><span class="sxs-lookup"><span data-stu-id="ed6b8-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="ed6b8-118">Use esse atributo para fornecer um nome curto para sua classe.</span><span class="sxs-lookup"><span data-stu-id="ed6b8-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="ed6b8-119">Você deve especificar uma cadeia de caracteres que atenda aos requisitos especificados na [especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="ed6b8-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed6b8-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ed6b8-120">Child Elements</span></span>  
 <span data-ttu-id="ed6b8-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ed6b8-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed6b8-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ed6b8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ed6b8-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="ed6b8-123">Element</span></span>|<span data-ttu-id="ed6b8-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed6b8-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ed6b8-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ed6b8-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="ed6b8-126">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no elemento [ \<nameEntry>](nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="ed6b8-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ed6b8-127">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="ed6b8-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="ed6b8-128">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="ed6b8-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="ed6b8-129">Contém o elemento [\<cryptographySettings>](cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="ed6b8-129">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ed6b8-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ed6b8-130">Example</span></span>  
 <span data-ttu-id="ed6b8-131">O exemplo a seguir mostra como usar o elemento **\<cryptoClass >** para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ed6b8-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ed6b8-132">Em seguida, você pode passar a cadeia de caracteres "RSA" para o método <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> e usar o método <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> para retornar um objeto `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="ed6b8-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed6b8-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed6b8-133">See also</span></span>

- [<span data-ttu-id="ed6b8-134">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="ed6b8-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ed6b8-135">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="ed6b8-135">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ed6b8-136">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="ed6b8-136">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ed6b8-137">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="ed6b8-137">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
