---
title: "Ativação com base em configuração no ISS e WAS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0938b98a3f079d03653df55f10c26a4a62db5bf3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="24202-102">Ativação com base em configuração no ISS e WAS</span><span class="sxs-lookup"><span data-stu-id="24202-102">Configuration-Based Activation in IIS and WAS</span></span>
<span data-ttu-id="24202-103">Normalmente, ao hospedar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço em serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS), você deve fornecer um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="24202-103">Normally when hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="24202-104">O arquivo. svc contém o nome do serviço e uma fábrica de host de serviço personalizada opcional.</span><span class="sxs-lookup"><span data-stu-id="24202-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="24202-105">Esse arquivo adicional aumenta a sobrecarga de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="24202-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="24202-106">O recurso de ativação com base em configuração remove a necessidade de ter um arquivo. svc e, portanto, os respectivos sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="24202-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>  
  
## <a name="configuration-based-activation"></a><span data-ttu-id="24202-107">Ativação com base em configuração</span><span class="sxs-lookup"><span data-stu-id="24202-107">Configuration-Based Activation</span></span>  
 <span data-ttu-id="24202-108">Ativação baseada em configuração usa os metadados que costumava ser colocado no arquivo. svc e o coloca no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="24202-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="24202-109">Dentro de <`serviceHostingEnvironment`> elemento há um <`serviceActivations`> elemento.</span><span class="sxs-lookup"><span data-stu-id="24202-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="24202-110">Dentro de <`serviceActivations`> elemento são um ou mais <`add`> elementos, um para cada serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="24202-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="24202-111">O <`add`> elemento contém atributos que permitem que você defina o endereço relativo para o serviço e o tipo de serviço ou uma fábrica de host de serviço.</span><span class="sxs-lookup"><span data-stu-id="24202-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="24202-112">O código de exemplo de configuração a seguir mostra como esta seção é usada.</span><span class="sxs-lookup"><span data-stu-id="24202-112">The following configuration example code shows how this section is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24202-113">Cada <`add`> elemento deve especificar um serviço ou um atributo de fábrica.</span><span class="sxs-lookup"><span data-stu-id="24202-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="24202-114">Especificando atributos de fábrica e o serviço é permitido.</span><span class="sxs-lookup"><span data-stu-id="24202-114">Specifying both service and factory attributes is allowed.</span></span>  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 <span data-ttu-id="24202-115">Com isso no arquivo Web. config, você pode colocar o código de serviço de origem no diretório App_Code do aplicativo ou um assembly compilado no diretório Bin do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24202-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="24202-116">Ao usar a ativação baseada em configuração, não há suporte para código embutido em arquivos. svc.</span><span class="sxs-lookup"><span data-stu-id="24202-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>  
> -   <span data-ttu-id="24202-117">O `relativeAddress` atributo deve ser definido como um endereço relativo, como "\<subdiretório > / SVC" ou "~ /\<sub-directory/SVC".</span><span class="sxs-lookup"><span data-stu-id="24202-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>  
> -   <span data-ttu-id="24202-118">Uma exceção de configuração é gerada se você registrar um endereço relativo que não tem uma extensão conhecida associada com o WCF.</span><span class="sxs-lookup"><span data-stu-id="24202-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>  
> -   <span data-ttu-id="24202-119">O endereço relativo especificado é relativo à raiz do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="24202-119">The relative address specified is relative to the root of the virtual application.</span></span>  
> -   <span data-ttu-id="24202-120">Devido ao modelo hierárquico da configuração, os endereços relativos registrados no nível de máquina e de site são herdados por aplicativos virtuais.</span><span class="sxs-lookup"><span data-stu-id="24202-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>  
> -   <span data-ttu-id="24202-121">Os registros de um arquivo de configuração têm precedência sobre as configurações em um SVC, .xamlx,. xoml ou outro arquivo.</span><span class="sxs-lookup"><span data-stu-id="24202-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>  
> -   <span data-ttu-id="24202-122">Qualquer ' \' (barras invertidas) em um URI enviado ao IIS / WAS são automaticamente convertidos para um '/' (barra).</span><span class="sxs-lookup"><span data-stu-id="24202-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="24202-123">Se um endereço relativo é adicionado, que contém um ' \' e enviar um URI que usa o endereço relativo do IIS, a barra invertida é convertida em uma barra invertida e o IIS não pode corresponder ao endereço relativo.</span><span class="sxs-lookup"><span data-stu-id="24202-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="24202-124">IIS envia informações de rastreamento que indica que não há nenhuma correspondência encontrada.</span><span class="sxs-lookup"><span data-stu-id="24202-124">IIS sends out trace information that indicates that there are no matches found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24202-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24202-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 <span data-ttu-id="24202-126">[Hosting Services](../../../../docs/framework/wcf/hosting-services.md) (Hospedando serviços)</span><span class="sxs-lookup"><span data-stu-id="24202-126">[Hosting Services](../../../../docs/framework/wcf/hosting-services.md)</span></span>  
 [<span data-ttu-id="24202-127">Visão geral dos serviços de fluxo de trabalho hospedagem</span><span class="sxs-lookup"><span data-stu-id="24202-127">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [<span data-ttu-id="24202-128">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="24202-128">\<serviceHostingEnvironment></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [<span data-ttu-id="24202-129">Recursos de hospedagem do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="24202-129">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
