---
title: BasicBinding com segurança de transporte
ms.date: 03/30/2017
ms.assetid: f49b1de6-0254-4362-8ef2-fccd8ff9688b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 69257099338ae2d50c5ea184c0800d0057e020f4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45658542"
---
# <a name="basicbinding-with-transport-security"></a><span data-ttu-id="38bd7-102">BasicBinding com segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="38bd7-102">BasicBinding with Transport Security</span></span>
<span data-ttu-id="38bd7-103">Este exemplo demonstra o uso da segurança de transporte SSL com a associação básica.</span><span class="sxs-lookup"><span data-stu-id="38bd7-103">This sample demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="38bd7-104">Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="38bd7-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="38bd7-105">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="38bd7-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="38bd7-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="38bd7-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="38bd7-107">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="38bd7-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="38bd7-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="38bd7-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\TransportSecurity`  
  
## <a name="sample-details"></a><span data-ttu-id="38bd7-109">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="38bd7-109">Sample Details</span></span>  
 <span data-ttu-id="38bd7-110">Por padrão, a associação básica oferece suporte à comunicação HTTP.</span><span class="sxs-lookup"><span data-stu-id="38bd7-110">By default, the basic binding supports HTTP communication.</span></span> <span data-ttu-id="38bd7-111">O exemplo mostra como habilitar a segurança de transporte para a associação básica.</span><span class="sxs-lookup"><span data-stu-id="38bd7-111">The sample shows how to enable transport security for the basic binding.</span></span> <span data-ttu-id="38bd7-112">Antes de executar o exemplo, você deve criar um certificado e atribuí-lo usando o Assistente de certificado do servidor Web.</span><span class="sxs-lookup"><span data-stu-id="38bd7-112">Before you run the sample, you must create a certificate and assign it by using the Web Server Certificate Wizard.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38bd7-113">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="38bd7-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="38bd7-114">O código do programa de exemplo é idêntico do [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span><span class="sxs-lookup"><span data-stu-id="38bd7-114">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="38bd7-115">A definição de ponto de extremidade e a definição de associação em que o arquivo de configuração são modificados para permitir a comunicação segura, conforme mostrado no seguinte exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="38bd7-115">The endpoint definition and binding definition in the configuration file settings are modified to enable secure communication, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
   </services>  
  <bindings>  
    <basicHttpBinding>  
      <!-- Configure basicHttpBinding with Transport security -- >  
      <!-- mode and clientCredentialType set to None.-->  
      <binding name="Binding1">  
        <security mode="Transport">  
          <transport clientCredentialType="None"/>  
        </security>  
      </binding>  
    </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="38bd7-116">Como o certificado usado neste exemplo é um certificado de teste criado com Makecert.exe, um alerta de segurança é exibida quando você tenta acessar um HTTPS: endereço no seu navegador, tais como https://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="38bd7-116">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an HTTPS: address in your browser, such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="38bd7-117">Para permitir que o cliente do Windows Communication Foundation (WCF) para trabalhar com um certificado de teste, o código adicional é adicionado ao cliente para suprimir o alerta de segurança.</span><span class="sxs-lookup"><span data-stu-id="38bd7-117">To allow the Windows Communication Foundation (WCF) client to work with a test certificate, some additional code is added to the client to suppress the security alert.</span></span> <span data-ttu-id="38bd7-118">Esse código e a classe que acompanha este artigo, não é necessário ao usar certificados real.</span><span class="sxs-lookup"><span data-stu-id="38bd7-118">This code, and the accompanying class, is not necessary when using real certificates.</span></span>  

```csharp
// This code is required only for test certificates such as those   
// created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="38bd7-119">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="38bd7-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="38bd7-120">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="38bd7-120">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="38bd7-121">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="38bd7-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="38bd7-122">Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="38bd7-122">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="38bd7-123">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="38bd7-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="38bd7-124">Certifique-se de que você tenha executado o [instruções de instalação do certificado de servidor de serviços de informações da Internet (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="38bd7-124">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="38bd7-125">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="38bd7-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="38bd7-126">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="38bd7-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38bd7-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38bd7-127">See Also</span></span>
