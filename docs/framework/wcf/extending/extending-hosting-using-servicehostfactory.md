---
title: Estendendo a hospedagem com ServiceHostFactory
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: e553fe161ffc5b50850d916cf1cef6b38dd5c1a9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="extending-hosting-using-servicehostfactory"></a>Estendendo a hospedagem com ServiceHostFactory
O padrão <xref:System.ServiceModel.ServiceHost> API para hospedar os serviços no Windows Communication Foundation (WCF) é um ponto de extensibilidade da arquitetura do WCF. Os usuários podem derivar suas próprias classes de host do <xref:System.ServiceModel.ServiceHost>, geralmente para substituir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> usar <xref:System.ServiceModel.Description.ServiceDescription> para adicionar pontos de extremidade padrão imperativa ou modificar comportamentos, antes de abrir o serviço.  
  
 No ambiente de hospedagem interna, você não precisa criar um personalizado <xref:System.ServiceModel.ServiceHost> porque você escrever o código que instancia o host e, em seguida, chamar <xref:System.ServiceModel.ICommunicationObject.Open> nele após você instanciá-la. Entre essas duas etapas, você pode fazer tudo o que você quiser. Você pode, por exemplo, adicionar um novo <xref:System.ServiceModel.Description.IServiceBehavior>:  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 Essa abordagem não é reutilizável. O código que manipula a descrição é codificado para o host de programa (nesse caso, a função Main ()), portanto, é difícil reutilizar essa lógica em outros contextos. Também existem outras maneiras de adicionar um <xref:System.ServiceModel.Description.IServiceBehavior> que não requerem código obrigatório. Você pode derivar um atributo de <xref:System.ServiceModel.ServiceBehaviorAttribute> e coloque que em sua implementação de serviço de tipo ou você pode fazer um comportamento personalizado configurável e compor dinamicamente usando a configuração.  
  
 No entanto, uma ligeira variação do exemplo também pode ser usada para resolver esse problema. É uma abordagem mover o código que adiciona o ServiceBehavior fora de `Main()` para o <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> método de um personalizado derivado de <xref:System.ServiceModel.ServiceHost>:  
  
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
  
 Em seguida, dentro de `Main()` você pode usar:  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 Agora você tem encapsuladas a lógica personalizada em uma abstração de limpeza que pode ser facilmente reutilizada em vários executáveis de host diferente.  
  
 Não é imediatamente óbvia como usar esse personalizado <xref:System.ServiceModel.ServiceHost> de dentro de serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS). Nesses ambientes são diferentes do ambiente de hospedagem interna, como o ambiente de hospedagem é a instanciação de um a <xref:System.ServiceModel.ServiceHost> em nome do aplicativo. A infraestrutura de hospedagem do IIS e WAS não sabe nada sobre seu personalizado <xref:System.ServiceModel.ServiceHost> derivado.  
  
 O <xref:System.ServiceModel.Activation.ServiceHostFactory> foi projetado para resolver esse problema de acesso personalizados <xref:System.ServiceModel.ServiceHost> de dentro do IIS ou do WAS. Porque o host de um personalizado que é derivado de <xref:System.ServiceModel.ServiceHost> é configurado dinamicamente e potencialmente de vários tipos, o ambiente de hospedagem nunca instancia-o diretamente. Em vez disso, o WCF usa um padrão de fábrica para fornecer uma camada de indireção entre o ambiente de hospedagem e o tipo concreto do serviço. A menos que você informe caso contrário, ele usa uma implementação padrão de <xref:System.ServiceModel.Activation.ServiceHostFactory> que retorna uma instância de <xref:System.ServiceModel.ServiceHost>. Mas você também pode fornecer sua própria fábrica que retorna seu host derivada, especificando o nome de tipo CLR da sua implementação de fábrica no @ServiceHost diretiva.  
  
 A intenção é que para casos básicos, implementar sua própria fábrica deve ser um exercício direto. Por exemplo, aqui está um personalizado <xref:System.ServiceModel.Activation.ServiceHostFactory> que retorna um derivado <xref:System.ServiceModel.ServiceHost>:  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 Para usar esta fábrica em vez de fábrica padrão, forneça o nome do tipo no @ServiceHost diretiva da seguinte maneira:  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Embora não haja nenhum limite técnica fazendo o que você deseja o <xref:System.ServiceModel.ServiceHost> retornar de <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, sugerimos que você mantenha suas implementações de fábrica mais simples possível. Se você tiver muita lógica personalizada, é melhor colocar essa lógica dentro de host para você, em vez de dentro de fábrica para que ele possa ser reutilizável.  
  
 Há uma camada a mais para a API de hospedagem que deve ser mencionada aqui. O WCF também possui <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, do qual <xref:System.ServiceModel.ServiceHost> e <xref:System.ServiceModel.Activation.ServiceHostFactory> respectivamente derivar. Aqueles existem em cenários mais avançados em que você deve alternar grande parte do sistema de metadados com suas próprias criações personalizadas.
