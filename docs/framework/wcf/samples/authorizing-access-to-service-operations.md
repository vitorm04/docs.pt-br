---
title: Autorizando o acesso às operações de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: a0ea82c876b3bd8c2a3218f84399fbb69e1d0080
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932504"
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="1b319-102">Autorizando o acesso às operações de serviço</span><span class="sxs-lookup"><span data-stu-id="1b319-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="1b319-103">Este exemplo demonstra como usar o [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) de Service Authorização para habilitar o uso do <xref:System.Security.Permissions.PrincipalPermissionAttribute> atributo para autorizar o acesso a operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="1b319-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="1b319-104">Este exemplo é baseado no exemplo de [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="1b319-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="1b319-105">O serviço e o cliente são configurados usando o [ \<> de WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1b319-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="1b319-106">O `mode` `Message` atributo `Windows` `clientCredentialType` [ do>desegurançafoidefinidocomoe\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) foi definido como.</span><span class="sxs-lookup"><span data-stu-id="1b319-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="1b319-107">O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é aplicado a cada método de serviço e usado para restringir o acesso a cada operação.</span><span class="sxs-lookup"><span data-stu-id="1b319-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="1b319-108">O chamador deve ser um administrador do Windows para acessar cada operação.</span><span class="sxs-lookup"><span data-stu-id="1b319-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="1b319-109">Neste exemplo, o cliente é um aplicativo de console (. exe) e o serviço é hospedado pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="1b319-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b319-110">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="1b319-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1b319-111">O arquivo de configuração de serviço usa a [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) de Service Authorização `principalPermissionMode` para definir o atributo:</span><span class="sxs-lookup"><span data-stu-id="1b319-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
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
  
 <span data-ttu-id="1b319-112">Definir o `principalPermissionMode` para `UseWindowsGroups` permite o uso do <xref:System.Security.Permissions.PrincipalPermissionAttribute> com base em nomes de grupo do Windows.</span><span class="sxs-lookup"><span data-stu-id="1b319-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="1b319-113">O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é aplicado a cada operação para exigir que o chamador faça parte do grupo de administradores do Windows, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1b319-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="1b319-114">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="1b319-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1b319-115">O cliente se comunicará com êxito com cada operação se estiver sendo executado sob uma conta que faz parte do grupo de administradores; caso contrário, o acesso será negado.</span><span class="sxs-lookup"><span data-stu-id="1b319-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="1b319-116">Para experimentar a falha de autorização, execute o cliente em uma conta que não faça parte do grupo de administradores.</span><span class="sxs-lookup"><span data-stu-id="1b319-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="1b319-117">Pressione ENTER na janela do console para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="1b319-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="1b319-118">Um serviço pode ser notificado de falhas de autorização implementando um <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="1b319-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="1b319-119">Consulte [ampliando o controle sobre tratamento de erros e relatórios](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) para `IErrorHandler`obter informações sobre como implementar o.</span><span class="sxs-lookup"><span data-stu-id="1b319-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1b319-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1b319-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1b319-121">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1b319-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1b319-122">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1b319-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1b319-123">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1b319-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
