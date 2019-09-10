---
title: Usar o dotnet-svcutil.xmlserializer no .NET Core
description: Saiba como você pode usar o pacote NuGet `dotnet-svcutil.xmlserializer` para pré-gerar um assembly de serialização para projetos .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: a98f8d30f2e37b722a3bf1f93be8fe9df540a468
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848971"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Usar o dotnet-svcutil.xmlserializer no .NET Core

O pacote NuGet `dotnet-svcutil.xmlserializer` pode pré-gerar um assembly de serialização para projetos .NET Core. Ele pré-gera o código de serialização C# para os tipos no aplicativo cliente que são usados pelo Contrato de Serviço do WCF e que podem ser serializados pelo XmlSerializer. Isso melhora o desempenho de inicialização da serialização de XML ao serializar ou desserializar objetos desses tipos.

## <a name="prerequisites"></a>Pré-requisitos

* [SDK do .NET Core 2.1](https://dotnet.microsoft.com/download) ou posterior
* Seu editor de código favorito

Você pode usar o comando `dotnet --info` para verificar quais versões do SDK do .NET Core e do tempo de execução estão instaladas.

## <a name="getting-started"></a>Introdução

Para usar `dotnet-svcutil.xmlserializer` em um aplicativo de console do .NET Core:

1. Crie um serviço do WCF chamado “MeuServiçoWCF” usando o modelo padrão “Aplicativo de serviço WCF” no .NET Framework. Adicione o atributo `[XmlSerializerFormat]` ao método de serviço desta forma:

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. Crie um aplicativo de console do .NET Core como um aplicativo cliente do WCF direcionado ao .NET Core 2.1 ou versões posteriores. Por exemplo, crie um aplicativo chamado 'MyWCFClient' com o seguinte comando:

    ```console
    dotnet new console --name MyWCFClient
    ```

    Para garantir que o projeto seja direcionado ao .NET Core 2.1 ou posterior, inspecione o elemento XML `TargetFramework` no arquivo de projeto:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Adicione uma referência de pacote a `System.ServiceModel.Http` executando o seguinte comando:

    ```console
    dotnet add package System.ServiceModel.Http
    ```

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

5. Adicione uma referência ao pacote `dotnet-svcutil.xmlserializer` executando o seguinte comando:
  
    ```console
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    A execução do comando deverá adicionar uma entrada ao arquivo de projeto semelhante a esta:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Compile o aplicativo executando `dotnet build`. Se tudo for bem-sucedido, um assembly chamado *MyWCFClient.XmlSerializers.dll* será gerado na pasta de saída. Se a ferramenta não puder gerar o assembly, você verá avisos na saída do build.

7. Inicie o serviço WCF, por exemplo, executando `http://localhost:2561/Service1.svc` no navegador. Depois, inicie o aplicativo cliente, e ele será carregado automaticamente e usará os serializadores pré-gerados no tempo de execução.
