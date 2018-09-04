---
title: Representando o cliente
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 5a13ab73e48616b38e583b1c9948fc1bf5eb8a64
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43522282"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="ea25d-102">Representando o cliente</span><span class="sxs-lookup"><span data-stu-id="ea25d-102">Impersonating the Client</span></span>
<span data-ttu-id="ea25d-103">O exemplo representação demonstra como representar o aplicativo do chamador no serviço para que o serviço possa acessar recursos do sistema em nome do chamador.</span><span class="sxs-lookup"><span data-stu-id="ea25d-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="ea25d-104">Este exemplo se baseia a [auto-hospedar](../../../../docs/framework/wcf/samples/self-host.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="ea25d-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="ea25d-105">Os arquivos de configuração do cliente e de serviço são os mesmos que o [auto-hospedar](../../../../docs/framework/wcf/samples/self-host.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="ea25d-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea25d-106">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ea25d-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ea25d-107">O código de serviço tiver sido modificado, de modo que o `Add` método no serviço representará o chamador usando a <xref:System.ServiceModel.OperationBehaviorAttribute> conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ea25d-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    Console.WriteLine("Received Add({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="ea25d-108">Como resultado, o contexto de segurança do thread em execução é alternado para representar o chamador antes de inserir o `Add` método e revertidas em saindo do método.</span><span class="sxs-lookup"><span data-stu-id="ea25d-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="ea25d-109">O `DisplayIdentityInformation` método mostrado no código de exemplo a seguir é uma função de utilitário que exibe a identidade do chamador.</span><span class="sxs-lookup"><span data-stu-id="ea25d-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tThread Identity            :{0}",  
         WindowsIdentity.GetCurrent().Name);  
    Console.WriteLine("\t\tThread Identity level  :{0}",   
         WindowsIdentity.GetCurrent().ImpersonationLevel);  
    Console.WriteLine("\t\thToken                     :{0}",  
         WindowsIdentity.GetCurrent().Token.ToString());  
    return;  
}  
```  
  
 <span data-ttu-id="ea25d-110">O `Subtract` método no serviço representará o chamador usando chamadas imperativas, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ea25d-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
```  
public double Subtract(double n1, double n2)  
{  
    double result = n1 - n2;  
    Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
Console.WriteLine("Before impersonating");  
DisplayIdentityInformation();  
  
    if (ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Impersonation ||  
        ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Delegation)  
    {  
        // Impersonate.  
        using (ServiceSecurityContext.Current.WindowsIdentity.Impersonate())  
        {  
            // Make a system call in the caller's context and ACLs   
            // on the system resource are enforced in the caller's context.   
            Console.WriteLine("Impersonating the caller imperatively");  
            DisplayIdentityInformation();  
        }  
    }  
    else  
    {  
        Console.WriteLine("ImpersonationLevel is not high enough to perform this operation.");  
    }  
  
Console.WriteLine("After reverting");  
DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="ea25d-111">Observe que nesse caso, o chamador não é representado para a chamada inteira, mas só é representado por uma parte da chamada.</span><span class="sxs-lookup"><span data-stu-id="ea25d-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="ea25d-112">Em geral, a representação para o menor escopo é preferível representando toda a operação.</span><span class="sxs-lookup"><span data-stu-id="ea25d-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="ea25d-113">Os outros métodos não representam o chamador.</span><span class="sxs-lookup"><span data-stu-id="ea25d-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="ea25d-114">O código do cliente foi modificado para definir a representação como <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span><span class="sxs-lookup"><span data-stu-id="ea25d-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="ea25d-115">O cliente especifica o nível de representação a ser usado pelo serviço, usando o <xref:System.Security.Principal.TokenImpersonationLevel> enumeração.</span><span class="sxs-lookup"><span data-stu-id="ea25d-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="ea25d-116">A enumeração suporta os seguintes valores: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> e <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span><span class="sxs-lookup"><span data-stu-id="ea25d-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="ea25d-117">Para executar uma verificação de acesso ao acessar um recurso do sistema no computador local que é protegido usando ACLs do Windows, o nível de representação deve ser definido como <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ea25d-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="ea25d-118">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas nas janelas do console de serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="ea25d-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ea25d-119">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="ea25d-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea25d-120">O serviço deve executar em uma conta administrativa ou a conta em que ele é executado deve ter direitos para registrar o http://localhost:8000/ServiceModelSamples URI com a camada HTTP.</span><span class="sxs-lookup"><span data-stu-id="ea25d-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the http://localhost:8000/ServiceModelSamples URI with the HTTP layer.</span></span> <span data-ttu-id="ea25d-121">Tais direitos podem ser concedidos ao configurar uma [reserva do Namespace](https://go.microsoft.com/fwlink/?LinkId=95012) usando o [Httpcfg.exe ferramenta](https://go.microsoft.com/fwlink/?LinkId=95010).</span><span class="sxs-lookup"><span data-stu-id="ea25d-121">Such rights can be granted by setting up a [Namespace Reservation](https://go.microsoft.com/fwlink/?LinkId=95012) using the [Httpcfg.exe tool](https://go.microsoft.com/fwlink/?LinkId=95010).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea25d-122">Em computadores que executam [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], a representação tem suporte apenas se o aplicativo Host.exe tem o privilégio de representação.</span><span class="sxs-lookup"><span data-stu-id="ea25d-122">On computers running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="ea25d-123">(Por padrão, somente os administradores têm essa permissão). Para adicionar esse privilégio a uma conta de serviço está em execução como, vá para **ferramentas administrativas**, abra **política de segurança Local**, abra **políticas locais**, clique em **Atribuição de direitos de usuário**e selecione **representar um cliente após autenticação** e clique duas vezes em **propriedades** para adicionar um usuário ou grupo.</span><span class="sxs-lookup"><span data-stu-id="ea25d-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ea25d-124">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ea25d-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ea25d-125">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea25d-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ea25d-126">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea25d-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ea25d-127">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea25d-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="ea25d-128">Para demonstrar que o serviço representará o chamador, execute o cliente em uma conta diferente daquela que o serviço está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="ea25d-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="ea25d-129">Para fazer isso, no prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="ea25d-129">To do so, at the command prompt, type:</span></span>  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="ea25d-130">Em seguida, você será solicitado para uma senha.</span><span class="sxs-lookup"><span data-stu-id="ea25d-130">You are then prompted for a password.</span></span> <span data-ttu-id="ea25d-131">Insira a senha para a conta especificada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ea25d-131">Enter the password for the account you previously specified.</span></span>  
  
5.  <span data-ttu-id="ea25d-132">Quando você executa o cliente, observe a identidade de antes e depois da execução com credenciais diferentes.</span><span class="sxs-lookup"><span data-stu-id="ea25d-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea25d-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea25d-133">See Also</span></span>
