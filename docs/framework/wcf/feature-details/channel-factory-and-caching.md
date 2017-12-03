---
title: "Cache e fábrica de canal"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1b06d290760afa9a52274c30899e25f00bc18af2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="3cb35-102">Cache e fábrica de canal</span><span class="sxs-lookup"><span data-stu-id="3cb35-102">Channel Factory and Caching</span></span>
<span data-ttu-id="3cb35-103">Os aplicativos cliente do WCF usam a classe <xref:System.ServiceModel.ChannelFactory%601> para criar um canal de comunicação com um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="3cb35-103">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="3cb35-104">Criar instâncias de <xref:System.ServiceModel.ChannelFactory%601> resulta em alguma sobrecarga porque envolve as seguintes operações:</span><span class="sxs-lookup"><span data-stu-id="3cb35-104">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>  
  
-   <span data-ttu-id="3cb35-105">Construir a árvore de <xref:System.ServiceModel.Description.ContractDescription></span><span class="sxs-lookup"><span data-stu-id="3cb35-105">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>  
  
-   <span data-ttu-id="3cb35-106">Refletir todos os tipos CLR necessários</span><span class="sxs-lookup"><span data-stu-id="3cb35-106">Reflecting all of the required CLR types</span></span>  
  
-   <span data-ttu-id="3cb35-107">Construir a pilha de canal</span><span class="sxs-lookup"><span data-stu-id="3cb35-107">Constructing the channel stack</span></span>  
  
-   <span data-ttu-id="3cb35-108">Descarte de recursos</span><span class="sxs-lookup"><span data-stu-id="3cb35-108">Disposing of resources</span></span>  
  
 <span data-ttu-id="3cb35-109">Para ajudar a minimizar a sobrecarga, o WCF pode armazenar em cache fábricas de canal quando você está usando um proxy de cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="3cb35-109">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="3cb35-110">Você tem controle direto sobre a criação da fábrica de canal, quando você usa o <xref:System.ServiceModel.ChannelFactory%601> classe diretamente.</span><span class="sxs-lookup"><span data-stu-id="3cb35-110">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>  
  
 <span data-ttu-id="3cb35-111">Os proxies de cliente WCF gerados com [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) são derivados de <xref:System.ServiceModel.ClientBase%601>.</span><span class="sxs-lookup"><span data-stu-id="3cb35-111">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="3cb35-112"><xref:System.ServiceModel.ClientBase%601>define um estático <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> propriedade que define o comportamento de cache de fábrica de canal.</span><span class="sxs-lookup"><span data-stu-id="3cb35-112"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="3cb35-113">Configurações de cache são feitas para um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="3cb35-113">Cache settings are made for a specific type.</span></span> <span data-ttu-id="3cb35-114">Por exemplo, definindo `ClientBase<ITest>.CacheSettings` para um dos valores definidos abaixo afetará apenas esses proxy/ClientBase do tipo `ITest`.</span><span class="sxs-lookup"><span data-stu-id="3cb35-114">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="3cb35-115">A configuração de cache para um determinado <xref:System.ServiceModel.ClientBase%601> é imutável, assim que a primeira instância de proxy/ClientBase é criada.</span><span class="sxs-lookup"><span data-stu-id="3cb35-115">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>  
  
## <a name="specifying-caching-behavior"></a><span data-ttu-id="3cb35-116">Especificar o comportamento do cache</span><span class="sxs-lookup"><span data-stu-id="3cb35-116">Specifying Caching Behavior</span></span>  
 <span data-ttu-id="3cb35-117">Comportamento do cache é especificado pela configuração de <xref:System.ServiceModel.ClientBase%601.CacheSetting> propriedade para um dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="3cb35-117">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>  
  
