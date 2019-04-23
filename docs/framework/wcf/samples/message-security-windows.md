---
title: Segurança de mensagens do Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: eed16f6231717119b30003451cef5eb54016678c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772590"
---
# <a name="message-security-windows"></a><span data-ttu-id="5c064-102">Segurança de mensagens do Windows</span><span class="sxs-lookup"><span data-stu-id="5c064-102">Message Security Windows</span></span>
<span data-ttu-id="5c064-103">Este exemplo demonstra como configurar um <xref:System.ServiceModel.WSHttpBinding> associação para usar segurança em nível de mensagem com a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="5c064-103">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="5c064-104">Este exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5c064-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="5c064-105">Neste exemplo, o serviço está hospedado no Internet Information Services (IIS) e o cliente é um aplicativo de console (.exe).</span><span class="sxs-lookup"><span data-stu-id="5c064-105">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c064-106">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5c064-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5c064-107">A segurança padrão para o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) é a segurança de mensagem usando a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="5c064-107">The default security for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="5c064-108">Neste exemplo, os arquivos de configuração definido explicitamente o `mode` atributo do [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) para `Message` e o `clientCredentialType` atributo `Windows`.</span><span class="sxs-lookup"><span data-stu-id="5c064-108">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="5c064-109">Esses valores são os valores padrão para essa associação, mas eles foram explicitamente configurados, conforme mostrado na seguinte configuração de exemplo para demonstrar seu uso.</span><span class="sxs-lookup"><span data-stu-id="5c064-109">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding>  
            <security mode="Message">  
                <message clientCredentialType="Windows"/>  
            </security>  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="5c064-110">A configuração do ponto de extremidade cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="5c064-110">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="5c064-111">A associação de cliente é configurado com os devidos `securityMode` e `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="5c064-111">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
            "http://localhost/servicemodelsamples/service.svc"   
            binding="wsHttpBinding"   
            bindingConfiguration="Binding1"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- The default security for the WSHttpBinding is -->  
      <!-- Message security using Windows authentication. -->  
      <!-- This configuration explicitly defines the security mode -->  
      <!-- as Message and the clientCredentialType as Windows -->  
      <!-- for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5c064-112">O código-fonte de serviço foi modificado para demonstrar como o <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> pode ser usado para acessar a identidade do chamador.</span><span class="sxs-lookup"><span data-stu-id="5c064-112">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="5c064-113">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="5c064-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5c064-114">O primeiro método chamado - `GetCallerIdentity` -retorna o nome da identidade do chamador para o cliente.</span><span class="sxs-lookup"><span data-stu-id="5c064-114">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="5c064-115">Pressione ENTER na janela do console para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="5c064-115">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5c064-116">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5c064-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5c064-117">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5c064-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5c064-118">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5c064-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5c064-119">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5c064-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
