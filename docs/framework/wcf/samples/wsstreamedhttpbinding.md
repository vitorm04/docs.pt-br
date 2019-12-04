---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: 36b4db5270205aec55ad52db40500c8d434a1560
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714546"
---
# <a name="wsstreamedhttpbinding"></a><span data-ttu-id="7fefd-102">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="7fefd-102">WSStreamedHttpBinding</span></span>

<span data-ttu-id="7fefd-103">O exemplo demonstra como criar uma associação que é projetada para dar suporte a cenários de streaming quando o transporte HTTP é usado.</span><span class="sxs-lookup"><span data-stu-id="7fefd-103">The sample demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>

> [!NOTE]
> <span data-ttu-id="7fefd-104">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="7fefd-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7fefd-105">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7fefd-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7fefd-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7fefd-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7fefd-107">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="7fefd-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7fefd-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="7fefd-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`

 <span data-ttu-id="7fefd-109">As etapas para criar e configurar uma nova associação padrão são as seguintes.</span><span class="sxs-lookup"><span data-stu-id="7fefd-109">The steps to create and configure a new standard binding are as follows.</span></span>

1. <span data-ttu-id="7fefd-110">Criar uma nova associação padrão</span><span class="sxs-lookup"><span data-stu-id="7fefd-110">Create a new standard binding</span></span>

    <span data-ttu-id="7fefd-111">As associações padrão no Windows Communication Foundation (WCF), como basicHttpBinding, e netTcpbinding, configuram os transportes subjacentes e a pilha de canal para requisitos específicos.</span><span class="sxs-lookup"><span data-stu-id="7fefd-111">The standard bindings in Windows Communication Foundation (WCF) such as basicHttpBinding, and netTcpBinding configure the underlying transports and channel stack for specific requirements.</span></span> <span data-ttu-id="7fefd-112">Neste exemplo, `WSStreamedHttpBinding` configura a pilha de canais para dar suporte ao streaming.</span><span class="sxs-lookup"><span data-stu-id="7fefd-112">In this sample, `WSStreamedHttpBinding` configures the channel stack to support streaming.</span></span> <span data-ttu-id="7fefd-113">Por padrão, o WS-Security e o sistema de mensagens confiável não são adicionados à pilha de canais porque não há suporte para os dois recursos pelo streaming.</span><span class="sxs-lookup"><span data-stu-id="7fefd-113">By default, WS-Security and reliable messaging are not added to the channel stack because both features are not supported by streaming.</span></span> <span data-ttu-id="7fefd-114">A nova associação é implementada na classe `WSStreamedHttpBinding` que deriva de <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="7fefd-114">The new binding is implemented in the class `WSStreamedHttpBinding` that derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="7fefd-115">O `WSStreamedHttpBinding` contém os seguintes elementos de associação: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>e <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="7fefd-115">The `WSStreamedHttpBinding` contains the following binding elements: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, and <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span> <span data-ttu-id="7fefd-116">A classe fornece um método `CreateBindingElements()` para configurar a pilha de associação resultante, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7fefd-116">The class provides a `CreateBindingElements()` method to configure the resulting binding stack, as shown in the following sample code.</span></span>

    ```csharp
    public override BindingElementCollection CreateBindingElements()
    {
        // return collection of BindingElements
        BindingElementCollection bindingElements = new BindingElementCollection();

        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by
        // the message encoder, and finally the transport at the end
        if (flowTransactions)
        {
            bindingElements.Add(transactionFlow);
        }
        bindingElements.Add(textEncoding);

        // add transport (http or https)
        bindingElements.Add(transport);
        return bindingElements.Clone();
    }
    ```

