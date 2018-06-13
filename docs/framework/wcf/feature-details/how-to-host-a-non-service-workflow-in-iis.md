---
title: Como hospedar um fluxo de trabalho sem serviço no IIS
ms.date: 03/30/2017
ms.assetid: f362562c-767d-401b-8257-916616568fd4
ms.openlocfilehash: 70fd6aca94f2addd7ee568e897171ae1da86db67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496740"
---
# <a name="how-to-host-a-non-service-workflow-in-iis"></a>Como hospedar um fluxo de trabalho sem serviço no IIS
Fluxos de trabalho que não são serviços de fluxo de trabalho podem ser hospedados em IIS / WAS. Isso é útil quando você precisa hospedar um fluxo de trabalho gravado por outra pessoa. Por exemplo, se o novo host do designer de fluxo de trabalho e permitir que os usuários criem seus próprios fluxos de trabalho.  Hospedando fluxos de trabalho sem serviço no IIS fornece suporte para recursos como o desligamento ocioso, reciclagem de processo, o monitoramento de integridade do processo e a ativação baseada em mensagem. Serviços de fluxo de trabalho hospedados no IIS contêm <xref:System.ServiceModel.Activities.Receive> atividades e o são ativados quando uma mensagem é recebida pelo IIS. Fluxos de trabalho não não contêm atividades de mensagem e por padrão, não não possível ativar enviando uma mensagem.  Você deve derivar uma classe de <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> e definir um contrato de serviço que contém operações para criar uma instância do fluxo de trabalho. Este tópico o orientará na criação de um fluxo de trabalho simple, definir um contrato de serviço que um cliente pode usar para ativar o fluxo de trabalho e derivar uma classe de <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> que usa o contrato de serviço para escutar as solicitações de criação de fluxo de trabalho.  
  
### <a name="create-a-simple-workflow"></a>Criar um fluxo de trabalho simple  
  
1.  Criar um novo [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] vazio solução chamada `CreationEndpointTest`.  
  
2.  Adicionar um novo projeto de aplicativo de serviço de fluxo de trabalho WCF chamado `SimpleWorkflow` à solução. O designer de fluxo de trabalho será aberta.  
  
3.  Exclua as atividades ReceiveRequest e SendResponse. Essas atividades são o que torna a um fluxo de trabalho como um serviço de fluxo de trabalho. Como não estamos trabalhando com um serviço de fluxo de trabalho, não precisamos delas.  
  
4.  Defina o DisplayName da atividade de sequência para "Fluxo de trabalho sequencial".  
  
5.  Renomeie Service1.xamlx para Workflow1.xamlx.  
  
6.  O designer fora da atividade de sequência e definir as propriedades Name e ConfigurationName para "Workflow1"  
  
7.  Arraste um <xref:System.Activities.Statements.WriteLine> atividade de <xref:System.Activities.Statements.Sequence>. O <xref:System.Activities.Statements.WriteLine> atividade pode ser encontrada no **primitivos** seção da caixa de ferramentas. Definir o <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade o <xref:System.Activities.Statements.WriteLine> atividade para "Olá, mundo".  
  
     O fluxo de trabalho agora deve se parecer com o diagrama a seguir.  
  
     ![Um fluxo de trabalho simple](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "fluxo de trabalho simples")  
  
### <a name="create-the-workflow-creation-service-contract"></a>Criar o contrato de serviço de criação do fluxo de trabalho  
  
1.  Adicionar um novo projeto de biblioteca de classe chamado `Shared` para o `CreationEndpointTest` solução.  
  
2.  Adicione uma referência a System.ServiceModel.dll, System. Configuration e System.ServiceModel.Activities para o `Shared` projeto.  
  
