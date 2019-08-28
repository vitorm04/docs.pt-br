---
title: Cache e fábrica de canal
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 98b77071204e2c2f98609e6c5bb1ca84a896dd58
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040210"
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="a624d-102">Cache e fábrica de canal</span><span class="sxs-lookup"><span data-stu-id="a624d-102">Channel Factory and Caching</span></span>

<span data-ttu-id="a624d-103">Os aplicativos cliente do WCF usam a classe <xref:System.ServiceModel.ChannelFactory%601> para criar um canal de comunicação com um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="a624d-103">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="a624d-104">Criar instâncias de <xref:System.ServiceModel.ChannelFactory%601> resulta em alguma sobrecarga porque envolve as seguintes operações:</span><span class="sxs-lookup"><span data-stu-id="a624d-104">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>

- <span data-ttu-id="a624d-105">Construir a árvore de <xref:System.ServiceModel.Description.ContractDescription></span><span class="sxs-lookup"><span data-stu-id="a624d-105">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>

- <span data-ttu-id="a624d-106">Refletir todos os tipos CLR necessários</span><span class="sxs-lookup"><span data-stu-id="a624d-106">Reflecting all of the required CLR types</span></span>

- <span data-ttu-id="a624d-107">Construir a pilha de canal</span><span class="sxs-lookup"><span data-stu-id="a624d-107">Constructing the channel stack</span></span>

- <span data-ttu-id="a624d-108">Descarte de recursos</span><span class="sxs-lookup"><span data-stu-id="a624d-108">Disposing of resources</span></span>

<span data-ttu-id="a624d-109">Para ajudar a minimizar a sobrecarga, o WCF pode armazenar em cache fábricas de canal quando você está usando um proxy de cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="a624d-109">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>

> [!TIP]
> <span data-ttu-id="a624d-110">Você tem controle direto sobre a criação de fábrica de canal quando <xref:System.ServiceModel.ChannelFactory%601> usa a classe diretamente.</span><span class="sxs-lookup"><span data-stu-id="a624d-110">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>

<span data-ttu-id="a624d-111">Os proxies de cliente do WCF gerados com a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) são derivados de <xref:System.ServiceModel.ClientBase%601>.</span><span class="sxs-lookup"><span data-stu-id="a624d-111">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="a624d-112"><xref:System.ServiceModel.ClientBase%601>define uma propriedade <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> estática que define o comportamento de cache da fábrica de canais.</span><span class="sxs-lookup"><span data-stu-id="a624d-112"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="a624d-113">As configurações de cache são feitas para um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="a624d-113">Cache settings are made for a specific type.</span></span> <span data-ttu-id="a624d-114">Por exemplo, a `ClientBase<ITest>.CacheSettings` configuração para um dos valores definidos abaixo afetará somente o proxy/ClientBase do tipo `ITest`.</span><span class="sxs-lookup"><span data-stu-id="a624d-114">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="a624d-115">A configuração de cache para um <xref:System.ServiceModel.ClientBase%601> específico é imutável assim que a primeira instância de proxy/ClientBase é criada.</span><span class="sxs-lookup"><span data-stu-id="a624d-115">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>

## <a name="specifying-caching-behavior"></a><span data-ttu-id="a624d-116">Especificando o comportamento de cache</span><span class="sxs-lookup"><span data-stu-id="a624d-116">Specifying Caching Behavior</span></span>

<span data-ttu-id="a624d-117">O comportamento de caching é especificado definindo <xref:System.ServiceModel.ClientBase%601.CacheSetting> a propriedade como um dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="a624d-117">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>

