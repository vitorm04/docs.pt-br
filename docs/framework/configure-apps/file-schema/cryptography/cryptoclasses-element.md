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
ms.openlocfilehash: 89b96edcf1da20698cd203e78fa27e644fa69cc3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201818"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="645fc-102">Elemento \<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="645fc-102">\<cryptoClasses> Element</span></span>

<span data-ttu-id="645fc-103">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no [\<nameEntry>](nameentry-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="645fc-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**  
  
## <a name="syntax"></a><span data-ttu-id="645fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="645fc-104">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="645fc-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="645fc-105">Attributes and Elements</span></span>  

 <span data-ttu-id="645fc-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="645fc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="645fc-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="645fc-107">Attributes</span></span>  

 <span data-ttu-id="645fc-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="645fc-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="645fc-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="645fc-109">Child Elements</span></span>  
  
|<span data-ttu-id="645fc-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="645fc-110">Element</span></span>|<span data-ttu-id="645fc-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="645fc-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoClass>](cryptoclass-element.md)|<span data-ttu-id="645fc-112">Contém uma classe de criptografia que tem um mapeamento para um nome amigável no **\<nameEntry>** elemento.</span><span class="sxs-lookup"><span data-stu-id="645fc-112">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="645fc-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="645fc-113">Parent Elements</span></span>  
  
|<span data-ttu-id="645fc-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="645fc-114">Element</span></span>|<span data-ttu-id="645fc-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="645fc-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="645fc-116">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="645fc-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="645fc-117">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="645fc-117">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="645fc-118">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="645fc-118">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="645fc-119">Contém o `cryptographySettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="645fc-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="645fc-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="645fc-120">Example</span></span>  

 <span data-ttu-id="645fc-121">O exemplo a seguir mostra como usar o **\<cryptoClass>** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="645fc-121">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="645fc-122">Em seguida, você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e usar o <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="645fc-122">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="645fc-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="645fc-123">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="645fc-124">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="645fc-124">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="645fc-125">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="645fc-125">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="645fc-126">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="645fc-126">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="645fc-127">System. Security. Cryptography. CryptoConfig. CreateFromName</span><span class="sxs-lookup"><span data-stu-id="645fc-127">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="645fc-128">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="645fc-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