|<span data-ttu-id="3cb35-118">Definir o valor de cache</span><span class="sxs-lookup"><span data-stu-id="3cb35-118">Cache Setting Value</span></span>|<span data-ttu-id="3cb35-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="3cb35-119">Description</span></span>|  
|-------------------------|-----------------|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="3cb35-120">Todas as instâncias de <xref:System.ServiceModel.ClientBase%601> dentro do domínio de aplicativo podem participar em cache.</span><span class="sxs-lookup"><span data-stu-id="3cb35-120">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="3cb35-121">O desenvolvedor determinou que não há nenhum implicações de segurança adversas para armazenamento em cache.</span><span class="sxs-lookup"><span data-stu-id="3cb35-121">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="3cb35-122">O cache será não desativado propriedades mesmo que "segurança" <xref:System.ServiceModel.ClientBase%601> são acessados.</span><span class="sxs-lookup"><span data-stu-id="3cb35-122">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="3cb35-123">As propriedades de "segurança" de <xref:System.ServiceModel.ClientBase%601> são <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> e <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span><span class="sxs-lookup"><span data-stu-id="3cb35-123">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="3cb35-124">Apenas instâncias do <xref:System.ServiceModel.ClientBase%601> criado a partir de pontos de extremidade definidos na configuração de participarem de arquivos no cache de dentro do domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3cb35-124">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="3cb35-125">Todas as instâncias de <xref:System.ServiceModel.ClientBase%601> criado por meio de programação dentro desse domínio de aplicativo não participará no cache.</span><span class="sxs-lookup"><span data-stu-id="3cb35-125">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="3cb35-126">Além disso, o cache será desabilitado para uma instância de <xref:System.ServiceModel.ClientBase%601> quando qualquer uma de suas propriedades de "segurança" é acessada.</span><span class="sxs-lookup"><span data-stu-id="3cb35-126">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="3cb35-127">O cache é desativado para todas as instâncias de <xref:System.ServiceModel.ClientBase%601> de um tipo específico dentro do aplicativo-domínio em questão.</span><span class="sxs-lookup"><span data-stu-id="3cb35-127">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|  
  
 <span data-ttu-id="3cb35-128">Os trechos de código a seguir ilustram como usar o <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="3cb35-128">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>  
  
```  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase<ITest>.CacheSettings = CacheSettings.AlwaysOn;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient (new BasicHttpBinding(), new EndpointAddress(address)))   
         {   
            // ...  
            proxy.Test(msg);   
            // ...  
         }   
      }   
   }   
}  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest { }  
```  
  
 <span data-ttu-id="3cb35-129">No código acima, todas as instâncias de `TestClient` usará a mesma fábrica de canais.</span><span class="sxs-lookup"><span data-stu-id="3cb35-129">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>  
  
```  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.Default;   
      int i = 1;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            if (i == 4)   
            {   
               ServiceEndpoint endpoint = proxy.Endpoint;   
               ... // use endpoint in some way   
            }   
            proxy.Test(msg);   
         }   
         i++;   
   }   
}   
  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 <span data-ttu-id="3cb35-130">No exemplo acima, todas as instâncias de `TestClient` seria usar a mesma fábrica de canais exceto instância #4.</span><span class="sxs-lookup"><span data-stu-id="3cb35-130">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="3cb35-131">Instância #4 usaria uma fábrica de canais que é criada especificamente para seu uso.</span><span class="sxs-lookup"><span data-stu-id="3cb35-131">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="3cb35-132">Essa configuração funciona para cenários em que um determinado ponto de extremidade precisa de configurações de segurança diferente de outros pontos de extremidade do mesmo tipo de fábrica de canal (neste caso `ITest`).</span><span class="sxs-lookup"><span data-stu-id="3cb35-132">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>  
  
```  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.AlwaysOff;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            proxy.Test(msg);   
         }           
      }   
   }  
}  
  
// Generated by SvcUtil.exe   
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 <span data-ttu-id="3cb35-133">No exemplo acima, todas as instâncias de `TestClient` usaria fábricas de canais diferentes.</span><span class="sxs-lookup"><span data-stu-id="3cb35-133">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="3cb35-134">Isso é útil quando cada ponto de extremidade tem diferentes requisitos de segurança e não faz sentido para o cache.</span><span class="sxs-lookup"><span data-stu-id="3cb35-134">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb35-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cb35-135">See Also</span></span>  
 <xref:System.ServiceModel.ClientBase%601>  
 <span data-ttu-id="3cb35-136">[Building Clients](../../../../docs/framework/wcf/building-clients.md) (Compilando clientes)</span><span class="sxs-lookup"><span data-stu-id="3cb35-136">[Building Clients](../../../../docs/framework/wcf/building-clients.md)</span></span>  
 [<span data-ttu-id="3cb35-137">Clientes</span><span class="sxs-lookup"><span data-stu-id="3cb35-137">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)  
 <span data-ttu-id="3cb35-138">[Accessing Services Using a WCF Client](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md) (Usando um cliente do WCF para acessar serviços)</span><span class="sxs-lookup"><span data-stu-id="3cb35-138">[Accessing Services Using a WCF Client](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)</span></span>  
 [<span data-ttu-id="3cb35-139">Como: usar o ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="3cb35-139">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
