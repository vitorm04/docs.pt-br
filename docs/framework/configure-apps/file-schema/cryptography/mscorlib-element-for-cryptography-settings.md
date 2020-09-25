---
title: Elemento <mscorlib> para configurações de criptografia
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: 1788205997d0dc49df172c9dfe48faceb8fc3290
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201779"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="58605-102">Elemento \<mscorlib> para configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="58605-102">\<mscorlib> Element for Cryptography Settings</span></span>

<span data-ttu-id="58605-103">Contém o [ \<cryptographySettings> elemento](cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="58605-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<mscorlib>**  
  
## <a name="syntax"></a><span data-ttu-id="58605-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58605-104">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58605-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="58605-105">Attributes and Elements</span></span>  

 <span data-ttu-id="58605-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="58605-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58605-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="58605-107">Attributes</span></span>  

 <span data-ttu-id="58605-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="58605-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="58605-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="58605-109">Child Elements</span></span>  
  
|<span data-ttu-id="58605-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="58605-110">Element</span></span>|<span data-ttu-id="58605-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="58605-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="58605-112">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="58605-112">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58605-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="58605-113">Parent Elements</span></span>  
  
|<span data-ttu-id="58605-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="58605-114">Element</span></span>|<span data-ttu-id="58605-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="58605-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="58605-116">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="58605-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="58605-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="58605-117">Example</span></span>  

 <span data-ttu-id="58605-118">O exemplo a seguir mostra como usar o **\<mscorlib>** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="58605-118">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="58605-119">Em seguida, você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e usar o <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="58605-119">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58605-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="58605-120">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="58605-121">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="58605-121">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="58605-122">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="58605-122">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="58605-123">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="58605-123">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="58605-124">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="58605-124">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
