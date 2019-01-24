---
title: Cache e fábrica de canal
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 055c9d1412338bb444ca33556f3c94b1ffc4c6a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745315"
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="62cbd-102">Cache e fábrica de canal</span><span class="sxs-lookup"><span data-stu-id="62cbd-102">Channel Factory and Caching</span></span>
<span data-ttu-id="62cbd-103">Os aplicativos cliente do WCF usam a classe <xref:System.ServiceModel.ChannelFactory%601> para criar um canal de comunicação com um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="62cbd-103">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="62cbd-104">Criar instâncias de <xref:System.ServiceModel.ChannelFactory%601> resulta em alguma sobrecarga porque envolve as seguintes operações:</span><span class="sxs-lookup"><span data-stu-id="62cbd-104">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>  
  
-   <span data-ttu-id="62cbd-105">Construir a árvore de <xref:System.ServiceModel.Description.ContractDescription></span><span class="sxs-lookup"><span data-stu-id="62cbd-105">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>  
  
-   <span data-ttu-id="62cbd-106">Refletir todos os tipos CLR necessários</span><span class="sxs-lookup"><span data-stu-id="62cbd-106">Reflecting all of the required CLR types</span></span>  
  
-   <span data-ttu-id="62cbd-107">Construir a pilha de canal</span><span class="sxs-lookup"><span data-stu-id="62cbd-107">Constructing the channel stack</span></span>  
  
-   <span data-ttu-id="62cbd-108">Descarte de recursos</span><span class="sxs-lookup"><span data-stu-id="62cbd-108">Disposing of resources</span></span>  
  
 <span data-ttu-id="62cbd-109">Para ajudar a minimizar a sobrecarga, o WCF pode armazenar em cache fábricas de canal quando você está usando um proxy de cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="62cbd-109">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="62cbd-110">Você tem controle direto sobre criação de fábrica de canal quando você usa o <xref:System.ServiceModel.ChannelFactory%601> classe diretamente.</span><span class="sxs-lookup"><span data-stu-id="62cbd-110">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>  
  
 <span data-ttu-id="62cbd-111">Os proxies de cliente WCF gerados com [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) derivados <xref:System.ServiceModel.ClientBase%601>.</span><span class="sxs-lookup"><span data-stu-id="62cbd-111">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="62cbd-112"><xref:System.ServiceModel.ClientBase%601> define um estático <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> propriedade que define o comportamento de cache de fábrica de canal.</span><span class="sxs-lookup"><span data-stu-id="62cbd-112"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="62cbd-113">Configurações de cache são feitas para um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="62cbd-113">Cache settings are made for a specific type.</span></span> <span data-ttu-id="62cbd-114">Por exemplo, definindo `ClientBase<ITest>.CacheSettings` a um dos valores definidos abaixo afetará apenas essas proxy/ClientBase do tipo `ITest`.</span><span class="sxs-lookup"><span data-stu-id="62cbd-114">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="62cbd-115">A configuração de cache para um determinado <xref:System.ServiceModel.ClientBase%601> é imutável, assim que a primeira instância de proxy/ClientBase é criada.</span><span class="sxs-lookup"><span data-stu-id="62cbd-115">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>  
  
## <a name="specifying-caching-behavior"></a><span data-ttu-id="62cbd-116">Especificando o comportamento de cache</span><span class="sxs-lookup"><span data-stu-id="62cbd-116">Specifying Caching Behavior</span></span>  
 <span data-ttu-id="62cbd-117">Comportamento de cache é especificado pela configuração de <xref:System.ServiceModel.ClientBase%601.CacheSetting> propriedade para um dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="62cbd-117">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>  
  
