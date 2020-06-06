---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: a54f5ce86aee1a5e831c0b10aa1471d4a82f40a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251800"
---
# \<system.identityModel>
<span data-ttu-id="a842c-102">Fornece a configuração para habilitar as opções do Windows Identity Foundation (WIF) em aplicativos.</span><span class="sxs-lookup"><span data-stu-id="a842c-102">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel>**  
  
## <a name="syntax"></a><span data-ttu-id="a842c-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a842c-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a842c-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a842c-104">Attributes and Elements</span></span>  
 <span data-ttu-id="a842c-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a842c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a842c-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="a842c-106">Attributes</span></span>  
 <span data-ttu-id="a842c-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a842c-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a842c-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a842c-108">Child Elements</span></span>  
  
|<span data-ttu-id="a842c-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="a842c-109">Element</span></span>|<span data-ttu-id="a842c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a842c-110">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="a842c-111">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="a842c-111">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a842c-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a842c-112">Parent Elements</span></span>  
  
|<span data-ttu-id="a842c-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="a842c-113">Element</span></span>|<span data-ttu-id="a842c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a842c-114">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="a842c-115">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a842c-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a842c-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="a842c-116">Remarks</span></span>  
 <span data-ttu-id="a842c-117">Adicione uma `<system.identityModel>` seção ao arquivo de configuração para configurar um serviço ou aplicativo para usar o Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="a842c-117">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="a842c-118">O `<system.identityModel>` elemento é representado pela <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> classe.</span><span class="sxs-lookup"><span data-stu-id="a842c-118">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a842c-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a842c-119">Example</span></span>  
 <span data-ttu-id="a842c-120">O exemplo a seguir mostra como adicionar uma `<system.identityModel>` seção a um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="a842c-120">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="a842c-121">Você deve primeiro adicionar a seção de configuração e a declaração de namespace sob o `<configSections>` elemento.</span><span class="sxs-lookup"><span data-stu-id="a842c-121">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="a842c-122">Em seguida, você pode adicionar o `<system.IdentityModel>` elemento ao arquivo de configuração para especificar uma ou mais configurações de identidade.</span><span class="sxs-lookup"><span data-stu-id="a842c-122">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a842c-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="a842c-123">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
