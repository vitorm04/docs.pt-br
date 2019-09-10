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
# <a name="extending-hosting-using-servicehostfactory"></a>Estendendo a hospedagem com ServiceHostFactory
A API <xref:System.ServiceModel.ServiceHost> padrão para hospedar serviços no Windows Communication Foundation (WCF) é um ponto de extensibilidade na arquitetura do WCF. Os usuários podem derivar suas próprias classes <xref:System.ServiceModel.ServiceHost>de host do, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> geralmente para <xref:System.ServiceModel.Description.ServiceDescription> substituir para usar para adicionar pontos de extremidade padrão imperativos ou modificar comportamentos, antes de abrir o serviço.  
  
 No ambiente de hospedagem interna, você não precisa criar um personalizado <xref:System.ServiceModel.ServiceHost> porque escreve o código que instancia o host e, em seguida, chama <xref:System.ServiceModel.ICommunicationObject.Open> -o depois de instanciá-lo. Entre essas duas etapas, você pode fazer aquilo que desejar. Você pode, por exemplo, adicionar um novo <xref:System.ServiceModel.Description.IServiceBehavior>:  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 Essa abordagem não é reutilizável. O código que manipula a descrição é codificado no programa de host (nesse caso, a função main ()), portanto, é difícil reutilizar essa lógica em outros contextos. Também há outras maneiras de adicionar um <xref:System.ServiceModel.Description.IServiceBehavior> que não exige código imperativo. Você pode derivar um atributo <xref:System.ServiceModel.ServiceBehaviorAttribute> de e colocá-lo em seu tipo de implementação de serviço ou pode tornar um comportamento personalizado configurável e Compose-lo dinamicamente usando a configuração.  
  
 No entanto, uma pequena variação do exemplo também pode ser usada para resolver esse problema. Uma abordagem é mover o código que adiciona o próprio comportamento de `Main()` e para o <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> método de um derivado personalizado de <xref:System.ServiceModel.ServiceHost>:  
  
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
  
 Em seguida, dentro `Main()` de você pode usar:  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 Agora você encapsula a lógica personalizada em uma abstração limpa que pode ser facilmente reutilizada em vários executáveis de host diferentes.  
  
 Não é imediatamente óbvio como usar esse personalizado <xref:System.ServiceModel.ServiceHost> de dentro do serviços de informações da Internet (IIS) ou do WAS (serviço de ativação de processos do Windows). Esses ambientes são diferentes do ambiente de auto-host, pois o ambiente de hospedagem é o que instancia o <xref:System.ServiceModel.ServiceHost> em nome do aplicativo. A infraestrutura do IIS e do was de hospedagem não sabe nada sobre <xref:System.ServiceModel.ServiceHost> o seu derivado personalizado.  
  
 O <xref:System.ServiceModel.Activation.ServiceHostFactory> foi projetado para resolver esse problema de acesso ao seu <xref:System.ServiceModel.ServiceHost> personalizado de dentro do IIS ou was. Como um host personalizado derivado do <xref:System.ServiceModel.ServiceHost> é configurado dinamicamente e potencialmente de vários tipos, o ambiente de hospedagem nunca o instancia diretamente. Em vez disso, o WCF usa um padrão de fábrica para fornecer uma camada de indireção entre o ambiente de hospedagem e o tipo concreto do serviço. A menos que você diga ao contrário, ele usa uma implementação <xref:System.ServiceModel.Activation.ServiceHostFactory> padrão do que retorna uma <xref:System.ServiceModel.ServiceHost>instância do. Mas você também pode fornecer sua própria fábrica que retorna o host derivado especificando o nome do tipo CLR da sua implementação de fábrica na @ServiceHost diretiva.  
  
 A intenção é que, para os casos básicos, implementar sua própria fábrica deve ser um exercício direto. Por exemplo, aqui está um personalizado <xref:System.ServiceModel.Activation.ServiceHostFactory> que retorna uma derivada <xref:System.ServiceModel.ServiceHost>:  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 Para usar essa fábrica em vez da fábrica padrão, forneça o nome do tipo na @ServiceHost diretiva da seguinte maneira:  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 Embora não haja nenhum limite técnico para <xref:System.ServiceModel.ServiceHost> fazer o que você deseja <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>retornar, sugerimos que você mantenha suas implementações de fábrica o mais simples possível. Se você tiver muita lógica personalizada, é melhor colocar essa lógica dentro do seu host, em vez de dentro da fábrica, para que ela possa ser reutilizável.  
  
 Há mais uma camada para a API de hospedagem que deve ser mencionada aqui. O WCF também <xref:System.ServiceModel.ServiceHostBase> tem <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>e, de <xref:System.ServiceModel.ServiceHost> onde <xref:System.ServiceModel.Activation.ServiceHostFactory> e derivar, respectivamente. Existem para cenários mais avançados em que você deve trocar partes grandes do sistema de metadados por suas próprias criações personalizadas.
