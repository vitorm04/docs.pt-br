---
title: <add> de <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850321"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="0d634-102">\<Adicionar > de \<perativações ></span><span class="sxs-lookup"><span data-stu-id="0d634-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="0d634-103">Um elemento de configuração que permite definir configurações de ativação de serviço virtual que são mapeadas para seus tipos de serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0d634-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="0d634-104">Isso possibilita a ativação de serviços hospedados no WAS/IIS sem um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="0d634-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="0d634-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d634-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0d634-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0d634-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0d634-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de ServiceHostingEnvironment**](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="0d634-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="0d634-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de imativações**](serviceactivations.md)</span><span class="sxs-lookup"><span data-stu-id="0d634-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)</span></span>\
<span data-ttu-id="0d634-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="0d634-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="0d634-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d634-110">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d634-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0d634-111">Attributes and Elements</span></span>

<span data-ttu-id="0d634-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0d634-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d634-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="0d634-113">Attributes</span></span>

|<span data-ttu-id="0d634-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="0d634-114">Attribute</span></span>|<span data-ttu-id="0d634-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d634-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="0d634-116">padrões</span><span class="sxs-lookup"><span data-stu-id="0d634-116">factory</span></span>|<span data-ttu-id="0d634-117">Uma cadeia de caracteres que especifica o nome do tipo CLR da fábrica que gera um elemento de ativação de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d634-117">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="0d634-118">serviço</span><span class="sxs-lookup"><span data-stu-id="0d634-118">service</span></span>|<span data-ttu-id="0d634-119">O ServiceType que implementa o serviço (o TypeName totalmente qualificado ou o TypeName curto (quando ele é colocado na pasta App_Code).</span><span class="sxs-lookup"><span data-stu-id="0d634-119">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="0d634-120">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="0d634-120">relativeAddress</span></span>|<span data-ttu-id="0d634-121">O endereço relativo no aplicativo IIS atual-por exemplo, "Service. svc".</span><span class="sxs-lookup"><span data-stu-id="0d634-121">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="0d634-122">No WCF 4,0, esse endereço relativo deve conter uma das extensões de arquivo conhecidas (. svc,. xamlx,...). Nenhum arquivo físico deve existir para o relativeUrl</span><span class="sxs-lookup"><span data-stu-id="0d634-122">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0d634-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0d634-123">Child Elements</span></span>

<span data-ttu-id="0d634-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0d634-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0d634-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0d634-125">Parent Elements</span></span>

|<span data-ttu-id="0d634-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d634-126">Element</span></span>|<span data-ttu-id="0d634-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d634-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d634-128">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="0d634-128">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="0d634-129">Uma seção de configuração que descreve as configurações de ativação.</span><span class="sxs-lookup"><span data-stu-id="0d634-129">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0d634-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d634-130">Remarks</span></span>

<span data-ttu-id="0d634-131">O exemplo a seguir mostra como definir as configurações de ativação no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="0d634-131">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="0d634-132">Usando essa configuração, você pode ativar o GreetingService sem usar um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="0d634-132">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="0d634-133">Observe que `<serviceHostingEnvironment>` é uma configuração de nível de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0d634-133">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="0d634-134">Você precisa posicionar o `web.config` que contém a configuração na raiz do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="0d634-134">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="0d634-135">Além disso, `serviceHostingEnvironment` é uma seção de reherança de machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="0d634-135">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="0d634-136">Se você registrar um único serviço na raiz do computador, cada serviço no aplicativo herdará esse serviço.</span><span class="sxs-lookup"><span data-stu-id="0d634-136">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="0d634-137">A ativação baseada em configuração dá suporte à ativação por meio do protocolo http e não http.</span><span class="sxs-lookup"><span data-stu-id="0d634-137">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="0d634-138">Ele requer extensões no relativeAddress, ou seja,. svc,. xoml ou. xamlx.</span><span class="sxs-lookup"><span data-stu-id="0d634-138">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="0d634-139">Você pode mapear suas próprias extensões para o know buildProviders, que permitirá que você ative o serviço em qualquer extensão.</span><span class="sxs-lookup"><span data-stu-id="0d634-139">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="0d634-140">Após o conflito, `<serviceActivations>` a seção substitui os registros. svc.</span><span class="sxs-lookup"><span data-stu-id="0d634-140">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d634-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d634-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
