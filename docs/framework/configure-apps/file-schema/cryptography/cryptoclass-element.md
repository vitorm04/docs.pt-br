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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088657"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="43b18-102">Elemento \<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="43b18-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="43b18-103">Contém uma classe de criptografia que tem um mapeamento para um nome amigável no [\<nameEntry>](nameentry-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="43b18-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**

## <a name="syntax"></a><span data-ttu-id="43b18-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43b18-104">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43b18-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="43b18-105">Attributes and Elements</span></span>  
 <span data-ttu-id="43b18-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="43b18-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43b18-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="43b18-107">Attributes</span></span>  
  
|<span data-ttu-id="43b18-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="43b18-108">Attribute</span></span>|<span data-ttu-id="43b18-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="43b18-109">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="43b18-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="43b18-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="43b18-111">Contém as informações para a classe de criptografia.</span><span class="sxs-lookup"><span data-stu-id="43b18-111">Contains the information for the cryptography class.</span></span> <span data-ttu-id="43b18-112">Use esse atributo para fornecer um nome curto para sua classe.</span><span class="sxs-lookup"><span data-stu-id="43b18-112">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="43b18-113">Você deve especificar uma cadeia de caracteres que atenda aos requisitos especificados na [especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="43b18-113">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43b18-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="43b18-114">Child Elements</span></span>  
 <span data-ttu-id="43b18-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="43b18-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43b18-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="43b18-116">Parent Elements</span></span>  
  
|<span data-ttu-id="43b18-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="43b18-117">Element</span></span>|<span data-ttu-id="43b18-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="43b18-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="43b18-119">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43b18-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="43b18-120">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no [\<nameEntry>](nameentry-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="43b18-120">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="43b18-121">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="43b18-121">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="43b18-122">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="43b18-122">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="43b18-123">Contém o [\<cryptographySettings>](cryptographysettings-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="43b18-123">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="43b18-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43b18-124">Example</span></span>  
 <span data-ttu-id="43b18-125">O exemplo a seguir mostra como usar o **\<cryptoClass>** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="43b18-125">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="43b18-126">Em seguida, você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e usar o <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="43b18-126">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43b18-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="43b18-127">See also</span></span>

- [<span data-ttu-id="43b18-128">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="43b18-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="43b18-129">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="43b18-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="43b18-130">Serviços de Criptografia</span><span class="sxs-lookup"><span data-stu-id="43b18-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="43b18-131">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="43b18-131">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
