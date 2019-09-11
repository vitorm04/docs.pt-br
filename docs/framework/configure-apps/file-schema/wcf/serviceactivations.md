---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 64ae0bfd90ae941fc78515c7936c998201c87485
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855140"
---
# <a name="serviceactivations"></a><span data-ttu-id="54e2f-101">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="54e2f-101">\<serviceActivations></span></span>

<span data-ttu-id="54e2f-102">Um elemento de configuração que permite adicionar configurações que definem as configurações de ativação de serviço virtual que são mapeadas para seus tipos de serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="54e2f-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="54e2f-103">Isso possibilita a ativação de serviços hospedados no WAS/IIS sem um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="54e2f-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="54e2f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="54e2f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="54e2f-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="54e2f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="54e2f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de ServiceHostingEnvironment**](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="54e2f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="54e2f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de imativações**</span><span class="sxs-lookup"><span data-stu-id="54e2f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="54e2f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54e2f-108">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54e2f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="54e2f-109">Attributes and Elements</span></span>

<span data-ttu-id="54e2f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="54e2f-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="54e2f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="54e2f-111">Attributes</span></span>

<span data-ttu-id="54e2f-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="54e2f-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54e2f-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="54e2f-113">Child Elements</span></span>

|<span data-ttu-id="54e2f-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="54e2f-114">Element</span></span>|<span data-ttu-id="54e2f-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="54e2f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54e2f-116">\<add></span><span class="sxs-lookup"><span data-stu-id="54e2f-116">\<add></span></span>](add-of-serviceactivations.md)|<span data-ttu-id="54e2f-117">Adiciona um elemento de configuração que especifica a ativação de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="54e2f-117">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="54e2f-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="54e2f-118">Parent Elements</span></span>

|<span data-ttu-id="54e2f-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="54e2f-119">Element</span></span>|<span data-ttu-id="54e2f-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="54e2f-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54e2f-121">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="54e2f-121">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="54e2f-122">Define o tipo que o ambiente de Hospedagem de serviço instancia para um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="54e2f-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="54e2f-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="54e2f-123">Remarks</span></span>

<span data-ttu-id="54e2f-124">O exemplo a seguir mostra como definir as configurações de ativação no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="54e2f-124">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="54e2f-125">Usando essa configuração, você pode ativar o GreetingService sem usar um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="54e2f-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="54e2f-126">Observe que `<serviceHostingEnvironment>` é uma configuração de nível de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="54e2f-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="54e2f-127">Você precisa posicionar o `web.config` que contém a configuração na raiz do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="54e2f-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="54e2f-128">Além disso, `serviceHostingEnvironment` é uma seção de reherança de machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="54e2f-128">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="54e2f-129">Se você registrar um único serviço na raiz do computador, cada serviço no aplicativo herdará esse serviço.</span><span class="sxs-lookup"><span data-stu-id="54e2f-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="54e2f-130">A ativação baseada em configuração dá suporte à ativação por meio do protocolo http e não http.</span><span class="sxs-lookup"><span data-stu-id="54e2f-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="54e2f-131">Ele requer extensões em relativeAddress, ou seja,. svc,. xoml ou. xamlx.</span><span class="sxs-lookup"><span data-stu-id="54e2f-131">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="54e2f-132">Você pode mapear suas próprias extensões para o know buildProviders, que permitirá que você ative o serviço em qualquer extensão.</span><span class="sxs-lookup"><span data-stu-id="54e2f-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="54e2f-133">Após o conflito, `<serviceActivations>` a seção substitui os registros. svc.</span><span class="sxs-lookup"><span data-stu-id="54e2f-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="54e2f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54e2f-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