|<span data-ttu-id="a624d-118">Valor de configuração de cache</span><span class="sxs-lookup"><span data-stu-id="a624d-118">Cache Setting Value</span></span>|<span data-ttu-id="a624d-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="a624d-119">Description</span></span>|
|-------------------------|-----------------|
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="a624d-120">Todas as instâncias <xref:System.ServiceModel.ClientBase%601> de dentro do aplicativo-domínio podem participar do Caching.</span><span class="sxs-lookup"><span data-stu-id="a624d-120">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="a624d-121">O desenvolvedor determinou que não há nenhuma implicação de segurança negativa no cache.</span><span class="sxs-lookup"><span data-stu-id="a624d-121">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="a624d-122">O cache não será desativado mesmo que as propriedades "sensíveis à <xref:System.ServiceModel.ClientBase%601> segurança" sejam acessadas.</span><span class="sxs-lookup"><span data-stu-id="a624d-122">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="a624d-123">As propriedades "sensíveis à segurança" do <xref:System.ServiceModel.ClientBase%601> são <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> e <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span><span class="sxs-lookup"><span data-stu-id="a624d-123">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="a624d-124">Somente instâncias de <xref:System.ServiceModel.ClientBase%601> criadas a partir de pontos de extremidade definidos em arquivos de configuração participam do cache dentro do domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a624d-124">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="a624d-125">Qualquer instância do <xref:System.ServiceModel.ClientBase%601> criada programaticamente nesse aplicativo-domínio não participará do cache.</span><span class="sxs-lookup"><span data-stu-id="a624d-125">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="a624d-126">Além disso, o Caching será desabilitado para uma <xref:System.ServiceModel.ClientBase%601> instância do uma vez que qualquer uma de suas propriedades "sensíveis à segurança" for acessada.</span><span class="sxs-lookup"><span data-stu-id="a624d-126">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="a624d-127">O Caching é desativado para todas as instâncias <xref:System.ServiceModel.ClientBase%601> de um tipo específico dentro do aplicativo-domínio em questão.</span><span class="sxs-lookup"><span data-stu-id="a624d-127">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|

<span data-ttu-id="a624d-128">Os trechos de código a seguir ilustram como <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> usar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="a624d-128">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>

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

<span data-ttu-id="a624d-129">No código acima, todas as instâncias do `TestClient` usarão a mesma fábrica de canais.</span><span class="sxs-lookup"><span data-stu-id="a624d-129">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>

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

<span data-ttu-id="a624d-130">No exemplo acima, todas as instâncias de `TestClient` usariam a mesma fábrica de canais, exceto #4 de instância.</span><span class="sxs-lookup"><span data-stu-id="a624d-130">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="a624d-131">A instância #4 usaria uma fábrica de canais criada especificamente para seu uso.</span><span class="sxs-lookup"><span data-stu-id="a624d-131">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="a624d-132">Essa configuração funcionaria para cenários em que um ponto de extremidade específico precisa de configurações de segurança diferentes dos outros pontos de extremidade do mesmo tipo de fábrica de `ITest`canal (nesse caso).</span><span class="sxs-lookup"><span data-stu-id="a624d-132">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>

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

<span data-ttu-id="a624d-133">No exemplo acima, todas as instâncias de `TestClient` usariam fábricas de canal diferentes.</span><span class="sxs-lookup"><span data-stu-id="a624d-133">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="a624d-134">Isso é útil quando cada ponto de extremidade tem requisitos de segurança diferentes e não faz sentido armazenar em cache.</span><span class="sxs-lookup"><span data-stu-id="a624d-134">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="a624d-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a624d-135">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="a624d-136">Compilando clientes</span><span class="sxs-lookup"><span data-stu-id="a624d-136">Building Clients</span></span>](../../../../docs/framework/wcf/building-clients.md)
- [<span data-ttu-id="a624d-137">Clientes</span><span class="sxs-lookup"><span data-stu-id="a624d-137">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)
- [<span data-ttu-id="a624d-138">Usando um cliente do WCF para acessar serviços</span><span class="sxs-lookup"><span data-stu-id="a624d-138">Accessing Services Using a WCF Client</span></span>](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="a624d-139">Como: Usar a ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="a624d-139">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
