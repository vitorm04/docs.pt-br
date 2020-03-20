---
title: Transporte de WS com credencial de mensagem
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 076d4490f6edc6efa8eeb50ae8baa23d5c4e369a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183140"
---
# <a name="ws-transport-with-message-credential"></a><span data-ttu-id="3caa8-102">Transporte de WS com credencial de mensagem</span><span class="sxs-lookup"><span data-stu-id="3caa8-102">WS Transport With Message Credential</span></span>
<span data-ttu-id="3caa8-103">Esta amostra demonstra o uso da segurança de transporte SSL em combinação com a credencial do cliente que está sendo transportada na mensagem.</span><span class="sxs-lookup"><span data-stu-id="3caa8-103">This sample demonstrates the use of SSL transport security in combination with client credential being carried in the message.</span></span> <span data-ttu-id="3caa8-104">Esta amostra `wsHttpBinding` usa a ligação.</span><span class="sxs-lookup"><span data-stu-id="3caa8-104">This sample uses the `wsHttpBinding` binding.</span></span>  
  
 <span data-ttu-id="3caa8-105">Por padrão, `wsHttpBinding` a vinculação fornece comunicação HTTP.</span><span class="sxs-lookup"><span data-stu-id="3caa8-105">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="3caa8-106">Quando configurado para segurança de transporte, a vinculação suporta comunicação HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3caa8-106">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="3caa8-107">O HTTPS fornece proteção de confidencialidade e integridade para as mensagens que são transmitidas pelo fio.</span><span class="sxs-lookup"><span data-stu-id="3caa8-107">HTTPS provides confidentiality and integrity protection for the messages that are transmitted over the wire.</span></span> <span data-ttu-id="3caa8-108">No entanto, o conjunto de mecanismos de autenticação que podem ser usados para autenticar o cliente ao serviço está limitado ao que o transporte HTTPS suporta.</span><span class="sxs-lookup"><span data-stu-id="3caa8-108">However the set of authentication mechanisms that can be used to authenticate the client to the service is limited to what the HTTPS transport supports.</span></span> <span data-ttu-id="3caa8-109">O Windows Communication Foundation (WCF) oferece um `TransportWithMessageCredential` modo de segurança projetado para superar essa limitação.</span><span class="sxs-lookup"><span data-stu-id="3caa8-109">Windows Communication Foundation (WCF) offers a `TransportWithMessageCredential` security mode that is designed to overcome this limitation.</span></span> <span data-ttu-id="3caa8-110">Quando esse modo de segurança é configurado, a segurança de transporte é usada para fornecer confidencialidade e integridade para as mensagens transmitidas e para executar a autenticação do serviço.</span><span class="sxs-lookup"><span data-stu-id="3caa8-110">When this security mode is configured, the transport security is used to provide confidentiality and integrity for the transmitted messages and to perform the service authentication.</span></span> <span data-ttu-id="3caa8-111">No entanto, a autenticação do cliente é realizada colocando a credencial do cliente diretamente na mensagem.</span><span class="sxs-lookup"><span data-stu-id="3caa8-111">However, the client authentication is performed by putting the client credential directly in the message.</span></span> <span data-ttu-id="3caa8-112">Isso permite que você use qualquer tipo de credencial que seja suportado pelo modo de segurança de mensagem para a autenticação do cliente, mantendo o benefício de desempenho do modo de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="3caa8-112">This allows you to use any credential type that is supported by the message security mode for the client authentication while keeping the performance benefit of transport security mode.</span></span>  
  
 <span data-ttu-id="3caa8-113">Nesta amostra, `UserName` um tipo de credencial é usado para autenticar o cliente ao serviço.</span><span class="sxs-lookup"><span data-stu-id="3caa8-113">In this sample, a `UserName` credential type is used to authenticate the client to the service.</span></span>  
  
 <span data-ttu-id="3caa8-114">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="3caa8-114">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="3caa8-115">A `wsHttpBinding` vinculação é especificada e configurada nos arquivos de configuração do aplicativo para o cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="3caa8-115">The `wsHttpBinding` binding is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3caa8-116">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="3caa8-116">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3caa8-117">O código do programa na amostra é quase idêntico ao do serviço [Getting Started.](../../../../docs/framework/wcf/samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="3caa8-117">The program code in the sample is almost identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="3caa8-118">Há uma operação adicional fornecida pelo `GetCallerIdentity`contrato de serviço - .</span><span class="sxs-lookup"><span data-stu-id="3caa8-118">There is one additional operation provided by the service contract - `GetCallerIdentity`.</span></span> <span data-ttu-id="3caa8-119">Esta operação retorna o nome da identidade do chamador para o chamador.</span><span class="sxs-lookup"><span data-stu-id="3caa8-119">This operation returns the name of the caller's identity to the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="3caa8-120">Você deve criar um certificado e atribuí-lo usando o Assistente de Certificado do Servidor Web antes de construir e executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="3caa8-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="3caa8-121">A definição de ponto final e a `TransportWithMessageCredential` definição de vinculação nas configurações do arquivo de configuração permitem o modo de segurança, conforme mostrado na configuração de exemplo a seguir para o cliente.</span><span class="sxs-lookup"><span data-stu-id="3caa8-121">The endpoint definition and binding definition in the configuration file settings enable `TransportWithMessageCredential` security mode, as shown in the following sample configuration for the client.</span></span>  
  
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
  
 <span data-ttu-id="3caa8-122">O endereço especificado usa o esquema https://.</span><span class="sxs-lookup"><span data-stu-id="3caa8-122">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="3caa8-123">A configuração de vinculação define o modo de segurança para `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="3caa8-123">The binding configuration sets the security mode to `TransportWithMessageCredential`.</span></span> <span data-ttu-id="3caa8-124">O mesmo modo de segurança deve ser especificado no arquivo Web.config do serviço.</span><span class="sxs-lookup"><span data-stu-id="3caa8-124">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="3caa8-125">Como o certificado usado nesta amostra é um certificado de teste criado com o Makecert.exe, um `https://localhost/servicemodelsamples/service.svc`alerta de segurança aparece quando você tenta acessar um endereço https: como , do seu navegador.</span><span class="sxs-lookup"><span data-stu-id="3caa8-125">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as  `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span> <span data-ttu-id="3caa8-126">Para permitir que o cliente WCF trabalhe com um certificado de teste em vigor, algum código adicional foi adicionado ao cliente para suprimir o alerta de segurança.</span><span class="sxs-lookup"><span data-stu-id="3caa8-126">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="3caa8-127">Este código, e a classe de acompanhamento, não é necessário ao usar certificados de produção.</span><span class="sxs-lookup"><span data-stu-id="3caa8-127">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 <span data-ttu-id="3caa8-128">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="3caa8-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3caa8-129">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="3caa8-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3caa8-130">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3caa8-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3caa8-131">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3caa8-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3caa8-132">Certifique-se de que você tenha realizado as Instruções de Instalação do [Certificado de Servidor do Serviço de Informações da Internet (IIS).](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)</span><span class="sxs-lookup"><span data-stu-id="3caa8-132">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
3. <span data-ttu-id="3caa8-133">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3caa8-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="3caa8-134">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3caa8-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
