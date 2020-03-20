---
title: Segurança de transporte WS
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
ms.openlocfilehash: 221bf2e0d304e93242bb5fea6854c1c9bb72aec2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143454"
---
# <a name="ws-transport-security"></a><span data-ttu-id="ee181-102">Segurança de transporte WS</span><span class="sxs-lookup"><span data-stu-id="ee181-102">WS Transport Security</span></span>
<span data-ttu-id="ee181-103">Esta amostra demonstra o uso da segurança <xref:System.ServiceModel.WSHttpBinding> de transporte SSL com a vinculação.</span><span class="sxs-lookup"><span data-stu-id="ee181-103">This sample demonstrates the use of SSL transport security with the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span> <span data-ttu-id="ee181-104">Por padrão, `wsHttpBinding` a vinculação fornece comunicação HTTP.</span><span class="sxs-lookup"><span data-stu-id="ee181-104">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="ee181-105">Quando configurado para segurança de transporte, a vinculação suporta comunicação HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ee181-105">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="ee181-106">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="ee181-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="ee181-107">O `wsHttpBinding` é especificado e configurado nos arquivos de configuração do aplicativo para o cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="ee181-107">The `wsHttpBinding` is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee181-108">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ee181-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ee181-109">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ee181-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ee181-110">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ee181-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ee181-111">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="ee181-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee181-112">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ee181-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 <span data-ttu-id="ee181-113">O código do programa na amostra é idêntico ao do serviço [Getting Started.](../../../../docs/framework/wcf/samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="ee181-113">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="ee181-114">Você deve criar um certificado e atribuí-lo usando o Assistente de Certificado do Servidor Web antes de construir e executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="ee181-114">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="ee181-115">A definição de ponto final e a `Transport` definição de vinculação nas configurações do arquivo de configuração permitem o modo de segurança, conforme mostrado na configuração de exemplo a seguir para o cliente.</span><span class="sxs-lookup"><span data-stu-id="ee181-115">The endpoint definition and binding definition in the configuration file settings enable `Transport` security mode, as shown in the following sample configuration for the client.</span></span>  
  
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
  
 <span data-ttu-id="ee181-116">O endereço especificado usa o esquema https://.</span><span class="sxs-lookup"><span data-stu-id="ee181-116">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="ee181-117">A configuração de vinculação define o modo de segurança para `Transport`.</span><span class="sxs-lookup"><span data-stu-id="ee181-117">The binding configuration sets the security mode to `Transport`.</span></span> <span data-ttu-id="ee181-118">O mesmo modo de segurança deve ser especificado no arquivo Web.config do serviço.</span><span class="sxs-lookup"><span data-stu-id="ee181-118">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="ee181-119">Como o certificado usado nesta amostra é um certificado de teste criado com o Makecert.exe, um https://localhost/servicemodelsamples/service.svcalerta de segurança aparece quando você tenta acessar um endereço https: como , do seu navegador.</span><span class="sxs-lookup"><span data-stu-id="ee181-119">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="ee181-120">Para permitir que o cliente da Windows Communication Foundation (WCF) trabalhe com um certificado de teste em vigor, algum código adicional foi adicionado ao cliente para suprimir o alerta de segurança.</span><span class="sxs-lookup"><span data-stu-id="ee181-120">To allow the Windows Communication Foundation (WCF) client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="ee181-121">Este código, e a classe de acompanhamento, não é necessário ao usar certificados de produção.</span><span class="sxs-lookup"><span data-stu-id="ee181-121">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="ee181-122">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="ee181-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ee181-123">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="ee181-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ee181-124">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ee181-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ee181-125">Instale ASP.NET 4.0 usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="ee181-125">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="ee181-126">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee181-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="ee181-127">Certifique-se de que você tenha realizado as Instruções de Instalação do [Certificado de Servidor do Serviço de Informações da Internet (IIS).](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)</span><span class="sxs-lookup"><span data-stu-id="ee181-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="ee181-128">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee181-128">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="ee181-129">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee181-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
