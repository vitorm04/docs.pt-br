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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155240"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="c89e8-102">Elemento \<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="c89e8-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="c89e8-103">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no [\<nameEntry>](nameentry-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="c89e8-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**  
  
## <a name="syntax"></a><span data-ttu-id="c89e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c89e8-104">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c89e8-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c89e8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c89e8-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c89e8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c89e8-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c89e8-107">Attributes</span></span>  
 <span data-ttu-id="c89e8-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c89e8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c89e8-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c89e8-109">Child Elements</span></span>  
  
|<span data-ttu-id="c89e8-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="c89e8-110">Element</span></span>|<span data-ttu-id="c89e8-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c89e8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoClass>](cryptoclass-element.md)|<span data-ttu-id="c89e8-112">Contém uma classe de criptografia que tem um mapeamento para um nome amigável no **\<nameEntry>** elemento.</span><span class="sxs-lookup"><span data-stu-id="c89e8-112">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c89e8-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c89e8-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c89e8-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="c89e8-114">Element</span></span>|<span data-ttu-id="c89e8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c89e8-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c89e8-116">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c89e8-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="c89e8-117">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="c89e8-117">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="c89e8-118">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="c89e8-118">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="c89e8-119">Contém o `cryptographySettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="c89e8-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c89e8-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c89e8-120">Example</span></span>  
 <span data-ttu-id="c89e8-121">O exemplo a seguir mostra como usar o **\<cryptoClass>** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c89e8-121">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="c89e8-122">Em seguida, você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e usar o <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="c89e8-122">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c89e8-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="c89e8-123">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="c89e8-124">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="c89e8-124">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c89e8-125">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="c89e8-125">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c89e8-126">Serviços de Criptografia</span><span class="sxs-lookup"><span data-stu-id="c89e8-126">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="c89e8-127">System. Security. Cryptography. CryptoConfig. CreateFromName</span><span class="sxs-lookup"><span data-stu-id="c89e8-127">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="c89e8-128">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="c89e8-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
