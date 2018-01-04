---
title: "Segurança de mensagens do Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
caps.latest.revision: "34"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c8bb8d0506dd535a312bd8df8954c8143d9543ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-windows"></a><span data-ttu-id="4d8c3-102">Segurança de mensagens do Windows</span><span class="sxs-lookup"><span data-stu-id="4d8c3-102">Message Security Windows</span></span>
<span data-ttu-id="4d8c3-103">Este exemplo demonstra como configurar um <xref:System.ServiceModel.WSHttpBinding> associação para usar a segurança de nível de mensagem com a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="4d8c3-103">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="4d8c3-104">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4d8c3-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="4d8c3-105">Neste exemplo, o serviço é hospedado no Internet Information Services (IIS) e o cliente é um aplicativo de console (.exe).</span><span class="sxs-lookup"><span data-stu-id="4d8c3-105">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d8c3-106">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4d8c3-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4d8c3-107">A segurança padrão para o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) é a segurança de mensagem usando a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="4d8c3-107">The default security for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="4d8c3-108">Neste exemplo, os arquivos de configuração definido explicitamente o `mode` atributo do [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) para `Message` e `clientCredentialType` atributo `Windows`.</span><span class="sxs-lookup"><span data-stu-id="4d8c3-108">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="4d8c3-109">Esses valores são os valores padrão para essa associação, mas eles foram explicitamente configurados, como mostrado no seguinte exemplo de configuração para demonstrar o seu uso.</span><span class="sxs-lookup"><span data-stu-id="4d8c3-109">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
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
  
 <span data-ttu-id="4d8c3-110">A configuração do ponto de extremidade cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="4d8c3-110">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="4d8c3-111">A ligação do cliente é configurado com as `securityMode` e `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="4d8c3-111">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
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
      <!--   
      <!--The default security for the WSHttpBinding is-->  
      <!--Message security using Windows authentication. -->  
      <!--This configuration explicitly defines the security mode -->  
      <!--as Message and the clientCredentialType as Windows  -->  
      <!--for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="4d8c3-112">O código de origem do serviço foi modificado para demonstrar como o <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> pode ser usado para acessar a identidade do chamador.</span><span class="sxs-lookup"><span data-stu-id="4d8c3-112">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  
  
```  
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```  
  
 <span data-ttu-id="4d8c3-113">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="4d8c3-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4d8c3-114">O primeiro método chamado - `GetCallerIdentity` -retorna o nome da identidade do chamador ao cliente.</span><span class="sxs-lookup"><span data-stu-id="4d8c3-114">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="4d8c3-115">Pressione ENTER na janela do console para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="4d8c3-115">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4d8c3-116">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4d8c3-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4d8c3-117">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d8c3-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4d8c3-118">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d8c3-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4d8c3-119">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d8c3-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d8c3-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d8c3-120">See Also</span></span>
