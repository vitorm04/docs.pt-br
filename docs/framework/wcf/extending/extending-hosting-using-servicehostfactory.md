---
title: Estendendo a hospedagem com ServiceHostFactory
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a7bcd2e0ba68499cad63ec47918fd2bd6bd80d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="aaf4d-102">Estendendo a hospedagem com ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="aaf4d-102">Extending Hosting Using ServiceHostFactory</span></span>
<span data-ttu-id="aaf4d-103">O padrão <xref:System.ServiceModel.ServiceHost> API para hospedar os serviços em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é um ponto de extensibilidade de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] arquitetura.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-103">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is an extensibility point in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] architecture.</span></span> <span data-ttu-id="aaf4d-104">Os usuários podem derivar suas próprias classes de host do <xref:System.ServiceModel.ServiceHost>, geralmente para substituir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> usar <xref:System.ServiceModel.Description.ServiceDescription> para adicionar pontos de extremidade padrão imperativa ou modificar comportamentos, antes de abrir o serviço.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-104">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="aaf4d-105">No ambiente de hospedagem interna, você não precisa criar um personalizado <xref:System.ServiceModel.ServiceHost> porque você escrever o código que instancia o host e, em seguida, chamar <xref:System.ServiceModel.ICommunicationObject.Open> nele após você instanciá-la.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-105">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="aaf4d-106">Entre essas duas etapas, você pode fazer tudo o que você quiser.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-106">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="aaf4d-107">Você pode, por exemplo, adicionar um novo <xref:System.ServiceModel.Description.IServiceBehavior>:</span><span class="sxs-lookup"><span data-stu-id="aaf4d-107">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="aaf4d-108">Essa abordagem não é reutilizável.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-108">This approach is not reusable.</span></span> <span data-ttu-id="aaf4d-109">O código que manipula a descrição é codificado para o host de programa (nesse caso, a função Main ()), portanto, é difícil reutilizar essa lógica em outros contextos.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-109">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="aaf4d-110">Também existem outras maneiras de adicionar um <xref:System.ServiceModel.Description.IServiceBehavior> que não requerem código obrigatório.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-110">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="aaf4d-111">Você pode derivar um atributo de <xref:System.ServiceModel.ServiceBehaviorAttribute> e coloque que em sua implementação de serviço de tipo ou você pode fazer um comportamento personalizado configurável e compor dinamicamente usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-111">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="aaf4d-112">No entanto, uma ligeira variação do exemplo também pode ser usada para resolver esse problema.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-112">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="aaf4d-113">É uma abordagem mover o código que adiciona o ServiceBehavior fora de `Main()` para o <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> método de um personalizado derivado de <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="aaf4d-113">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```  
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
  
 <span data-ttu-id="aaf4d-114">Em seguida, dentro de `Main()` você pode usar:</span><span class="sxs-lookup"><span data-stu-id="aaf4d-114">Then, inside of `Main()` you can use:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="aaf4d-115">Agora você tem encapsuladas a lógica personalizada em uma abstração de limpeza que pode ser facilmente reutilizada em vários executáveis de host diferente.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-115">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="aaf4d-116">Não é imediatamente óbvia como usar esse personalizado <xref:System.ServiceModel.ServiceHost> de dentro de serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="aaf4d-116">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="aaf4d-117">Nesses ambientes são diferentes do ambiente de hospedagem interna, como o ambiente de hospedagem é a instanciação de um a <xref:System.ServiceModel.ServiceHost> em nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-117">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="aaf4d-118">A infraestrutura de hospedagem do IIS e WAS não sabe nada sobre seu personalizado <xref:System.ServiceModel.ServiceHost> derivado.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-118">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="aaf4d-119">O <xref:System.ServiceModel.Activation.ServiceHostFactory> foi projetado para resolver esse problema de acesso personalizados <xref:System.ServiceModel.ServiceHost> de dentro do IIS ou do WAS.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-119">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="aaf4d-120">Porque o host de um personalizado que é derivado de <xref:System.ServiceModel.ServiceHost> é configurado dinamicamente e potencialmente de vários tipos, o ambiente de hospedagem nunca instancia-o diretamente.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-120">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="aaf4d-121">Em vez disso, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa um padrão de fábrica para fornecer uma camada de indireção entre o ambiente de hospedagem e o tipo concreto do serviço.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-121">Instead, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="aaf4d-122">A menos que você informe caso contrário, ele usa uma implementação padrão de <xref:System.ServiceModel.Activation.ServiceHostFactory> que retorna uma instância de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-122">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="aaf4d-123">Mas você também pode fornecer sua própria fábrica que retorna seu host derivada, especificando o nome de tipo CLR da sua implementação de fábrica no @ServiceHost diretiva.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-123">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="aaf4d-124">A intenção é que para casos básicos, implementar sua própria fábrica deve ser um exercício direto.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-124">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="aaf4d-125">Por exemplo, aqui está um personalizado <xref:System.ServiceModel.Activation.ServiceHostFactory> que retorna um derivado <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="aaf4d-125">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="aaf4d-126">Para usar esta fábrica em vez de fábrica padrão, forneça o nome do tipo no @ServiceHost diretiva da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="aaf4d-126">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="aaf4d-127">Embora não haja nenhum limite técnica fazendo o que você deseja o <xref:System.ServiceModel.ServiceHost> retornar de <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, sugerimos que você mantenha suas implementações de fábrica mais simples possível.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-127">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="aaf4d-128">Se você tiver muita lógica personalizada, é melhor colocar essa lógica dentro de host para você, em vez de dentro de fábrica para que ele possa ser reutilizável.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-128">If you have lots of custom logic, it is better to put that logic inside of you host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="aaf4d-129">Há uma camada a mais para a API de hospedagem que deve ser mencionada aqui.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-129">There is one more layer to the hosting API that should be mentioned here.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="aaf4d-130">também tem <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, do qual <xref:System.ServiceModel.ServiceHost> e <xref:System.ServiceModel.Activation.ServiceHostFactory> respectivamente derivar.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-130"> also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="aaf4d-131">Aqueles existem em cenários mais avançados em que você deve alternar grande parte do sistema de metadados com suas próprias criações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="aaf4d-131">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
