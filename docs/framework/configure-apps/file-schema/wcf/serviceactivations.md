---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: fb7c699612ef12aae39aaeadaf170d0e8f2553cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936443"
---
# <a name="serviceactivations"></a><span data-ttu-id="63aba-101">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="63aba-101">\<serviceActivations></span></span>

<span data-ttu-id="63aba-102">Um elemento de configuração que permite adicionar configurações que definem as configurações de ativação de serviço virtual que são mapeadas para seus tipos de serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="63aba-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="63aba-103">Isso possibilita a ativação de serviços hospedados no WAS/IIS sem um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="63aba-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="63aba-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="63aba-104">\<system.ServiceModel></span></span>\
<span data-ttu-id="63aba-105">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="63aba-105">\<serviceHostingEnvironment></span></span>\
<span data-ttu-id="63aba-106">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="63aba-106">\<serviceActivations></span></span>

## <a name="syntax"></a><span data-ttu-id="63aba-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63aba-107">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63aba-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="63aba-108">Attributes and Elements</span></span>

<span data-ttu-id="63aba-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="63aba-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="63aba-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="63aba-110">Attributes</span></span>

<span data-ttu-id="63aba-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="63aba-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="63aba-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="63aba-112">Child Elements</span></span>

|<span data-ttu-id="63aba-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="63aba-113">Element</span></span>|<span data-ttu-id="63aba-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="63aba-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63aba-115">\<add></span><span class="sxs-lookup"><span data-stu-id="63aba-115">\<add></span></span>](add-of-serviceactivations.md)|<span data-ttu-id="63aba-116">Adiciona um elemento de configuração que especifica a ativação de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="63aba-116">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="63aba-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="63aba-117">Parent Elements</span></span>

|<span data-ttu-id="63aba-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="63aba-118">Element</span></span>|<span data-ttu-id="63aba-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="63aba-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63aba-120">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="63aba-120">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="63aba-121">Define o tipo que o ambiente de Hospedagem de serviço instancia para um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="63aba-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="63aba-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="63aba-122">Remarks</span></span>

<span data-ttu-id="63aba-123">O exemplo a seguir mostra como definir as configurações de ativação no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="63aba-123">The following example shows how to configure activation settings within your web.config file.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="63aba-124">Usando essa configuração, você pode ativar o GreetingService sem usar um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="63aba-124">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="63aba-125">Observe que `<serviceHostingEnvironment>` é uma configuração de nível de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63aba-125">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="63aba-126">Você precisa posicionar o `web.config` que contém a configuração na raiz do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="63aba-126">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="63aba-127">Além disso, `serviceHostingEnvironment` é uma seção de reherança de machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="63aba-127">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="63aba-128">Se você registrar um único serviço na raiz do computador, cada serviço no aplicativo herdará esse serviço.</span><span class="sxs-lookup"><span data-stu-id="63aba-128">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="63aba-129">A ativação baseada em configuração dá suporte à ativação por meio do protocolo http e não http.</span><span class="sxs-lookup"><span data-stu-id="63aba-129">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="63aba-130">Ele requer extensões em relativeAddress, ou seja,. svc,. xoml ou. xamlx.</span><span class="sxs-lookup"><span data-stu-id="63aba-130">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="63aba-131">Você pode mapear suas próprias extensões para o know buildProviders, que permitirá que você ative o serviço em qualquer extensão.</span><span class="sxs-lookup"><span data-stu-id="63aba-131">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="63aba-132">Após o conflito, `<serviceActivations>` a seção substitui os registros. svc.</span><span class="sxs-lookup"><span data-stu-id="63aba-132">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="63aba-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63aba-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
