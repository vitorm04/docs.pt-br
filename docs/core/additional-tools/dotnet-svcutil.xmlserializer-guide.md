# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Usar o dotnet-svcutil.xmlserializer no .NET Core

## <a name="prerequisites"></a>Pré-requisitos

É necessário o seguinte para que o dotnet-svcutil.xmlserializer funcione. 

* [SDK do .NET Core 2.1 ou posteriores](https://www.microsoft.com/net/download/dotnet-core/sdk-2.1.300)
* [Tempo de execução do .NET Core 2.1 ou posterior](https://www.microsoft.com/net/download/dotnet-core/runtime-2.1.0)

Você pode usar o comando `dotnet --info` para verificar quais versões do SDK do .NET Core e do tempo de execução estão instaladas.

Para usar o dotnet-svcutil.xmlserializer em um aplicativo de console do .NET Core:

1. Crie um serviço do WCF chamado “MeuServiçoWCF” usando o modelo padrão “Aplicativo de serviço WCF” no .NET Framework.  Adicione o atributo ```[XmlSerializerFormat]``` ao método de serviço como a seguir
    ```c#
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```
2. Crie um aplicativo de console do .NET Core como um aplicativo cliente do WCF direcionado a netcoreapp 2.1, por exemplo, crie um aplicativo chamado “MeuClienteWCF” com o comando
    ```
    dotnet new console --name MyWCFClient
    ```
    Verifique se seu csproj é direcionado a um netcoreapp 2.1. Para tanto, use o seguinte elemento XML no arquivo .csproj
    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```
3. Adicione uma referência de pacote a System.ServiceModel.Http executando o seguinte comando:
   
   ```dotnet add package System.ServiceModel.Http -v 4.5.0```

4. Adicione o código de cliente do WCF:
    ```csharp
    using System.ServiceModel;
    
    class Program
    {
        static void Main(string[] args)
        {
            var myBinding = new BasicHttpBinding();
            var myEndpoint = new EndpointAddress("http://localhost:2561/Service1.svc"); //Fill your service url here
            var myChannelFactory = new ChannelFactory<IService1>(myBinding, myEndpoint);
            IService1 client = myChannelFactory.CreateChannel();
            string s = client.GetData(1);
            ((ICommunicationObject)client).Close();
        }
    }

    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```
5. Edite o arquivo .csproj e adicione uma referência ao pacote dotnet-svcutil.xmlserializer. Por exemplo:

    i. Execute o comando: `dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`

    ii. Adicione as seguintes linhas em MeuClienteWCF.csproj:
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Compile o aplicativo executando `dotnet build`. Se tudo for bem-sucedido, um assembly chamado MeuClienteWCF.XmlSerializers.dll será gerado na pasta de saída. Se a ferramenta não conseguiu gerar o assembly, você verá avisos na saída do build.

7. Inicie o serviço WCF, por exemplo, executando http://localhost:2561/Service1.svc no navegador. Depois, inicie o aplicativo cliente, e ele será carregado automaticamente e usará os serializadores pré-gerados no tempo de execução.