3.  Renomeie o arquivo Class1.cs para IWorkflowCreation.cs e o código a seguir para o arquivo.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
  
    namespace Shared  
    {  
        //service contract exposed from the endpoint  
        [ServiceContract(Name = "IWorkflowCreation")]  
        public interface IWorkflowCreation  
        {  
            [OperationContract(Name = "Create")]  
            Guid Create(IDictionary<string, object> inputs);  
  
            [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
            void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
        }  
    }  
    ```  
  
     Esse contrato define duas operações que ambos criam uma nova instância do fluxo de trabalho sem serviço recém-criado. Um cria uma nova instância com uma ID de instância gerado e o outro permite que você especifique a ID de instância para a nova instância de fluxo de trabalho.  Ambos os métodos permitem que você passar parâmetros para a nova instância de fluxo de trabalho. Este contrato será exposto pelo <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> para permitir que os clientes criar novas instâncias de fluxo de trabalho sem serviço.  
  
### <a name="derive-a-class-from-workflowhostingendpoint"></a>Derive uma classe de WorkflowHostingEndpoint  
  
1.  Adicionar uma nova classe chamada `CreationEndpoint` derivado <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> para o `Shared` projeto.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Globalization;  
    using System.ServiceModel;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Channels;  
  
    namespace Shared  
    {  
        public class CreationEndpoint : WorkflowHostingEndpoint  
        {  
        }  
    }  
    ```  
  
2.  Adicionar um local estático <xref:System.Uri> variável chamada `defaultBaseUri` para o `CreationEndpoint` classe.  
  
    ```  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
    }  
    ```  
  
3.  Adicione o seguinte construtor para o `CreationEndpoint` classe. Observe que especificamos o `IWorkflowCreation` contrato de serviço na chamada para o construtor base.  
  
    ```  
    public CreationEndpoint(Binding binding, EndpointAddress address)  
       : base(typeof(IWorkflowCreation), binding, address)  
       {  
       }  
    ```  
  
4.  Adicione o seguinte construtor padrão para o `CreationEndpoint` classe.  
  
    ```  
    public CreationEndpoint()  
       : this(GetDefaultBinding(),  
       new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative))))  
       {  
       }  
    ```  
  
5.  Adicionar um estático `DefaultBaseUri` propriedade para o `CreationEndpoint` classe. Essa propriedade será usada para manter um padrão URI de base se não for fornecido.  
  
    ```  
    static Uri DefaultBaseUri  
    {  
       get  
       {  
          if (defaultBaseUri == null)  
          {  
             defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                Process.GetCurrentProcess().Id,  
                AppDomain.CurrentDomain.Id));  
          }  
          return defaultBaseUri;  
       }  
     }  
    ```  
  
6.  Crie o seguinte método para obter a associação padrão a ser usado para o ponto de extremidade de criação.  
  
    ```  
    //defaults to NetNamedPipeBinding  
    public static Binding GetDefaultBinding()  
    {  
       return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
    }  
    ```  
  
7.  Substituir o <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> método para retornar a ID de instância de fluxo de trabalho. Se o `Action` cabeçalho termina com "Criar" retorna um GUID vazio, se o `Action` cabeçalho termina com o GUID é passado para o método de retorno de "CreateWithInstanceId". Caso contrário, gerar um <xref:System.InvalidOperationException>. Essas `Action` cabeçalhos correspondem às duas operações definidas no `IWorkflowCreation` contrato de serviço.  
  
    ```  
    protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
    {  
       //Create was called by client  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
       {  
          return Guid.Empty;  
       }  
       //CreateWithInstanceId was called by client  
       else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
       {  
          return (Guid)inputs[1];  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
    }  
    ```  
  
8.  Substituir o <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> método para criar um <xref:System.ServiceModel.Activities.WorkflowCreationContext> e adicionar argumentos para o fluxo de trabalho, enviar a ID de instância para o cliente e, em seguida, retornar o <xref:System.ServiceModel.Activities.WorkflowCreationContext>.  
  
    ```  
    protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
    {  
       WorkflowCreationContext creationContext = new WorkflowCreationContext();  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create") || (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId")))  
       {  
          Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
          if (arguments != null && arguments.Count > 0)  
          {  
             foreach (KeyValuePair<string, object> pair in arguments)  
             {  
                //arguments to pass to the workflow  
                creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
             }  
          }  
          //reply to client with instanceId  
          responseContext.SendResponse(instanceId, null);  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
       return creationContext;  
    }  
    ```  
  
### <a name="create-a-standard-endpoint-element-to-allow-you-to-configure-the-workflowcreationendpoint"></a>Criar um elemento de ponto de extremidade padrão para permitir que você configure o WorkflowCreationEndpoint  
  
1.  Adicione uma referência ao compartilhado no `CreationEndpoint` projeto  
  
2.  Adicionar uma nova classe chamada `CreationEndpointElement`, derivada de <xref:System.ServiceModel.Configuration.StandardEndpointElement> para o `CreationEndpoint` projeto. Essa classe representa um `CreationEndpoint` em um arquivo Web. config.  
  
    ```  
    using System;  
    using System.Configuration;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Configuration;  
    using System.ServiceModel.Description;  
    using Shared;  
  
    namespace CreationEndpointTest  
    {  
        //config element for CreationEndpoint  
        public class CreationEndpointElement : StandardEndpointElement  
        {  
       }  
    ```  
  
3.  Adicionar uma propriedade chamada `EndpointType` para retornar o tipo do ponto de extremidade.  
  
    ```  
    protected override Type EndpointType  
    {  
       get { return typeof(CreationEndpoint); }  
    }  
    ```  
  
4.  Substituir o <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> método e retorna um novo `CreationEndpoint`.  
  
    ```  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
    {  
       return new CreationEndpoint();  
    }  
    ```  
  
5.  Sobrecarga de <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>, e <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> métodos. Esses métodos apenas precisam ser definidos, não é preciso adicionar qualquer código para eles.  
  
    ```  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
    ```  
  
6.  Adicione a classe de coleção para `CreationEndpoint` para o arquivo CreationEndpointElement.cs no `CreationEndpoint` projeto. Essa classe é usada por configuração para manter um número de `CreationEndpoint` instâncias em um arquivo Web. config.  
  
    ```  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
    ```  
  
7.  Compile a solução.  
  
### <a name="host-the-workflow-in-iis"></a>Host de fluxo de trabalho no IIS  
  
1.  Criar um novo aplicativo chamado `MyCreationEndpoint` no IIS.  
  
2.  Copie o arquivo workflow1.xaml gerado pelo designer de fluxo de trabalho para o diretório de aplicativo e renomeie-o para workflow1.xamlx.  
  
3.  Copie os arquivos de CreationEndpoint.dll e shared.dll para o diretório bin do aplicativo (criar o diretório bin se não estiver presente).  
  
4.  Substitua o conteúdo do arquivo Web. config no `CreationEndpoint` projeto com o código a seguir.  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.web>  
        <compilation debug="true" targetFramework="4.0" />  
      </system.web>   
    </configuration>  
    ```  
  
5.  Após o `<system.web>` elemento, registrar `CreationEndpoint` adicionando o seguinte código de configuração.  
  
    ```xml  
    <system.serviceModel>  
        <!--register CreationEndpoint-->  
        <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
        <extensions>  
          <endpointExtensions>  
            <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, CreationEndpoint, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </endpointExtensions>  
        </extensions>  
    </system.serviceModel>  
    ```  
  
     Isso registra o `CreationEndpointCollection` de classe para que você possa configurar um `CreationEndpoint` em um arquivo Web. config.  
  
6.  Adicionar um `<service>` elemento (após o \</extensions > marca) com um `CreationEndpoint` que vai escutar mensagens de entrada.  
  
    ```xml  
    <services>  
          <!-- add endpoint to service-->  
          <service name="Workflow1" behaviorConfiguration="basicConfig" >  
            <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
          </service>  
        </services>  
    ```  
  
7.  Adicionar um \<comportamentos > elemento (após o  \< /services > marca) para habilitar metadados de serviço.  
  
    ```xml  
    <behaviors>  
          <serviceBehaviors>  
            <behavior name="basicConfig">  
              <serviceMetadata httpGetEnabled="true" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
    ```  
  
8.  Copie o Web. config para seu diretório de aplicativo do IIS.  
  
9. Teste para ver se o ponto de extremidade de criação está funcionando, inicie o Internet Explorer e navegando até http://localhost/MyCreationEndpoint/Workflow1.xamlx. O Internet Explorer deve exibir a tela a seguir:  
  
     ![Testando o serviço](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")  
  
### <a name="create-a-client-that-will-call-the-creationendpoint"></a>Crie um cliente que chamará o CreationEndpoint.  
  
1.  Adicionar um novo aplicativo de Console para o `CreationEndpointTest` solução.  
  
2.  Adicione referências a System.ServiceModel.dll, System.ServiceModel.Activities e o `Shared` projeto.  
  
3.  No `Main` método cria um <xref:System.ServiceModel.ChannelFactory%601> do tipo `IWorkflowCreation` e chame <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Isso retornará um proxy. Em seguida, você pode chamar `Create` no proxy para criar a instância de fluxo de trabalho hospedados no IIS:  
  
    ```  
    using System.Text;  
    using Shared;  
    using System.ServiceModel;  
  
    namespace CreationEndpointClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                try  
                {  
                    //client using BasicHttpBinding  
                    IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/CreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                    Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                    Console.WriteLine("Press return to exit ...");  
                    Console.ReadLine();  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine(ex);  
                    Console.ReadLine();  
                }  
            }  
        }  
    }  
    ```  
  
4.  Execute o CreationEndpointClient. A saída deve se parecer com o seguinte:  
  
    ```Output  
    Workflow Instance created using CreationEndpoint added in config. Instance Id: 0875dac0-2b8b-473e-b3cc-abcb235e9693Press return to exit ...  
    ```  
  
    > [!NOTE]
    >  Você não verá a saída do fluxo de trabalho porque ele está em execução no IIS que não tem nenhuma saída de console.  
  
## <a name="example"></a>Exemplo  
 Este é o código completo para este exemplo.  
  
```xaml  
<!-— workflow1.xamlx -->  
<WorkflowService mc:Ignorable="sap"   
                 ConfigurationName="Workflow1"   
                 sap:VirtualizedContainerService.HintSize="263,230"   
                 Name="Workflow1"   
                 mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces"   
                 xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"   
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:mv="clr-namespace:Microsoft.VisualBasic;assembly=System"   
                 xmlns:mva="clr-namespace:Microsoft.VisualBasic.Activities;assembly=System.Activities"   
                 xmlns:p="http://schemas.microsoft.com/netfx/2009/xaml/activities"   
                 xmlns:s="clr-namespace:System;assembly=mscorlib"   
                 xmlns:s1="clr-namespace:System;assembly=System"   
                 xmlns:s2="clr-namespace:System;assembly=System.Xml"   
                 xmlns:s3="clr-namespace:System;assembly=System.Core"   
                 xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities"   
                 xmlns:sap="http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation"   
                 xmlns:scg="clr-namespace:System.Collections.Generic;assembly=System"   
                 xmlns:scg1="clr-namespace:System.Collections.Generic;assembly=System.ServiceModel"   
                 xmlns:scg2="clr-namespace:System.Collections.Generic;assembly=System.Core"   
                 xmlns:scg3="clr-namespace:System.Collections.Generic;assembly=mscorlib"   
                 xmlns:sd="clr-namespace:System.Data;assembly=System.Data"   
                 xmlns:sl="clr-namespace:System.Linq;assembly=System.Core"   
                 xmlns:st="clr-namespace:System.Text;assembly=mscorlib"   
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <p:Sequence DisplayName="Sequential Service"   
              sad:XamlDebuggerXmlReader.FileName="c:\projects\CreationEndpointTest\CreationEndpoint\Service1.xamlx"   
              sap:VirtualizedContainerService.HintSize="233,200"   
              mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces">  
    <p:Sequence.Variables>  
      <p:Variable x:TypeArguments="CorrelationHandle" Name="handle" />  
      <p:Variable x:TypeArguments="x:Int32" Name="data" />  
    </p:Sequence.Variables>  
    <sap:WorkflowViewStateService.ViewState>  
      <scg3:Dictionary x:TypeArguments="x:String, x:Object">  
        <x:Boolean x:Key="IsExpanded">True</x:Boolean>  
      </scg3:Dictionary>  
    </sap:WorkflowViewStateService.ViewState>  
    <p:WriteLine sap:VirtualizedContainerService.HintSize="211,61" Text="Hello, world" />  
  </p:Sequence>  
