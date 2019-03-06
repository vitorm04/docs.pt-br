---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: fd17c0318480f5e157c8c9114116735b82bbfcef
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351288"
---
# <a name="systemidentitymodel"></a><span data-ttu-id="105e6-102">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="105e6-102">\<system.identityModel></span></span>
<span data-ttu-id="105e6-103">Fornece configuração para habilitar as opções do Windows Identity Foundation (WIF) em aplicativos.</span><span class="sxs-lookup"><span data-stu-id="105e6-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
 <span data-ttu-id="105e6-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="105e6-104">\<system.identityModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="105e6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="105e6-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="105e6-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="105e6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="105e6-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="105e6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="105e6-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="105e6-108">Attributes</span></span>  
 <span data-ttu-id="105e6-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="105e6-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="105e6-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="105e6-110">Child Elements</span></span>  
  
|<span data-ttu-id="105e6-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="105e6-111">Element</span></span>|<span data-ttu-id="105e6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="105e6-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="105e6-113">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="105e6-113">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="105e6-114">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="105e6-114">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="105e6-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="105e6-115">Parent Elements</span></span>  
  
|<span data-ttu-id="105e6-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="105e6-116">Element</span></span>|<span data-ttu-id="105e6-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="105e6-117">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="105e6-118">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="105e6-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="105e6-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="105e6-119">Remarks</span></span>  
 <span data-ttu-id="105e6-120">Adicionar um `<system.identityModel>` seção ao arquivo de configuração para configurar um serviço ou aplicativo para usar o Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="105e6-120">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="105e6-121">O `<system.identityModel>` elemento é representado pelo <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> classe.</span><span class="sxs-lookup"><span data-stu-id="105e6-121">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="105e6-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="105e6-122">Example</span></span>  
 <span data-ttu-id="105e6-123">O exemplo a seguir mostra como adicionar um `<system.identityModel>` seção ao arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="105e6-123">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="105e6-124">Você deve primeiro adicionar a declaração de namespace e a seção de configuração sob o `<configSections>` elemento.</span><span class="sxs-lookup"><span data-stu-id="105e6-124">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="105e6-125">Em seguida, você pode adicionar o `<system.IdentityModel>` elemento ao seu arquivo de configuração para especificar uma ou mais configurações de identidade.</span><span class="sxs-lookup"><span data-stu-id="105e6-125">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="105e6-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="105e6-126">See also</span></span>
- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