2. <span data-ttu-id="7fefd-117">Adicionar suporte à configuração</span><span class="sxs-lookup"><span data-stu-id="7fefd-117">Add configuration support</span></span>

    <span data-ttu-id="7fefd-118">Para expor o transporte por meio da configuração, o exemplo implementa mais duas classes —`WSStreamedHttpBindingConfigurationElement` e `WSStreamedHttpBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="7fefd-118">To expose the transport through configuration the sample implements two more classes—`WSStreamedHttpBindingConfigurationElement` and `WSStreamedHttpBindingSection`.</span></span> <span data-ttu-id="7fefd-119">A classe `WSStreamedHttpBindingSection` é uma <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> que expõe `WSStreamedHttpBinding` ao sistema de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="7fefd-119">The class `WSStreamedHttpBindingSection` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `WSStreamedHttpBinding` to the WCF configuration system.</span></span> <span data-ttu-id="7fefd-120">A maior parte da implementação é delegada para `WSStreamedHttpBindingConfigurationElement`, que deriva de <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="7fefd-120">The bulk of the implementation is delegated to `WSStreamedHttpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="7fefd-121">A classe `WSStreamedHttpBindingConfigurationElement` tem propriedades que correspondem às propriedades de `WSStreamedHttpBinding`e funções para mapear cada elemento de configuração para uma associação.</span><span class="sxs-lookup"><span data-stu-id="7fefd-121">The class `WSStreamedHttpBindingConfigurationElement` has properties that correspond to the properties of `WSStreamedHttpBinding`, and functions to map each configuration element to a binding.</span></span>

    <span data-ttu-id="7fefd-122">Registre o manipulador com o sistema de configuração, adicionando a seção a seguir ao arquivo de configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="7fefd-122">Register the handler with the configuration system, by adding the following section to the service's configuration file.</span></span>

    ```xml
    <configuration>
      <system.serviceModel>
        <extensions>
          <bindingExtensions>
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />
          </bindingExtensions>
        </extensions>
      </system.serviceModel>
    </configuration>
    ```

    <span data-ttu-id="7fefd-123">O manipulador pode ser referenciado na seção de configuração de serviceModel.</span><span class="sxs-lookup"><span data-stu-id="7fefd-123">The handler can then be referenced from the serviceModel configuration section.</span></span>

    ```xml
    <configuration>
      <system.serviceModel>
        <client>
          <endpoint
                    address="https://localhost/servicemodelsamples/service.svc"
                    bindingConfiguration="Binding"
                    binding="wsStreamedHttpBinding"
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>
        </client>
      </system.serviceModel>
    </configuration>
    ```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7fefd-124">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7fefd-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7fefd-125">Instale o ASP.NET 4,0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="7fefd-125">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="7fefd-126">Verifique se você executou as etapas listadas no [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7fefd-126">Ensure that you have performed the steps listed in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="7fefd-127">Verifique se você executou as [instruções de instalação do certificado do servidor serviços de informações da Internet (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="7fefd-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>

4. <span data-ttu-id="7fefd-128">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7fefd-128">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="7fefd-129">Para executar o exemplo em uma configuração entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7fefd-129">To run the sample in a cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

6. <span data-ttu-id="7fefd-130">Quando a janela do cliente for exibida, digite "Sample. txt".</span><span class="sxs-lookup"><span data-stu-id="7fefd-130">When the client window displays, type "Sample.txt".</span></span> <span data-ttu-id="7fefd-131">Você deve encontrar uma "cópia de Sample. txt" em seu diretório.</span><span class="sxs-lookup"><span data-stu-id="7fefd-131">You should find a "Copy of Sample.txt" in your directory.</span></span>

## <a name="the-wsstreamedhttpbinding-sample-service"></a><span data-ttu-id="7fefd-132">O serviço de exemplo WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="7fefd-132">The WSStreamedHttpBinding Sample Service</span></span>

<span data-ttu-id="7fefd-133">O serviço de exemplo que usa `WSStreamedHttpBinding` está localizado no subdiretório de serviço.</span><span class="sxs-lookup"><span data-stu-id="7fefd-133">The sample service that uses `WSStreamedHttpBinding` is located in the service subdirectory.</span></span> <span data-ttu-id="7fefd-134">A implementação de `OperationContract` usa uma `MemoryStream` para recuperar primeiro todos os dados do fluxo de entrada antes de retornar o `MemoryStream`.</span><span class="sxs-lookup"><span data-stu-id="7fefd-134">The implementation of `OperationContract` uses a `MemoryStream` to first retrieve all data from the incoming stream before returning the `MemoryStream`.</span></span> <span data-ttu-id="7fefd-135">O serviço de exemplo é hospedado pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="7fefd-135">The sample service is hosted by Internet Information Services (IIS).</span></span>

```csharp
[ServiceContract]
public interface IStreamedEchoService
{
    [OperationContract]
    Stream Echo(Stream data);
}

public class StreamedEchoService : IStreamedEchoService
{
    public Stream Echo(Stream data)
    {
        MemoryStream dataStorage = new MemoryStream();
        byte[] byteArray = new byte[8192];
        int bytesRead = data.Read(byteArray, 0, 8192);
        while (bytesRead > 0)
        {
            dataStorage.Write(byteArray, 0, bytesRead);
            bytesRead = data.Read(byteArray, 0, 8192);
        }
        data.Close();
        dataStorage.Seek(0, SeekOrigin.Begin);

        return dataStorage;
    }
}
```

## <a name="the-wsstreamedhttpbinding-sample-client"></a><span data-ttu-id="7fefd-136">O cliente de exemplo WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="7fefd-136">The WSStreamedHttpBinding Sample Client</span></span>

<span data-ttu-id="7fefd-137">O cliente usado para interagir com o serviço usando `WSStreamedHttpBinding` está localizado no subdiretório do cliente.</span><span class="sxs-lookup"><span data-stu-id="7fefd-137">The client that is used to interact with the service using `WSStreamedHttpBinding` is located in the client subdirectory.</span></span> <span data-ttu-id="7fefd-138">Como o certificado usado neste exemplo é um certificado de teste criado com MakeCert. exe, um alerta de segurança é exibido quando você tenta acessar um endereço HTTPS em seu navegador, como https://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="7fefd-138">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert displays when you attempt to access an HTTPS address in your browser such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="7fefd-139">Para permitir que o cliente WCF trabalhe com um certificado de teste em vigor, algum código adicional foi adicionado ao cliente para suprimir o alerta de segurança.</span><span class="sxs-lookup"><span data-stu-id="7fefd-139">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="7fefd-140">O código e a classe que o acompanha não são necessários ao usar certificados de produção.</span><span class="sxs-lookup"><span data-stu-id="7fefd-140">The code and the accompanying class are not required when using production certificates.</span></span>

```csharp
// WARNING: This code is only required for test certificates such as those created by makecert. It is
// not recommended for production code.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```