</WorkflowService>  
```  
  
```csharp  
// CreationEndpointElement.cs  
using System;  
using System.Configuration;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Description;  
using Shared;  
  
namespace CreationEndpointTest  
{  
    //config element for CreationEndpoint  
    public class CreationEndpointElement : StandardEndpointElement  
    {  
        protected override Type EndpointType  
        {  
            get { return typeof(CreationEndpoint); }  
        }  
  
        protected override ConfigurationPropertyCollection Properties  
        {  
            get  
            {  
                ConfigurationPropertyCollection properties = base.Properties;  
                properties.Add(new ConfigurationProperty("name", typeof(String), null, ConfigurationPropertyOptions.IsRequired));  
                return properties;  
            }  
        }  
  
        protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
        {  
            return new CreationEndpoint();  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
    }  
  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
}  
```  
  
```xml  
<!-- web.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <!--register CreationEndpoint-->  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
    <extensions>  
      <endpointExtensions>  
        <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, Shared, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </endpointExtensions>  
    </extensions>  
    <services>  
      <!-- add endpoint to service-->  
      <service name="Workflow1" behaviorConfiguration="basicConfig" >  
        <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="basicConfig">  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```csharp  
// IWorkflowCreation.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
  
namespace Shared  
{  
    //service contract exposed from the endpoint  
    [ServiceContract(Name = "IWorkflowCreation")]  
    public interface IWorkflowCreation  
    {  
        [OperationContract(Name = "Create")]  
        Guid Create(IDictionary<string, object> inputs);  
  
        [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
        void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
    }  
}  
```  
  
```csharp  
// CreationEndpoint.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Channels;  
using System.ServiceModel;  
using System.Globalization;  
using System.Diagnostics;  
  
namespace Shared  
{  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
  
        public CreationEndpoint(Binding binding, EndpointAddress address)  
            : base(typeof(IWorkflowCreation), binding, address) { }  
  
        public CreationEndpoint()  
            : this(GetDefaultBinding(),  
                new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative)))) { }  
  
        static Uri DefaultBaseUri  
        {  
            get  
            {  
                if (defaultBaseUri == null)  
                {  
                    defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                        Process.GetCurrentProcess().Id,  
                        AppDomain.CurrentDomain.Id));  
                }  
                return defaultBaseUri;  
            }  
        }  
  
        //defaults to NetNamedPipeBinding  
        public static Binding GetDefaultBinding()  
        {  
            return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
        }  
  
        protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
        {  
            //Create was called by client  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                return Guid.Empty;  
            }  
  
            //CreateWithInstanceId was called by client  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                return (Guid)inputs[1];  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
        }  
  
        protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
        {  
            WorkflowCreationContext creationContext = new WorkflowCreationContext();  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to the workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
                //reply to client with instanceId  
                responseContext.SendResponse(instanceId, null);  
            }  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
            return creationContext;  
        }  
    }  
}  
```  
  
```csharp  
// CreationEndpointClient.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Shared;  
using System.ServiceModel;  
  
namespace CreationClient  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                //client using BasicHttpBinding  
                IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/MyCreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                Console.WriteLine("Press return to exit ...");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex);  
                Console.ReadLine();  
            }  
  
        }  
    }  
  
}  
```  
  
 Este exemplo pode parecer confuso, pois implementem um serviço que implementa `IWorkflowCreation`. Isso ocorre porque o `CreationEndpoint` faz isso para você.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Hospedagem nos Serviços de Informações da Internet](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Práticas recomendadas de hospedagem de Serviços de Informações da Internet](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Instruções de hospedagem do Serviços de Informações da Internet](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [Arquitetura do Windows Workflow](../../../../docs/framework/windows-workflow-foundation/architecture.md)  
 [Indicador de resumo de WorkflowHostingEndpoint](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)  
 [Hospedando novamente o Designer de Fluxo de Trabalho](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Visão geral do Windows Workflow](../../../../docs/framework/windows-workflow-foundation/overview.md)
