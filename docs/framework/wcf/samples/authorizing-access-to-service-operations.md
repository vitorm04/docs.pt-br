---
title: Autorizando o acesso às operações de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: c2ad6977674666ef65df1ea4cfe58cfd4bff8b69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183918"
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="6d533-102">Autorizando o acesso às operações de serviço</span><span class="sxs-lookup"><span data-stu-id="6d533-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="6d533-103">Esta amostra demonstra como usar o <xref:System.Security.Permissions.PrincipalPermissionAttribute> [ \<serviçoAutorização>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para permitir o uso do atributo para autorizar o acesso às operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="6d533-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="6d533-104">Esta amostra é baseada na amostra [Getting Started.](../../../../docs/framework/wcf/samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="6d533-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="6d533-105">O serviço e o cliente são configurados usando o [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6d533-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="6d533-106">O `mode` atributo [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) da>de `Message` `clientCredentialType` segurança foi `Windows`definido e foi definido para .</span><span class="sxs-lookup"><span data-stu-id="6d533-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="6d533-107">O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é aplicado a cada método de serviço e usado para restringir o acesso a cada operação.</span><span class="sxs-lookup"><span data-stu-id="6d533-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="6d533-108">O chamador deve ser um administrador do Windows para acessar cada operação.</span><span class="sxs-lookup"><span data-stu-id="6d533-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="6d533-109">Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="6d533-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d533-110">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="6d533-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6d533-111">O arquivo de configuração do serviço `principalPermissionMode` usa o [ \<serviçoAutorização>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para definir o atributo:</span><span class="sxs-lookup"><span data-stu-id="6d533-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="6d533-112">A `principalPermissionMode` configuração do `UseWindowsGroups` <xref:System.Security.Permissions.PrincipalPermissionAttribute> "para" permite o uso de com base em nomes de grupos do Windows.</span><span class="sxs-lookup"><span data-stu-id="6d533-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="6d533-113">O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é aplicado a cada operação para exigir que o chamador faça parte do grupo de administradores do Windows, conforme mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="6d533-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="6d533-114">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="6d533-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6d533-115">O cliente se comunica com sucesso com cada operação se estiver executando uma conta que faz parte do grupo Administradores; caso contrário, o acesso é negado.</span><span class="sxs-lookup"><span data-stu-id="6d533-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="6d533-116">Para experimentar a falha de autorização, execute o cliente em uma conta que não faz parte do grupo Administradores.</span><span class="sxs-lookup"><span data-stu-id="6d533-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="6d533-117">Pressione ENTER na janela do console para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="6d533-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="6d533-118">Um serviço pode ser notificado de falhas <xref:System.ServiceModel.Dispatcher.IErrorHandler>de autorização implementando um .</span><span class="sxs-lookup"><span data-stu-id="6d533-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="6d533-119">Consulte [Estendendo o controle sobre o manuseio de erros e relatórios](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) para obter informações sobre a implementação `IErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="6d533-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6d533-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="6d533-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6d533-121">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6d533-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6d533-122">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6d533-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6d533-123">Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .</span><span class="sxs-lookup"><span data-stu-id="6d533-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
