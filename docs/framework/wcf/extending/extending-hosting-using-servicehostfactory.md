---
title: Estendendo a hospedagem com ServiceHostFactory
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: de6a590b94285872dd77006eda7f86d5d629be9d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849909"
---
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="88f5b-102">Estendendo a hospedagem com ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="88f5b-102">Extending Hosting Using ServiceHostFactory</span></span>
<span data-ttu-id="88f5b-103">A API <xref:System.ServiceModel.ServiceHost> padrão para hospedar serviços no Windows Communication Foundation (WCF) é um ponto de extensibilidade na arquitetura do WCF.</span><span class="sxs-lookup"><span data-stu-id="88f5b-103">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in Windows Communication Foundation (WCF) is an extensibility point in the WCF architecture.</span></span> <span data-ttu-id="88f5b-104">Os usuários podem derivar suas próprias classes <xref:System.ServiceModel.ServiceHost>de host do, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> geralmente para <xref:System.ServiceModel.Description.ServiceDescription> substituir para usar para adicionar pontos de extremidade padrão imperativos ou modificar comportamentos, antes de abrir o serviço.</span><span class="sxs-lookup"><span data-stu-id="88f5b-104">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="88f5b-105">No ambiente de hospedagem interna, você não precisa criar um personalizado <xref:System.ServiceModel.ServiceHost> porque escreve o código que instancia o host e, em seguida, chama <xref:System.ServiceModel.ICommunicationObject.Open> -o depois de instanciá-lo.</span><span class="sxs-lookup"><span data-stu-id="88f5b-105">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="88f5b-106">Entre essas duas etapas, você pode fazer aquilo que desejar.</span><span class="sxs-lookup"><span data-stu-id="88f5b-106">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="88f5b-107">Você pode, por exemplo, adicionar um novo <xref:System.ServiceModel.Description.IServiceBehavior>:</span><span class="sxs-lookup"><span data-stu-id="88f5b-107">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="88f5b-108">Essa abordagem não é reutilizável.</span><span class="sxs-lookup"><span data-stu-id="88f5b-108">This approach is not reusable.</span></span> <span data-ttu-id="88f5b-109">O código que manipula a descrição é codificado no programa de host (nesse caso, a função main ()), portanto, é difícil reutilizar essa lógica em outros contextos.</span><span class="sxs-lookup"><span data-stu-id="88f5b-109">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="88f5b-110">Também há outras maneiras de adicionar um <xref:System.ServiceModel.Description.IServiceBehavior> que não exige código imperativo.</span><span class="sxs-lookup"><span data-stu-id="88f5b-110">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="88f5b-111">Você pode derivar um atributo <xref:System.ServiceModel.ServiceBehaviorAttribute> de e colocá-lo em seu tipo de implementação de serviço ou pode tornar um comportamento personalizado configurável e Compose-lo dinamicamente usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="88f5b-111">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="88f5b-112">No entanto, uma pequena variação do exemplo também pode ser usada para resolver esse problema.</span><span class="sxs-lookup"><span data-stu-id="88f5b-112">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="88f5b-113">Uma abordagem é mover o código que adiciona o próprio comportamento de `Main()` e para o <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> método de um derivado personalizado de <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="88f5b-113">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```csharp
public class DerivedHost : ServiceHost  
{  
   public DerivedHost( Type t, params Uri baseAddresses ) :  
      base( t, baseAddresses ) {}  
  
   public override void OnOpening()  
   {  
  this.Description.Add( new MyServiceBehavior() );  
   }  
}  
```  
  
 <span data-ttu-id="88f5b-114">Em seguida, dentro `Main()` de você pode usar:</span><span class="sxs-lookup"><span data-stu-id="88f5b-114">Then, inside of `Main()` you can use:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="88f5b-115">Agora você encapsula a lógica personalizada em uma abstração limpa que pode ser facilmente reutilizada em vários executáveis de host diferentes.</span><span class="sxs-lookup"><span data-stu-id="88f5b-115">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="88f5b-116">Não é imediatamente óbvio como usar esse personalizado <xref:System.ServiceModel.ServiceHost> de dentro do serviços de informações da Internet (IIS) ou do WAS (serviço de ativação de processos do Windows).</span><span class="sxs-lookup"><span data-stu-id="88f5b-116">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="88f5b-117">Esses ambientes são diferentes do ambiente de auto-host, pois o ambiente de hospedagem é o que instancia o <xref:System.ServiceModel.ServiceHost> em nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88f5b-117">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="88f5b-118">A infraestrutura do IIS e do was de hospedagem não sabe nada sobre <xref:System.ServiceModel.ServiceHost> o seu derivado personalizado.</span><span class="sxs-lookup"><span data-stu-id="88f5b-118">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="88f5b-119">O <xref:System.ServiceModel.Activation.ServiceHostFactory> foi projetado para resolver esse problema de acesso ao seu <xref:System.ServiceModel.ServiceHost> personalizado de dentro do IIS ou was.</span><span class="sxs-lookup"><span data-stu-id="88f5b-119">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="88f5b-120">Como um host personalizado derivado do <xref:System.ServiceModel.ServiceHost> é configurado dinamicamente e potencialmente de vários tipos, o ambiente de hospedagem nunca o instancia diretamente.</span><span class="sxs-lookup"><span data-stu-id="88f5b-120">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="88f5b-121">Em vez disso, o WCF usa um padrão de fábrica para fornecer uma camada de indireção entre o ambiente de hospedagem e o tipo concreto do serviço.</span><span class="sxs-lookup"><span data-stu-id="88f5b-121">Instead, WCF uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="88f5b-122">A menos que você diga ao contrário, ele usa uma implementação <xref:System.ServiceModel.Activation.ServiceHostFactory> padrão do que retorna uma <xref:System.ServiceModel.ServiceHost>instância do.</span><span class="sxs-lookup"><span data-stu-id="88f5b-122">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="88f5b-123">Mas você também pode fornecer sua própria fábrica que retorna o host derivado especificando o nome do tipo CLR da sua implementação de fábrica na @ServiceHost diretiva.</span><span class="sxs-lookup"><span data-stu-id="88f5b-123">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="88f5b-124">A intenção é que, para os casos básicos, implementar sua própria fábrica deve ser um exercício direto.</span><span class="sxs-lookup"><span data-stu-id="88f5b-124">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="88f5b-125">Por exemplo, aqui está um personalizado <xref:System.ServiceModel.Activation.ServiceHostFactory> que retorna uma derivada <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="88f5b-125">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="88f5b-126">Para usar essa fábrica em vez da fábrica padrão, forneça o nome do tipo na @ServiceHost diretiva da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="88f5b-126">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 <span data-ttu-id="88f5b-127">Embora não haja nenhum limite técnico para <xref:System.ServiceModel.ServiceHost> fazer o que você deseja <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>retornar, sugerimos que você mantenha suas implementações de fábrica o mais simples possível.</span><span class="sxs-lookup"><span data-stu-id="88f5b-127">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="88f5b-128">Se você tiver muita lógica personalizada, é melhor colocar essa lógica dentro do seu host, em vez de dentro da fábrica, para que ela possa ser reutilizável.</span><span class="sxs-lookup"><span data-stu-id="88f5b-128">If you have lots of custom logic, it is better to put that logic inside of your host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="88f5b-129">Há mais uma camada para a API de hospedagem que deve ser mencionada aqui.</span><span class="sxs-lookup"><span data-stu-id="88f5b-129">There is one more layer to the hosting API that should be mentioned here.</span></span> <span data-ttu-id="88f5b-130">O WCF também <xref:System.ServiceModel.ServiceHostBase> tem <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>e, de <xref:System.ServiceModel.ServiceHost> onde <xref:System.ServiceModel.Activation.ServiceHostFactory> e derivar, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="88f5b-130">WCF also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="88f5b-131">Existem para cenários mais avançados em que você deve trocar partes grandes do sistema de metadados por suas próprias criações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="88f5b-131">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
