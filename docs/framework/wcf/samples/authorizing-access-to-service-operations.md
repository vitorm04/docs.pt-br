---
title: Autorizando o acesso às operações de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: b38134c901e1058e966d217e9b673083e45803c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716604"
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="fef40-102">Autorizando o acesso às operações de serviço</span><span class="sxs-lookup"><span data-stu-id="fef40-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="fef40-103">Este exemplo demonstra como usar o [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para habilitar o uso do <xref:System.Security.Permissions.PrincipalPermissionAttribute> atributo para autorizar o acesso a operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="fef40-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="fef40-104">Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="fef40-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="fef40-105">O serviço e o cliente são configurados usando o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="fef40-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="fef40-106">O `mode` atributo do [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) foi definido como `Message` e `clientCredentialType` foi definido como `Windows`.</span><span class="sxs-lookup"><span data-stu-id="fef40-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="fef40-107">O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é aplicado a cada método de serviço e usado para restringir o acesso a cada operação.</span><span class="sxs-lookup"><span data-stu-id="fef40-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="fef40-108">O chamador deve ser um administrador do Windows para acessar cada operação.</span><span class="sxs-lookup"><span data-stu-id="fef40-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="fef40-109">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="fef40-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fef40-110">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="fef40-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fef40-111">O arquivo de configuração de serviço usa o [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para definir o `principalPermissionMode` atributo:</span><span class="sxs-lookup"><span data-stu-id="fef40-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
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
  
 <span data-ttu-id="fef40-112">Definindo o `principalPermissionMode` à `UseWindowsGroups` permite o uso de <xref:System.Security.Permissions.PrincipalPermissionAttribute> com base em nomes de grupo do Windows.</span><span class="sxs-lookup"><span data-stu-id="fef40-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="fef40-113">O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é aplicado a cada operação para exigir que o chamador a fazer parte do grupo de administradores do Windows, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fef40-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="fef40-114">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="fef40-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fef40-115">O cliente com êxito se comunica com cada operação se ele estiver em execução em uma conta que faz parte do grupo Administradores; Caso contrário, o acesso foi negado.</span><span class="sxs-lookup"><span data-stu-id="fef40-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="fef40-116">Para fazer experiências com falha de autorização, execute o cliente em uma conta que não é parte do grupo Administradores.</span><span class="sxs-lookup"><span data-stu-id="fef40-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="fef40-117">Pressione ENTER na janela do console para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="fef40-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="fef40-118">Um serviço pode ser notificado das falhas de autorização com a implementação de um <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="fef40-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="fef40-119">Ver [estendendo o controle sobre o tratamento de erros e emissão de relatórios](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) para obter informações sobre como implementar `IErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="fef40-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fef40-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="fef40-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fef40-121">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fef40-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="fef40-122">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fef40-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="fef40-123">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fef40-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fef40-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fef40-124">See also</span></span>
