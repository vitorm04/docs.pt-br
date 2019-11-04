---
title: Segurança de transporte WS
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
ms.openlocfilehash: 444d743271820d4b8590eef954561200345540a9
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424466"
---
# <a name="ws-transport-security"></a><span data-ttu-id="96182-102">Segurança de transporte WS</span><span class="sxs-lookup"><span data-stu-id="96182-102">WS Transport Security</span></span>
<span data-ttu-id="96182-103">Este exemplo demonstra o uso de segurança de transporte SSL com a associação de <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="96182-103">This sample demonstrates the use of SSL transport security with the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span> <span data-ttu-id="96182-104">Por padrão, a associação de `wsHttpBinding` fornece comunicação HTTP.</span><span class="sxs-lookup"><span data-stu-id="96182-104">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="96182-105">Quando configurado para segurança de transporte, a associação dá suporte à comunicação HTTPS.</span><span class="sxs-lookup"><span data-stu-id="96182-105">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="96182-106">Este exemplo é baseado no [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="96182-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="96182-107">O `wsHttpBinding` é especificado e configurado nos arquivos de configuração do aplicativo para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="96182-107">The `wsHttpBinding` is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96182-108">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="96182-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="96182-109">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="96182-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="96182-110">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="96182-110">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="96182-111">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="96182-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="96182-112">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="96182-112">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 <span data-ttu-id="96182-113">O código do programa no exemplo é idêntico ao do serviço de [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="96182-113">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="96182-114">Você deve criar um certificado e atribuí-lo usando o assistente de certificado do servidor Web antes de compilar e executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="96182-114">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="96182-115">A definição do ponto de extremidade e a definição de associação nas configurações do arquivo de configuração habilitam o modo de segurança `Transport`, conforme mostrado no exemplo de configuração a seguir para o cliente.</span><span class="sxs-lookup"><span data-stu-id="96182-115">The endpoint definition and binding definition in the configuration file settings enable `Transport` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address="https://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as None -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="96182-116">O endereço especificado usa o esquema https://.</span><span class="sxs-lookup"><span data-stu-id="96182-116">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="96182-117">A configuração de associação define o modo de segurança como `Transport`.</span><span class="sxs-lookup"><span data-stu-id="96182-117">The binding configuration sets the security mode to `Transport`.</span></span> <span data-ttu-id="96182-118">O mesmo modo de segurança deve ser especificado no arquivo Web. config do serviço.</span><span class="sxs-lookup"><span data-stu-id="96182-118">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="96182-119">Como o certificado usado neste exemplo é um certificado de teste criado com MakeCert. exe, um alerta de segurança é exibido quando você tenta acessar um https: address, como https://localhost/servicemodelsamples/service.svc, no seu navegador.</span><span class="sxs-lookup"><span data-stu-id="96182-119">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="96182-120">Para permitir que o cliente do Windows Communication Foundation (WCF) funcione com um certificado de teste em vigor, um código adicional foi adicionado ao cliente para suprimir o alerta de segurança.</span><span class="sxs-lookup"><span data-stu-id="96182-120">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="96182-121">Esse código e a classe que o acompanham não são necessários ao usar certificados de produção.</span><span class="sxs-lookup"><span data-stu-id="96182-121">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="96182-122">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="96182-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="96182-123">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="96182-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="96182-124">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="96182-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="96182-125">Instale o ASP.NET 4,0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="96182-125">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="96182-126">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="96182-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="96182-127">Verifique se você executou as [instruções de instalação do certificado do servidor serviços de informações da Internet (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="96182-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="96182-128">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="96182-128">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="96182-129">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="96182-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
