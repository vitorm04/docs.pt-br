---
title: Estendendo a hospedagem com ServiceHostFactory
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: e553fe161ffc5b50850d916cf1cef6b38dd5c1a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991309"
---
# <a name="extending-hosting-using-servicehostfactory"></a>Estendendo a hospedagem com ServiceHostFactory
O padrão <xref:System.ServiceModel.ServiceHost> API para hospedar serviços no Windows Communication Foundation (WCF) é um ponto de extensibilidade na arquitetura do WCF. Os usuários podem derivar suas próprias classes de host do <xref:System.ServiceModel.ServiceHost>, geralmente para substituir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> usar <xref:System.ServiceModel.Description.ServiceDescription> para adicionar pontos de extremidade padrão imperativamente ou modificar comportamentos, antes de abrir o serviço.  
  
 No ambiente de hospedagem interna, você não precisa criar um personalizado <xref:System.ServiceModel.ServiceHost> porque você escrever o código que instancia o host e, em seguida, chamar <xref:System.ServiceModel.ICommunicationObject.Open> nele depois que ela é instanciada. Entre essas duas etapas, você pode fazer tudo o que você deseja. Você pode, por exemplo, adicionar um novo <xref:System.ServiceModel.Description.IServiceBehavior>:  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 Essa abordagem não é reutilizável. O código que manipula a descrição é codificado no host do programa (nesse caso, a função Main ()), portanto, é difícil de ser reutilizada essa lógica em outros contextos. Também há outras maneiras de adicionar um <xref:System.ServiceModel.Description.IServiceBehavior> que não exigem código obrigatório. Você pode derivar um atributo de <xref:System.ServiceModel.ServiceBehaviorAttribute> e coloque que sua implementação de serviço tipo ou você pode fazer um comportamento personalizado configurável e compô-la dinamicamente usando a configuração.  
  
 No entanto, uma ligeira variação do exemplo também pode ser usada para resolver esse problema. Uma abordagem é mover o código que adiciona o ServiceBehavior fora de `Main()` para o <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> método de um personalizado derivado de <xref:System.ServiceModel.ServiceHost>:  
  
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
  
 Agora você tem encapsulado a lógica personalizada em uma abstração limpa que possa ser facilmente reutilizada em muitos arquivos executáveis de host diferente.  
  
 Não é imediatamente óbvio como usar esse custom <xref:System.ServiceModel.ServiceHost> de dentro de serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS). Esses ambientes são diferentes de ambiente de hospedagem interna, como o ambiente de hospedagem é a instanciar um o <xref:System.ServiceModel.ServiceHost> em nome do aplicativo. A infraestrutura de hospedagem IIS e WAS não sabe nada sobre seu personalizado <xref:System.ServiceModel.ServiceHost> derivativo.  
  
 O <xref:System.ServiceModel.Activation.ServiceHostFactory> foi projetado para resolver esse problema de acessar seu personalizado <xref:System.ServiceModel.ServiceHost> de dentro do IIS ou WAS. Como um personalizado de host que é derivada de <xref:System.ServiceModel.ServiceHost> tiver sido configurada dinamicamente e potencialmente de vários tipos, o ambiente de hospedagem nunca instancia diretamente. Em vez disso, o WCF usa um padrão de fábrica para fornecer uma camada de indireção entre o ambiente de hospedagem e o tipo concreto do serviço. A menos que você dizer caso contrário, ele usa uma implementação padrão de <xref:System.ServiceModel.Activation.ServiceHostFactory> que retorna uma instância de <xref:System.ServiceModel.ServiceHost>. Mas você também pode fornecer sua própria fábrica que retorna o seu host derivada especificando o nome do tipo CLR da sua implementação de fábrica no @ServiceHost diretiva.  
  
 A intenção é que para casos básicos, implementar sua própria fábrica deve ser um exercício direto. Por exemplo, aqui está um personalizado <xref:System.ServiceModel.Activation.ServiceHostFactory> que retorna um derivada <xref:System.ServiceModel.ServiceHost>:  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 Para usar esta fábrica, em vez do alocador padrão, forneça o nome do tipo no @ServiceHost diretiva da seguinte maneira:  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Embora não haja nenhum limite técnico sobre como fazer o que você deseja a <xref:System.ServiceModel.ServiceHost> retornar de <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, sugerimos que você mantenha suas implementações de fábrica tão simples quanto possível. Se você tiver muita lógica personalizada, é melhor colocar essa lógica dentro do host para você, em vez de dentro de fábrica para que ele possa ser reutilizável.  
  
 Não há mais de uma camada para a API de hospedagem deve ser mencionada aqui. O WCF também possui <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, do qual <xref:System.ServiceModel.ServiceHost> e <xref:System.ServiceModel.Activation.ServiceHostFactory> derivam, respectivamente. Eles existirem para cenários mais avançados em que você deve alternar grandes partes do sistema metadados com suas próprias criações personalizadas.
