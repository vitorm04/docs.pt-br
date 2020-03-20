---
title: Elemento <system.web> (Configurações da Web)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152835"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="cdc49-102">\<system.web> Element (Web Settings) [Elemento system.web> (configurações da Web)]</span><span class="sxs-lookup"><span data-stu-id="cdc49-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="cdc49-103">Contém informações sobre como a camada de hospedagem ASP.NET gerencia o comportamento em todo o processo.</span><span class="sxs-lookup"><span data-stu-id="cdc49-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[<span data-ttu-id="cdc49-104">**\<>de configuração**</span><span class="sxs-lookup"><span data-stu-id="cdc49-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="cdc49-105">&nbsp;&nbsp;**\<system.web>**</span><span class="sxs-lookup"><span data-stu-id="cdc49-105">&nbsp;&nbsp;**\<system.web>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdc49-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdc49-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdc49-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cdc49-107">Attributes and Elements</span></span>  

<span data-ttu-id="cdc49-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cdc49-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdc49-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="cdc49-109">Attributes</span></span>  

<span data-ttu-id="cdc49-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cdc49-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cdc49-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cdc49-111">Child Elements</span></span>  
  
|<span data-ttu-id="cdc49-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="cdc49-112">Element</span></span>|<span data-ttu-id="cdc49-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdc49-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdc49-114">\<>de pool de aplicativos</span><span class="sxs-lookup"><span data-stu-id="cdc49-114">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="cdc49-115">Especifica as configurações de configuração para pools de aplicativos IIS em um arquivo aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="cdc49-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cdc49-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cdc49-116">Parent Elements</span></span>  
  
|<span data-ttu-id="cdc49-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="cdc49-117">Element</span></span>|<span data-ttu-id="cdc49-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdc49-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdc49-119">\<>de configuração</span><span class="sxs-lookup"><span data-stu-id="cdc49-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="cdc49-120">Especifica o elemento raiz em cada arquivo de configuração que é usado pelos aplicativos common language runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cdc49-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdc49-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="cdc49-121">Remarks</span></span>  

<span data-ttu-id="cdc49-122">O `system.web` elemento e `applicationPool` seu elemento filho foram adicionados ao Quadro .NET a partir do Quadro .NET 3.5 SP1.</span><span class="sxs-lookup"><span data-stu-id="cdc49-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="cdc49-123">Quando você executa versões IIS 7.0 ou posteriores no modo Integrado, essa combinação de elementos permite configurar como ASP.NET gerencia threads e como ele faz filas quando ASP.NET está hospedado em um pool de aplicativos IIS.</span><span class="sxs-lookup"><span data-stu-id="cdc49-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="cdc49-124">Se você executar versões IIS 7.0 ou posteriores no modo Classic ou ISAPI, essas configurações serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="cdc49-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdc49-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cdc49-125">Example</span></span>  

<span data-ttu-id="cdc49-126">O exemplo a seguir mostra como configurar ASP.NET comportamento em todo o processo no arquivo aspnet.config quando ASP.NET está hospedado em um pool de aplicativos IIS.</span><span class="sxs-lookup"><span data-stu-id="cdc49-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="cdc49-127">O exemplo pressupõe que o IIS está sendo executado no modo Integrado e que o aplicativo está usando o .NET Framework 3.5 SP1 ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="cdc49-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="cdc49-128">Esse comportamento não ocorre em versões do Quadro .NET antes do Quadro .NET 3.5 SP1.</span><span class="sxs-lookup"><span data-stu-id="cdc49-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="cdc49-129">Os valores no exemplo são os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="cdc49-129">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool
        maxConcurrentRequestsPerCPU="5000"
        maxConcurrentThreadsPerCPU="0"
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="cdc49-130">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="cdc49-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cdc49-131">Namespace</span><span class="sxs-lookup"><span data-stu-id="cdc49-131">Namespace</span></span>||  
|<span data-ttu-id="cdc49-132">Nome do Esquema</span><span class="sxs-lookup"><span data-stu-id="cdc49-132">Schema Name</span></span>||  
|<span data-ttu-id="cdc49-133">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="cdc49-133">Validation File</span></span>||  
|<span data-ttu-id="cdc49-134">Pode ser vazio</span><span class="sxs-lookup"><span data-stu-id="cdc49-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="cdc49-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="cdc49-135">See also</span></span>

- [<span data-ttu-id="cdc49-136">\<aplicativoPool> Element (Configurações da Web)</span><span class="sxs-lookup"><span data-stu-id="cdc49-136">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
