---
title: Autorizando o acesso às operações de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 3097c86f50a75dec8a649ca4e1edd2511a046ca8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585526"
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="34062-102">Autorizando o acesso às operações de serviço</span><span class="sxs-lookup"><span data-stu-id="34062-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="34062-103">Este exemplo demonstra como usar o [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) para habilitar o uso do <xref:System.Security.Permissions.PrincipalPermissionAttribute> atributo para autorizar o acesso a operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="34062-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="34062-104">Este exemplo é baseado no exemplo de [introdução](getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="34062-104">This sample is based on the [Getting Started](getting-started-sample.md) sample.</span></span> <span data-ttu-id="34062-105">O serviço e o cliente são configurados usando o [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="34062-105">The service and client are configured using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="34062-106">O `mode` atributo de [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) foi definido como e foi `Message` `clientCredentialType` definido como `Windows` .</span><span class="sxs-lookup"><span data-stu-id="34062-106">The `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="34062-107">O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é aplicado a cada método de serviço e usado para restringir o acesso a cada operação.</span><span class="sxs-lookup"><span data-stu-id="34062-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="34062-108">O chamador deve ser um administrador do Windows para acessar cada operação.</span><span class="sxs-lookup"><span data-stu-id="34062-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="34062-109">Neste exemplo, o cliente é um aplicativo de console (. exe) e o serviço é hospedado pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="34062-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34062-110">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="34062-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="34062-111">O arquivo de configuração de serviço usa o [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) para definir o `principalPermissionMode` atributo:</span><span class="sxs-lookup"><span data-stu-id="34062-111">The service configuration file uses the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
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
  
 <span data-ttu-id="34062-112">Definir o `principalPermissionMode` para `UseWindowsGroups` permite o uso do <xref:System.Security.Permissions.PrincipalPermissionAttribute> com base em nomes de grupo do Windows.</span><span class="sxs-lookup"><span data-stu-id="34062-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="34062-113">O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é aplicado a cada operação para exigir que o chamador faça parte do grupo de administradores do Windows, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="34062-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="34062-114">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="34062-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="34062-115">O cliente se comunicará com êxito com cada operação se estiver sendo executado sob uma conta que faz parte do grupo de administradores; caso contrário, o acesso será negado.</span><span class="sxs-lookup"><span data-stu-id="34062-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="34062-116">Para experimentar a falha de autorização, execute o cliente em uma conta que não faça parte do grupo de administradores.</span><span class="sxs-lookup"><span data-stu-id="34062-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="34062-117">Pressione ENTER na janela do console para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="34062-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="34062-118">Um serviço pode ser notificado de falhas de autorização implementando um <xref:System.ServiceModel.Dispatcher.IErrorHandler> .</span><span class="sxs-lookup"><span data-stu-id="34062-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="34062-119">Consulte [ampliando o controle sobre tratamento de erros e relatórios](extending-control-over-error-handling-and-reporting.md) para obter informações sobre como implementar o `IErrorHandler` .</span><span class="sxs-lookup"><span data-stu-id="34062-119">See [Extending Control Over Error Handling and Reporting](extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="34062-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="34062-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="34062-121">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="34062-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="34062-122">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="34062-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="34062-123">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="34062-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
