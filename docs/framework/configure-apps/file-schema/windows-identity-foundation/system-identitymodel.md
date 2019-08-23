---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: 286ae88946692e6894ca3c7ee9e1348415c84ade
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943593"
---
# <a name="systemidentitymodel"></a><span data-ttu-id="04250-102">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="04250-102">\<system.identityModel></span></span>
<span data-ttu-id="04250-103">Fornece a configuração para habilitar as opções do Windows Identity Foundation (WIF) em aplicativos.</span><span class="sxs-lookup"><span data-stu-id="04250-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
 <span data-ttu-id="04250-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="04250-104">\<system.identityModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04250-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04250-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04250-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="04250-106">Attributes and Elements</span></span>  
 <span data-ttu-id="04250-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="04250-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04250-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="04250-108">Attributes</span></span>  
 <span data-ttu-id="04250-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="04250-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="04250-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="04250-110">Child Elements</span></span>  
  
|<span data-ttu-id="04250-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="04250-111">Element</span></span>|<span data-ttu-id="04250-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="04250-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04250-113">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="04250-113">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="04250-114">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="04250-114">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="04250-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="04250-115">Parent Elements</span></span>  
  
|<span data-ttu-id="04250-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="04250-116">Element</span></span>|<span data-ttu-id="04250-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="04250-117">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="04250-118">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="04250-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04250-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="04250-119">Remarks</span></span>  
 <span data-ttu-id="04250-120">Adicione uma `<system.identityModel>` seção ao arquivo de configuração para configurar um serviço ou aplicativo para usar o Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="04250-120">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="04250-121">O `<system.identityModel>` elemento é representado <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> pela classe.</span><span class="sxs-lookup"><span data-stu-id="04250-121">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04250-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="04250-122">Example</span></span>  
 <span data-ttu-id="04250-123">O exemplo a seguir mostra como adicionar uma `<system.identityModel>` seção a um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="04250-123">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="04250-124">Você deve primeiro adicionar a seção de configuração e a declaração de `<configSections>` namespace sob o elemento.</span><span class="sxs-lookup"><span data-stu-id="04250-124">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="04250-125">Em seguida, você pode `<system.IdentityModel>` adicionar o elemento ao arquivo de configuração para especificar uma ou mais configurações de identidade.</span><span class="sxs-lookup"><span data-stu-id="04250-125">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="04250-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04250-126">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