|<span data-ttu-id="62cbd-118">Valor de configuração de cache</span><span class="sxs-lookup"><span data-stu-id="62cbd-118">Cache Setting Value</span></span>|<span data-ttu-id="62cbd-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="62cbd-119">Description</span></span>|  
|-------------------------|-----------------|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="62cbd-120">Todas as instâncias de <xref:System.ServiceModel.ClientBase%601> dentro do domínio de aplicativo podem participar em cache.</span><span class="sxs-lookup"><span data-stu-id="62cbd-120">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="62cbd-121">O desenvolvedor determinou que não há nenhum implicações de segurança adversos para armazenamento em cache.</span><span class="sxs-lookup"><span data-stu-id="62cbd-121">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="62cbd-122">Armazenamento em cache será não ser desativado propriedades mesmo se "sensível à segurança" no <xref:System.ServiceModel.ClientBase%601> são acessados.</span><span class="sxs-lookup"><span data-stu-id="62cbd-122">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="62cbd-123">As propriedades de "segurança" de <xref:System.ServiceModel.ClientBase%601> estão <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> e <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span><span class="sxs-lookup"><span data-stu-id="62cbd-123">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="62cbd-124">Somente instâncias de <xref:System.ServiceModel.ClientBase%601> criado a partir de pontos de extremidade definidos na configuração de participarem de arquivos em cache dentro do domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="62cbd-124">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="62cbd-125">Todas as instâncias do <xref:System.ServiceModel.ClientBase%601> criado por meio de programação dentro desse domínio de aplicativo não participará de cache.</span><span class="sxs-lookup"><span data-stu-id="62cbd-125">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="62cbd-126">Além disso, o cache será desabilitado para uma instância do <xref:System.ServiceModel.ClientBase%601> depois de qualquer uma de suas propriedades de "segurança" é acessada.</span><span class="sxs-lookup"><span data-stu-id="62cbd-126">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="62cbd-127">Armazenamento em cache é desativado para todas as instâncias de <xref:System.ServiceModel.ClientBase%601> de um tipo específico dentro do aplicativo-domínio em questão.</span><span class="sxs-lookup"><span data-stu-id="62cbd-127">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|  
  
 <span data-ttu-id="62cbd-128">Os trechos de código a seguir ilustram como usar o <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="62cbd-128">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="62cbd-129">No código acima, todas as instâncias de `TestClient` usará a mesma fábrica de canais.</span><span class="sxs-lookup"><span data-stu-id="62cbd-129">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="62cbd-130">No exemplo acima, todas as instâncias de `TestClient` usaria a mesma fábrica de canais, exceto instância #4.</span><span class="sxs-lookup"><span data-stu-id="62cbd-130">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="62cbd-131">Instância #4 usaria uma fábrica de canais que é criada especificamente para seu uso.</span><span class="sxs-lookup"><span data-stu-id="62cbd-131">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="62cbd-132">Essa configuração funciona para cenários em que um ponto de extremidade específico precisa diferentes configurações de segurança de outros pontos de extremidade do mesmo tipo de fábrica de canal (nesse caso, `ITest`).</span><span class="sxs-lookup"><span data-stu-id="62cbd-132">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="62cbd-133">No exemplo acima, todas as instâncias de `TestClient` usaria fábricas de canais diferentes.</span><span class="sxs-lookup"><span data-stu-id="62cbd-133">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="62cbd-134">Isso é útil quando cada ponto de extremidade tem diferentes requisitos de segurança e não faz sentido para o cache.</span><span class="sxs-lookup"><span data-stu-id="62cbd-134">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62cbd-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62cbd-135">See also</span></span>
- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="62cbd-136">Compilando clientes</span><span class="sxs-lookup"><span data-stu-id="62cbd-136">Building Clients</span></span>](../../../../docs/framework/wcf/building-clients.md)
- [<span data-ttu-id="62cbd-137">Clientes</span><span class="sxs-lookup"><span data-stu-id="62cbd-137">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)
- [<span data-ttu-id="62cbd-138">Usando um cliente do WCF para acessar serviços</span><span class="sxs-lookup"><span data-stu-id="62cbd-138">Accessing Services Using a WCF Client</span></span>](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="62cbd-139">Como: Usar o ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="62cbd-139">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
