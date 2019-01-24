---
title: Transporte de WS com credencial de mensagem
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 9495dea69e489321360b1f4e24fea7d1e84fa038
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690209"
---
# <a name="ws-transport-with-message-credential"></a><span data-ttu-id="00cee-102">Transporte de WS com credencial de mensagem</span><span class="sxs-lookup"><span data-stu-id="00cee-102">WS Transport With Message Credential</span></span>
<span data-ttu-id="00cee-103">Este exemplo demonstra o uso da segurança de transporte do SSL em combinação com a credencial de cliente que está sendo executada na mensagem.</span><span class="sxs-lookup"><span data-stu-id="00cee-103">This sample demonstrates the use of SSL transport security in combination with client credential being carried in the message.</span></span> <span data-ttu-id="00cee-104">Este exemplo usa o `wsHttpBinding` associação.</span><span class="sxs-lookup"><span data-stu-id="00cee-104">This sample uses the `wsHttpBinding` binding.</span></span>  
  
 <span data-ttu-id="00cee-105">Por padrão, o `wsHttpBinding` associação fornece comunicação HTTP.</span><span class="sxs-lookup"><span data-stu-id="00cee-105">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="00cee-106">Quando configurado para segurança de transporte, a associação dá suporte a comunicação HTTPS.</span><span class="sxs-lookup"><span data-stu-id="00cee-106">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="00cee-107">HTTPS fornece confidencialidade e proteção de integridade para as mensagens que são transmitidos eletronicamente.</span><span class="sxs-lookup"><span data-stu-id="00cee-107">HTTPS provides confidentiality and integrity protection for the messages that are transmitted over the wire.</span></span> <span data-ttu-id="00cee-108">No entanto, o conjunto de mecanismos de autenticação que pode ser usado para autenticar o cliente para o serviço é limitado dá suporte ao transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="00cee-108">However the set of authentication mechanisms that can be used to authenticate the client to the service is limited to what the HTTPS transport supports.</span></span> <span data-ttu-id="00cee-109">Windows Communication Foundation (WCF) oferece um `TransportWithMessageCredential` modo de segurança que foi projetado para superar essa limitação.</span><span class="sxs-lookup"><span data-stu-id="00cee-109">Windows Communication Foundation (WCF) offers a `TransportWithMessageCredential` security mode that is designed to overcome this limitation.</span></span> <span data-ttu-id="00cee-110">Quando esse modo de segurança está configurado, a segurança de transporte é usada para fornecer confidencialidade e integridade para as mensagens transmitidas e realizar a autenticação de serviço.</span><span class="sxs-lookup"><span data-stu-id="00cee-110">When this security mode is configured, the transport security is used to provide confidentiality and integrity for the transmitted messages and to perform the service authentication.</span></span> <span data-ttu-id="00cee-111">No entanto, a autenticação do cliente é executada colocando-se a credencial do cliente diretamente na mensagem.</span><span class="sxs-lookup"><span data-stu-id="00cee-111">However, the client authentication is performed by putting the client credential directly in the message.</span></span> <span data-ttu-id="00cee-112">Isso permite que você use qualquer tipo de credencial que é compatível com o modo de segurança de mensagem para a autenticação de cliente, mantendo o benefício de desempenho do modo de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="00cee-112">This allows you to use any credential type that is supported by the message security mode for the client authentication while keeping the performance benefit of transport security mode.</span></span>  
  
 <span data-ttu-id="00cee-113">Neste exemplo, um `UserName` tipo de credencial é usado para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="00cee-113">In this sample, a `UserName` credential type is used to authenticate the client to the service.</span></span>  
  
 <span data-ttu-id="00cee-114">Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="00cee-114">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="00cee-115">O `wsHttpBinding` associação é especificada e configurada nos arquivos de configuração do aplicativo para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="00cee-115">The `wsHttpBinding` binding is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00cee-116">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="00cee-116">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="00cee-117">O código do programa de exemplo é quase idêntico do [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span><span class="sxs-lookup"><span data-stu-id="00cee-117">The program code in the sample is almost identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="00cee-118">Há uma operação adicional fornecida pelo contrato de serviço - `GetCallerIdentity`.</span><span class="sxs-lookup"><span data-stu-id="00cee-118">There is one additional operation provided by the service contract - `GetCallerIdentity`.</span></span> <span data-ttu-id="00cee-119">Essa operação retorna o nome da identidade do chamador para o chamador.</span><span class="sxs-lookup"><span data-stu-id="00cee-119">This operation returns the name of the caller's identity to the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="00cee-120">Você deve criar um certificado e atribuí-lo usando o Assistente de certificado do servidor Web antes de criar e executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="00cee-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="00cee-121">A definição de ponto de extremidade e a definição de associação na configuração do arquivo de configurações permitem `TransportWithMessageCredential` modo de segurança, conforme mostrado no seguinte exemplo de configuração para o cliente.</span><span class="sxs-lookup"><span data-stu-id="00cee-121">The endpoint definition and binding definition in the configuration file settings enable `TransportWithMessageCredential` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="00cee-122">O endereço especificado usa o esquema de https://.</span><span class="sxs-lookup"><span data-stu-id="00cee-122">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="00cee-123">A configuração de associação define o modo de segurança para `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="00cee-123">The binding configuration sets the security mode to `TransportWithMessageCredential`.</span></span> <span data-ttu-id="00cee-124">O mesmo modo de segurança deve ser especificado no arquivo de Web. config do serviço.</span><span class="sxs-lookup"><span data-stu-id="00cee-124">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="00cee-125">Como o certificado usado neste exemplo é um certificado de teste criado com Makecert.exe, um alerta de segurança é exibida quando você tenta acessar um https: endereço, tais como `https://localhost/servicemodelsamples/service.svc `, do seu navegador.</span><span class="sxs-lookup"><span data-stu-id="00cee-125">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as  `https://localhost/servicemodelsamples/service.svc `, from your browser.</span></span> <span data-ttu-id="00cee-126">Para permitir que o cliente do WCF para trabalhar com um certificado de teste em vigor, o código adicional foi adicionado ao cliente para suprimir o alerta de segurança.</span><span class="sxs-lookup"><span data-stu-id="00cee-126">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="00cee-127">Esse código e a classe que acompanha este artigo, não é necessário ao usar certificados de produção.</span><span class="sxs-lookup"><span data-stu-id="00cee-127">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 <span data-ttu-id="00cee-128">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="00cee-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="00cee-129">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="00cee-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:   
YourDomainName\YourAccountName  
   Enter password:   
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="00cee-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="00cee-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="00cee-131">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00cee-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="00cee-132">Certifique-se de que você tenha executado o [instruções de instalação do certificado de servidor de serviços de informações da Internet (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="00cee-132">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
3.  <span data-ttu-id="00cee-133">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00cee-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="00cee-134">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00cee-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00cee-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00cee-135">See also</span></span>
