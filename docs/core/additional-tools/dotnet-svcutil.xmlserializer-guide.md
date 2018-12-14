# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="392b8-101">Usar o dotnet-svcutil.xmlserializer no .NET Core</span><span class="sxs-lookup"><span data-stu-id="392b8-101">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

## <a name="prerequisites"></a><span data-ttu-id="392b8-102">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="392b8-102">Prerequisites</span></span>

<span data-ttu-id="392b8-103">É necessário o seguinte para que o dotnet-svcutil.xmlserializer funcione.</span><span class="sxs-lookup"><span data-stu-id="392b8-103">The following is required for dotnet-svcutil.xmlserializer to work.</span></span> 

* [<span data-ttu-id="392b8-104">SDK do .NET Core 2.1 ou posteriores</span><span class="sxs-lookup"><span data-stu-id="392b8-104">.NET Core 2.1 SDK or later</span></span>](https://www.microsoft.com/net/download/dotnet-core/sdk-2.1.300)
* [<span data-ttu-id="392b8-105">Tempo de execução do .NET Core 2.1 ou posterior</span><span class="sxs-lookup"><span data-stu-id="392b8-105">.NET Core Runtime 2.1 or later</span></span>](https://www.microsoft.com/net/download/dotnet-core/runtime-2.1.0)

<span data-ttu-id="392b8-106">Você pode usar o comando `dotnet --info` para verificar quais versões do SDK do .NET Core e do tempo de execução estão instaladas.</span><span class="sxs-lookup"><span data-stu-id="392b8-106">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

<span data-ttu-id="392b8-107">Para usar o dotnet-svcutil.xmlserializer em um aplicativo de console do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="392b8-107">To use dotnet-svcutil.xmlserializer in a .NET Core console application:</span></span>

1. <span data-ttu-id="392b8-108">Crie um serviço do WCF chamado “MeuServiçoWCF” usando o modelo padrão “Aplicativo de serviço WCF” no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="392b8-108">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span>  <span data-ttu-id="392b8-109">Adicione o atributo ```[XmlSerializerFormat]``` ao método de serviço como a seguir</span><span class="sxs-lookup"><span data-stu-id="392b8-109">Add ```[XmlSerializerFormat]``` attribute on the service method like the following</span></span>
    ```c#
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```
2. <span data-ttu-id="392b8-110">Crie um aplicativo de console do .NET Core como um aplicativo cliente do WCF direcionado a netcoreapp 2.1, por exemplo, crie um aplicativo chamado “MeuClienteWCF” com o comando</span><span class="sxs-lookup"><span data-stu-id="392b8-110">Create a .NET Core console application as WCF client application that targets at netcoreapp 2.1, e.g. create an app named 'MyWCFClient' with the command,</span></span>
    ```
    dotnet new console --name MyWCFClient
    ```
    <span data-ttu-id="392b8-111">Verifique se seu csproj é direcionado a um netcoreapp 2.1.</span><span class="sxs-lookup"><span data-stu-id="392b8-111">Make sure your csproj targets a netcoreapp 2.1.</span></span> <span data-ttu-id="392b8-112">Para tanto, use o seguinte elemento XML no arquivo .csproj</span><span class="sxs-lookup"><span data-stu-id="392b8-112">This is done using the following XML element in your .csproj file</span></span>
    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```
3. <span data-ttu-id="392b8-113">Adicione uma referência de pacote a System.ServiceModel.Http executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="392b8-113">Add a package reference to System.ServiceModel.Http by running the following command:</span></span>
   
   ```dotnet add package System.ServiceModel.Http -v 4.5.0```

4. <span data-ttu-id="392b8-114">Adicione o código de cliente do WCF:</span><span class="sxs-lookup"><span data-stu-id="392b8-114">Add the WCF Client code:</span></span>
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
5. <span data-ttu-id="392b8-115">Edite o arquivo .csproj e adicione uma referência ao pacote dotnet-svcutil.xmlserializer.</span><span class="sxs-lookup"><span data-stu-id="392b8-115">Edit the .csproj file and add a reference to the dotnet-svcutil.xmlserializer package.</span></span> <span data-ttu-id="392b8-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="392b8-116">For example:</span></span>

    <span data-ttu-id="392b8-117">i.</span><span class="sxs-lookup"><span data-stu-id="392b8-117">i.</span></span> <span data-ttu-id="392b8-118">Execute o comando: `dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`</span><span class="sxs-lookup"><span data-stu-id="392b8-118">Run command: `dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`</span></span>

    <span data-ttu-id="392b8-119">ii.</span><span class="sxs-lookup"><span data-stu-id="392b8-119">ii.</span></span> <span data-ttu-id="392b8-120">Adicione as seguintes linhas em MeuClienteWCF.csproj:</span><span class="sxs-lookup"><span data-stu-id="392b8-120">Add the following lines in MyWCFClient.csproj,</span></span>
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="392b8-121">Compile o aplicativo executando `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="392b8-121">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="392b8-122">Se tudo for bem-sucedido, um assembly chamado MeuClienteWCF.XmlSerializers.dll será gerado na pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="392b8-122">If everything succeeds, an assembly named MyWCFClient.XmlSerializers.dll will be generated in the output folder.</span></span> <span data-ttu-id="392b8-123">Se a ferramenta não conseguiu gerar o assembly, você verá avisos na saída do build.</span><span class="sxs-lookup"><span data-stu-id="392b8-123">You will see warnings in the build output if the tool failed to generate the assembly.</span></span>

7. <span data-ttu-id="392b8-124">Inicie o serviço WCF, por exemplo, executando http://localhost:2561/Service1.svc no navegador.</span><span class="sxs-lookup"><span data-stu-id="392b8-124">Start the WCF service e.g. by running http://localhost:2561/Service1.svc in the browser.</span></span> <span data-ttu-id="392b8-125">Depois, inicie o aplicativo cliente, e ele será carregado automaticamente e usará os serializadores pré-gerados no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="392b8-125">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>
