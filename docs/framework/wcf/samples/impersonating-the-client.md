---
title: Representando o cliente
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 10a8d243b3f053879f183864e955d9260c07865b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183605"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="2bb89-102">Representando o cliente</span><span class="sxs-lookup"><span data-stu-id="2bb89-102">Impersonating the Client</span></span>
<span data-ttu-id="2bb89-103">A amostra de personificação demonstra como se passar pelo aplicativo de chamada no serviço para que o serviço possa acessar os recursos do sistema em nome do chamador.</span><span class="sxs-lookup"><span data-stu-id="2bb89-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="2bb89-104">Esta amostra é baseada na amostra [self-host.](../../../../docs/framework/wcf/samples/self-host.md)</span><span class="sxs-lookup"><span data-stu-id="2bb89-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="2bb89-105">Os arquivos de configuração de serviço e cliente são os mesmos da amostra [Self-Host.](../../../../docs/framework/wcf/samples/self-host.md)</span><span class="sxs-lookup"><span data-stu-id="2bb89-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bb89-106">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="2bb89-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2bb89-107">O código de serviço foi `Add` modificado de modo que o <xref:System.ServiceModel.OperationBehaviorAttribute> método no serviço se passa pelo chamador usando o conforme mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="2bb89-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="2bb89-108">Como resultado, o contexto de segurança do segmento de execução `Add` é alterado para se passar pelo chamador antes de inserir o método e revertido ao sair do método.</span><span class="sxs-lookup"><span data-stu-id="2bb89-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="2bb89-109">O `DisplayIdentityInformation` método mostrado no código de amostra a seguir é uma função de utilidade que exibe a identidade do chamador.</span><span class="sxs-lookup"><span data-stu-id="2bb89-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="2bb89-110">O `Subtract` método no serviço personifica o chamador usando chamadas imperativas, conforme mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="2bb89-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="2bb89-111">Observe que, neste caso, o chamador não é personificado para toda a chamada, mas é apenas personificado por uma parte da chamada.</span><span class="sxs-lookup"><span data-stu-id="2bb89-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="2bb89-112">Em geral, representar-se para o menor escopo é preferível se passar por toda a operação.</span><span class="sxs-lookup"><span data-stu-id="2bb89-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="2bb89-113">Os outros métodos não se passam pelo interlocutor.</span><span class="sxs-lookup"><span data-stu-id="2bb89-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="2bb89-114">O código do cliente foi modificado para <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>definir o nível de representação para .</span><span class="sxs-lookup"><span data-stu-id="2bb89-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="2bb89-115">O cliente especifica o nível de personificação a ser <xref:System.Security.Principal.TokenImpersonationLevel> usado pelo serviço, usando a enumeração.</span><span class="sxs-lookup"><span data-stu-id="2bb89-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="2bb89-116">A enumeração suporta os <xref:System.Security.Principal.TokenImpersonationLevel.None>seguintes <xref:System.Security.Principal.TokenImpersonationLevel.Identification> <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> valores: , <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, e <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span><span class="sxs-lookup"><span data-stu-id="2bb89-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="2bb89-117">Para realizar uma verificação de acesso ao acessar um recurso do sistema na máquina local que está <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>protegido usando ACLs do Windows, o nível de representação deve ser definido para , como mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="2bb89-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="2bb89-118">Quando você executa a amostra, as solicitações e respostas da operação são exibidas nas janelas do serviço e do console cliente.</span><span class="sxs-lookup"><span data-stu-id="2bb89-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="2bb89-119">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="2bb89-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bb89-120">O serviço deve ser executado uma conta administrativa ou a `http://localhost:8000/ServiceModelSamples` conta a que ele é executado deve ser concedido o direito de registrar o URI com a camada HTTP.</span><span class="sxs-lookup"><span data-stu-id="2bb89-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="2bb89-121">Esses direitos podem ser concedidos configurando uma [Reserva de Namespace](/windows/win32/http/namespace-reservations-registrations-and-routing) usando a [ferramenta Httpcfg.exe](/windows/win32/http/httpcfg-exe).</span><span class="sxs-lookup"><span data-stu-id="2bb89-121">Such rights can be granted by setting up a [Namespace Reservation](/windows/win32/http/namespace-reservations-registrations-and-routing) using the [Httpcfg.exe tool](/windows/win32/http/httpcfg-exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bb89-122">Nos computadores que executam o Windows Server 2003, a representação só é suportada se o aplicativo Host.exe tiver o privilégio de personificação.</span><span class="sxs-lookup"><span data-stu-id="2bb89-122">On computers running Windows Server 2003, impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="2bb89-123">(Por padrão, apenas os administradores têm essa permissão.) Para adicionar esse privilégio a uma conta que o serviço está executando, vá para **Ferramentas Administrativas,** abra **a Política de Segurança Local,** abra **políticas locais,** clique em **Atribuição de Direitos do Usuário**e **selecione Personificar um Cliente após autenticação** e clique duas vezes **em Propriedades** para adicionar um usuário ou grupo.</span><span class="sxs-lookup"><span data-stu-id="2bb89-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2bb89-124">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="2bb89-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2bb89-125">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2bb89-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2bb89-126">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2bb89-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2bb89-127">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2bb89-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="2bb89-128">Para demonstrar que o serviço se passa pelo chamador, execute o cliente em uma conta diferente da que o serviço está executando.</span><span class="sxs-lookup"><span data-stu-id="2bb89-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="2bb89-129">Para isso, no prompt de comando, digite:</span><span class="sxs-lookup"><span data-stu-id="2bb89-129">To do so, at the command prompt, type:</span></span>  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="2bb89-130">Em seguida, você é solicitado para uma senha.</span><span class="sxs-lookup"><span data-stu-id="2bb89-130">You are then prompted for a password.</span></span> <span data-ttu-id="2bb89-131">Digite a senha da conta que você especificou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2bb89-131">Enter the password for the account you previously specified.</span></span>  
  
5. <span data-ttu-id="2bb89-132">Quando executar o cliente, anote a identidade antes e depois de executá-la com diferentes credenciais.</span><span class="sxs-lookup"><span data-stu-id="2bb89-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
