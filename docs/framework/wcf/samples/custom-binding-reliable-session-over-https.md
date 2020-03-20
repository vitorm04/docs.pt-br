---
title: Sessão confiável de associação personalizada através de HTTPS
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: 051e7f56662a2ca67018ae7dd29189ff50245fc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183869"
---
# <a name="custom-binding-reliable-session-over-https"></a><span data-ttu-id="159db-102">Sessão confiável de associação personalizada através de HTTPS</span><span class="sxs-lookup"><span data-stu-id="159db-102">Custom Binding Reliable Session over HTTPS</span></span>
<span data-ttu-id="159db-103">Esta amostra demonstra o uso da segurança de transporte SSL com sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="159db-103">This sample demonstrates the use of SSL transport security with Reliable Sessions.</span></span> <span data-ttu-id="159db-104">As Sessões Confiáveis implementam o protocolo de mensagens ws-confiável.</span><span class="sxs-lookup"><span data-stu-id="159db-104">Reliable Sessions implements the WS-Reliable Messaging protocol.</span></span> <span data-ttu-id="159db-105">Você pode ter uma sessão segura e confiável compondo o WS-Security sobre sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="159db-105">You can have a secure reliable session by composing WS-Security over Reliable Sessions.</span></span> <span data-ttu-id="159db-106">Mas, às vezes, você pode optar por usar a segurança de transporte HTTP com O SSL.</span><span class="sxs-lookup"><span data-stu-id="159db-106">But sometimes, you may choose to instead use HTTP transport security with SSL.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="159db-107">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="159db-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="159db-108">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="159db-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="159db-109">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="159db-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="159db-110">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="159db-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a><span data-ttu-id="159db-111">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="159db-111">Sample Details</span></span>  
 <span data-ttu-id="159db-112">O SSL garante que os pacotes em si estejam protegidos.</span><span class="sxs-lookup"><span data-stu-id="159db-112">SSL ensures that the packets themselves are secured.</span></span> <span data-ttu-id="159db-113">É importante notar que isso é diferente de garantir a sessão confiável usando o WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="159db-113">It is important to note that this is different from securing the reliable session using WS-Secure Conversation.</span></span>  
  
 <span data-ttu-id="159db-114">Para usar uma sessão confiável sobre HTTPS, você deve criar uma vinculação personalizada.</span><span class="sxs-lookup"><span data-stu-id="159db-114">To use reliable session over HTTPS, you must create a custom binding.</span></span> <span data-ttu-id="159db-115">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="159db-115">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="159db-116">Uma vinculação personalizada é criada usando o elemento de vinculação de sessão confiável e o [ \<httpsTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md).</span><span class="sxs-lookup"><span data-stu-id="159db-116">A custom binding is created using the reliable session binding element and the [\<httpsTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md).</span></span> <span data-ttu-id="159db-117">A configuração a seguir é da vinculação personalizada.</span><span class="sxs-lookup"><span data-stu-id="159db-117">The following configuration is of the custom binding.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="159db-118">O código do programa na amostra é idêntico ao do serviço [Getting Started.](../../../../docs/framework/wcf/samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="159db-118">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="159db-119">Você deve criar um certificado e atribuí-lo usando o Assistente de Certificado do Servidor Web antes de construir e executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="159db-119">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="159db-120">A definição de ponto final e a definição de vinculação nas configurações do arquivo de configuração permitem o uso de vinculação personalizada, conforme mostrado na configuração de amostra a seguir para o cliente.</span><span class="sxs-lookup"><span data-stu-id="159db-120">The endpoint definition and binding definition in the configuration file settings enable the use of custom binding as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"
                binding="customBinding"
                bindingConfiguration="reliableSessionOverHttps"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="159db-121">O endereço especificado usa o esquema https://.</span><span class="sxs-lookup"><span data-stu-id="159db-121">The address specified uses the https:// scheme.</span></span>  
  
 <span data-ttu-id="159db-122">Como o certificado usado nesta amostra é um certificado de teste criado com o Makecert.exe, um https://localhost/servicemodelsamples/service.svcalerta de segurança aparece quando você tenta acessar um endereço https: como , do seu navegador.</span><span class="sxs-lookup"><span data-stu-id="159db-122">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="159db-123">Para permitir que o cliente da Windows Communication Foundation (WCF) trabalhe com um certificado de teste em vigor, algum código adicional foi adicionado ao cliente para suprimir o alerta de segurança.</span><span class="sxs-lookup"><span data-stu-id="159db-123">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="159db-124">Este código, e a classe de acompanhamento, não é necessário ao usar certificados de produção.</span><span class="sxs-lookup"><span data-stu-id="159db-124">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="159db-125">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="159db-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="159db-126">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="159db-126">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="159db-127">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="159db-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="159db-128">Instale ASP.NET 4.0 usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="159db-128">Install  ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="159db-129">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="159db-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="159db-130">Certifique-se de que você tenha realizado as Instruções de Instalação do [Certificado de Servidor do Serviço de Informações da Internet (IIS).](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)</span><span class="sxs-lookup"><span data-stu-id="159db-130">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="159db-131">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="159db-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="159db-132">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="159db-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
