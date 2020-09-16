---
title: Ativação com base em configuração no ISS e WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: f947a64acdf602d12fcd2319a1b994912ecb331e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556623"
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="b0111-102">Ativação com base em configuração no ISS e WAS</span><span class="sxs-lookup"><span data-stu-id="b0111-102">Configuration-Based Activation in IIS and WAS</span></span>

<span data-ttu-id="b0111-103">Normalmente, ao hospedar um serviço de Windows Communication Foundation (WCF) em Serviços de Informações da Internet (IIS) ou no WAS (serviço de ativação de processos do Windows), você deve fornecer um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="b0111-103">Normally when hosting a Windows Communication Foundation (WCF) service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="b0111-104">O arquivo. svc contém o nome do serviço e uma fábrica de host de serviço personalizada opcional.</span><span class="sxs-lookup"><span data-stu-id="b0111-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="b0111-105">Esse arquivo adicional adiciona sobrecarga de gerenciabilidade.</span><span class="sxs-lookup"><span data-stu-id="b0111-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="b0111-106">O recurso de ativação baseada em configuração remove a necessidade de ter um arquivo. svc e, portanto, a sobrecarga associada.</span><span class="sxs-lookup"><span data-stu-id="b0111-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>

## <a name="configuration-based-activation"></a><span data-ttu-id="b0111-107">Ativação com base em configuração</span><span class="sxs-lookup"><span data-stu-id="b0111-107">Configuration-Based Activation</span></span>

<span data-ttu-id="b0111-108">A ativação baseada em configuração usa os metadados que costumava ser colocados no arquivo. svc e os coloca no arquivo de Web.config.</span><span class="sxs-lookup"><span data-stu-id="b0111-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="b0111-109">Dentro do `serviceHostingEnvironment` elemento<> há um elemento <`serviceActivations`>.</span><span class="sxs-lookup"><span data-stu-id="b0111-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="b0111-110">Dentro do `serviceActivations` elemento <> há um ou mais `add` elementos de> <, um para cada serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="b0111-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="b0111-111">O `add` elemento <> contém atributos que permitem definir o endereço relativo para o serviço e o tipo de serviço ou uma fábrica de host de serviço.</span><span class="sxs-lookup"><span data-stu-id="b0111-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="b0111-112">O código de exemplo de configuração a seguir mostra como essa seção é usada.</span><span class="sxs-lookup"><span data-stu-id="b0111-112">The following configuration example code shows how this section is used.</span></span>

> [!NOTE]
> <span data-ttu-id="b0111-113">Cada `add` elemento de> de <deve especificar um atributo de serviço ou de fábrica.</span><span class="sxs-lookup"><span data-stu-id="b0111-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="b0111-114">É permitido especificar os atributos de serviço e de fábrica.</span><span class="sxs-lookup"><span data-stu-id="b0111-114">Specifying both service and factory attributes is allowed.</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 <span data-ttu-id="b0111-115">Com isso no arquivo Web.config, você pode posicionar o código-fonte do serviço no diretório App_Code do aplicativo ou um assembly em conformidade no diretório bin do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b0111-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="b0111-116">Ao usar a ativação baseada em configuração, não há suporte para código embutido em arquivos. svc.</span><span class="sxs-lookup"><span data-stu-id="b0111-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>
> - <span data-ttu-id="b0111-117">O `relativeAddress` atributo deve ser definido como um endereço relativo, como " \<sub-directory> /Service.svc" ou "~/ \< sub-Directory/Service. svc".</span><span class="sxs-lookup"><span data-stu-id="b0111-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>
> - <span data-ttu-id="b0111-118">Uma exceção de configuração será gerada se você registrar um endereço relativo que não tenha uma extensão conhecida associada ao WCF.</span><span class="sxs-lookup"><span data-stu-id="b0111-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>
> - <span data-ttu-id="b0111-119">O endereço relativo especificado é relativo à raiz do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="b0111-119">The relative address specified is relative to the root of the virtual application.</span></span>
> - <span data-ttu-id="b0111-120">Devido ao modelo hierárquico da configuração, os endereços relativos registrados no nível do computador e do site são herdados por aplicativos virtuais.</span><span class="sxs-lookup"><span data-stu-id="b0111-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>
> - <span data-ttu-id="b0111-121">Os registros em um arquivo de configuração têm precedência sobre as configurações em um. svc,. xamlx,. xoml ou outro arquivo.</span><span class="sxs-lookup"><span data-stu-id="b0111-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>
> - <span data-ttu-id="b0111-122">Qualquer ' \ ' (barras invertidas) em um URI enviado para o IIS/WAS é convertido automaticamente em um '/' (barra "/").</span><span class="sxs-lookup"><span data-stu-id="b0111-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="b0111-123">Se um endereço relativo for adicionado que contenha um ' \ ' e você enviar um URI que usa o endereço relativo, a barra invertida será convertida em uma barra e o IIS não poderá corresponder ao endereço relativo.</span><span class="sxs-lookup"><span data-stu-id="b0111-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="b0111-124">O IIS envia informações de rastreamento que indicam que não foram encontradas correspondências.</span><span class="sxs-lookup"><span data-stu-id="b0111-124">IIS sends out trace information that indicates that there are no matches found.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0111-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="b0111-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [<span data-ttu-id="b0111-126">Serviços de hospedagem</span><span class="sxs-lookup"><span data-stu-id="b0111-126">Hosting Services</span></span>](../hosting-services.md)
- [<span data-ttu-id="b0111-127">Visão geral de serviços de fluxo de trabalho de hospedagem</span><span class="sxs-lookup"><span data-stu-id="b0111-127">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md)
- <span data-ttu-id="b0111-128">[Recursos de hospedagem do Windows Server AppFabric](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b0111-128">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
