---
title: <add> de <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850321"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="e2504-102">\<add> de \<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="e2504-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="e2504-103">Um elemento de configuração que permite definir configurações de ativação de serviço virtual que são mapeadas para seus tipos de serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e2504-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="e2504-104">Isso possibilita a ativação de serviços hospedados no WAS/IIS sem um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="e2504-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="e2504-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e2504-105">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2504-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e2504-106">Attributes and Elements</span></span>

<span data-ttu-id="e2504-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e2504-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2504-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="e2504-108">Attributes</span></span>

|<span data-ttu-id="e2504-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="e2504-109">Attribute</span></span>|<span data-ttu-id="e2504-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2504-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="e2504-111">fábrica</span><span class="sxs-lookup"><span data-stu-id="e2504-111">factory</span></span>|<span data-ttu-id="e2504-112">Uma cadeia de caracteres que especifica o nome do tipo CLR da fábrica que gera um elemento de ativação de serviço.</span><span class="sxs-lookup"><span data-stu-id="e2504-112">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="e2504-113">serviço</span><span class="sxs-lookup"><span data-stu-id="e2504-113">service</span></span>|<span data-ttu-id="e2504-114">O ServiceType que implementa o serviço (o TypeName totalmente qualificado ou o TypeName curto (quando é colocado na pasta App_Code).</span><span class="sxs-lookup"><span data-stu-id="e2504-114">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="e2504-115">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="e2504-115">relativeAddress</span></span>|<span data-ttu-id="e2504-116">O endereço relativo no aplicativo IIS atual-por exemplo, "Service. svc".</span><span class="sxs-lookup"><span data-stu-id="e2504-116">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="e2504-117">No WCF 4,0, esse endereço relativo deve conter uma das extensões de arquivo conhecidas (. svc,. xamlx,...). Nenhum arquivo físico deve existir para o relativeUrl</span><span class="sxs-lookup"><span data-stu-id="e2504-117">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e2504-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e2504-118">Child Elements</span></span>

<span data-ttu-id="e2504-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e2504-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e2504-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e2504-120">Parent Elements</span></span>

|<span data-ttu-id="e2504-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e2504-121">Element</span></span>|<span data-ttu-id="e2504-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2504-122">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="e2504-123">Uma seção de configuração que descreve as configurações de ativação.</span><span class="sxs-lookup"><span data-stu-id="e2504-123">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e2504-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="e2504-124">Remarks</span></span>

<span data-ttu-id="e2504-125">O exemplo a seguir mostra como definir as configurações de ativação no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="e2504-125">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="e2504-126">Usando essa configuração, você pode ativar o GreetingService sem usar um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="e2504-126">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="e2504-127">Observe que `<serviceHostingEnvironment>` é uma configuração de nível de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e2504-127">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="e2504-128">Você precisa posicionar o `web.config` que contém a configuração na raiz do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="e2504-128">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="e2504-129">Além disso, `serviceHostingEnvironment` é uma seção de reherança de machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="e2504-129">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="e2504-130">Se você registrar um único serviço na raiz do computador, cada serviço no aplicativo herdará esse serviço.</span><span class="sxs-lookup"><span data-stu-id="e2504-130">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="e2504-131">A ativação baseada em configuração dá suporte à ativação por meio do protocolo http e não http.</span><span class="sxs-lookup"><span data-stu-id="e2504-131">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="e2504-132">Ele requer extensões no relativeAddress, ou seja,. svc,. xoml ou. xamlx.</span><span class="sxs-lookup"><span data-stu-id="e2504-132">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="e2504-133">Você pode mapear suas próprias extensões para o know buildProviders, que permitirá que você ative o serviço em qualquer extensão.</span><span class="sxs-lookup"><span data-stu-id="e2504-133">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="e2504-134">Após o conflito, a `<serviceActivations>` seção substitui os registros. svc.</span><span class="sxs-lookup"><span data-stu-id="e2504-134">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2504-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="e2504-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
