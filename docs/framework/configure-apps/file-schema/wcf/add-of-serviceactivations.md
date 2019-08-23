---
title: <add> de <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 929773fcb6b6a3ee5c75aa970147277d9dbe7b45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920021"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="8dde6-102">\<Adicionar > de \<perativações ></span><span class="sxs-lookup"><span data-stu-id="8dde6-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="8dde6-103">Um elemento de configuração que permite definir configurações de ativação de serviço virtual que são mapeadas para seus tipos de serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8dde6-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="8dde6-104">Isso possibilita a ativação de serviços hospedados no WAS/IIS sem um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="8dde6-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="8dde6-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8dde6-105">\<system.ServiceModel></span></span>\
<span data-ttu-id="8dde6-106">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="8dde6-106">\<serviceHostingEnvironment></span></span>

## <a name="syntax"></a><span data-ttu-id="8dde6-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8dde6-107">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8dde6-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8dde6-108">Attributes and Elements</span></span>

<span data-ttu-id="8dde6-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8dde6-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8dde6-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8dde6-110">Attributes</span></span>

|<span data-ttu-id="8dde6-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="8dde6-111">Attribute</span></span>|<span data-ttu-id="8dde6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8dde6-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="8dde6-113">padrões</span><span class="sxs-lookup"><span data-stu-id="8dde6-113">factory</span></span>|<span data-ttu-id="8dde6-114">Uma cadeia de caracteres que especifica o nome do tipo CLR da fábrica que gera um elemento de ativação de serviço.</span><span class="sxs-lookup"><span data-stu-id="8dde6-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="8dde6-115">serviço</span><span class="sxs-lookup"><span data-stu-id="8dde6-115">service</span></span>|<span data-ttu-id="8dde6-116">O ServiceType que implementa o serviço (o TypeName totalmente qualificado ou o TypeName curto (quando ele é colocado na pasta App_Code).</span><span class="sxs-lookup"><span data-stu-id="8dde6-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="8dde6-117">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="8dde6-117">relativeAddress</span></span>|<span data-ttu-id="8dde6-118">O endereço relativo no aplicativo IIS atual-por exemplo, "Service. svc".</span><span class="sxs-lookup"><span data-stu-id="8dde6-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="8dde6-119">No WCF 4,0, esse endereço relativo deve conter uma das extensões de arquivo conhecidas (. svc,. xamlx,...). Nenhum arquivo físico deve existir para o relativeUrl</span><span class="sxs-lookup"><span data-stu-id="8dde6-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8dde6-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8dde6-120">Child Elements</span></span>

<span data-ttu-id="8dde6-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8dde6-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8dde6-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8dde6-122">Parent Elements</span></span>

|<span data-ttu-id="8dde6-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="8dde6-123">Element</span></span>|<span data-ttu-id="8dde6-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="8dde6-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8dde6-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="8dde6-125">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="8dde6-126">Uma seção de configuração que descreve as configurações de ativação.</span><span class="sxs-lookup"><span data-stu-id="8dde6-126">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8dde6-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="8dde6-127">Remarks</span></span>

<span data-ttu-id="8dde6-128">O exemplo a seguir mostra como definir as configurações de ativação no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="8dde6-128">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="8dde6-129">Usando essa configuração, você pode ativar o GreetingService sem usar um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="8dde6-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="8dde6-130">Observe que `<serviceHostingEnvironment>` é uma configuração de nível de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8dde6-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="8dde6-131">Você precisa posicionar o `web.config` que contém a configuração na raiz do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="8dde6-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="8dde6-132">Além disso, `serviceHostingEnvironment` é uma seção de reherança de machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="8dde6-132">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="8dde6-133">Se você registrar um único serviço na raiz do computador, cada serviço no aplicativo herdará esse serviço.</span><span class="sxs-lookup"><span data-stu-id="8dde6-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="8dde6-134">A ativação baseada em configuração dá suporte à ativação por meio do protocolo http e não http.</span><span class="sxs-lookup"><span data-stu-id="8dde6-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="8dde6-135">Ele requer extensões no relativeAddress, ou seja,. svc,. xoml ou. xamlx.</span><span class="sxs-lookup"><span data-stu-id="8dde6-135">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="8dde6-136">Você pode mapear suas próprias extensões para o know buildProviders, que permitirá que você ative o serviço em qualquer extensão.</span><span class="sxs-lookup"><span data-stu-id="8dde6-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="8dde6-137">Após o conflito, `<serviceActivations>` a seção substitui os registros. svc.</span><span class="sxs-lookup"><span data-stu-id="8dde6-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="8dde6-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8dde6-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
