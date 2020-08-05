---
title: Representando e revertendo
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
ms.openlocfilehash: 7eecc7d6cb3fa4cc1c1bd971d36f9d3ca47a7144
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555664"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="5035f-102">Representando e revertendo</span><span class="sxs-lookup"><span data-stu-id="5035f-102">Impersonating and Reverting</span></span>

> [!NOTE]
> <span data-ttu-id="5035f-103">Este artigo aplica-se ao Windows.</span><span class="sxs-lookup"><span data-stu-id="5035f-103">This article applies to Windows.</span></span>
>
> <span data-ttu-id="5035f-104">Para obter informações sobre ASP.NET Core, consulte [segurança do ASP.NET Core](/aspnet/core/security/).</span><span class="sxs-lookup"><span data-stu-id="5035f-104">For information about ASP.NET Core, see [ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="5035f-105">Às vezes, talvez seja necessário obter um token de conta do Windows para representar uma conta do Windows.</span><span class="sxs-lookup"><span data-stu-id="5035f-105">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="5035f-106">Por exemplo, seu aplicativo baseado em ASP.NET pode ter que agir em nome de vários usuários em momentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="5035f-106">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="5035f-107">Seu aplicativo pode aceitar um token que representa um administrador do Serviços de Informações da Internet (IIS), representar esse usuário, executar uma operação e reverter para a identidade anterior.</span><span class="sxs-lookup"><span data-stu-id="5035f-107">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="5035f-108">Em seguida, ele pode aceitar um token do IIS que representa um usuário com menos direitos, executar alguma operação e reverter novamente.</span><span class="sxs-lookup"><span data-stu-id="5035f-108">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="5035f-109">Em situações em que o aplicativo deve representar uma conta do Windows que não foi anexada ao thread atual pelo IIS, você deve recuperar o token dessa conta e usá-lo para ativar a conta.</span><span class="sxs-lookup"><span data-stu-id="5035f-109">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="5035f-110">Você pode fazer isso executando as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="5035f-110">You can do this by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="5035f-111">Recuperar um token de conta para um usuário específico fazendo uma chamada para o método **LogonUser** não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5035f-111">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="5035f-112">Esse método não está na biblioteca de classes base do .NET, mas está localizado no **advapi32.dll**não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5035f-112">This method is not in the .NET base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="5035f-113">O acesso a métodos em código não gerenciado é uma operação avançada e está além do escopo desta discussão.</span><span class="sxs-lookup"><span data-stu-id="5035f-113">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="5035f-114">Para obter mais informações, consulte [interoperação com código não gerenciado](../../framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="5035f-114">For more information, see [Interoperating with Unmanaged Code](../../framework/interop/index.md).</span></span> <span data-ttu-id="5035f-115">Para obter mais informações sobre o método **LogonUser** e **advapi32.dll**, consulte a documentação do Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="5035f-115">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2. <span data-ttu-id="5035f-116">Crie uma nova instância da classe **WindowsIdentity** , passando o token.</span><span class="sxs-lookup"><span data-stu-id="5035f-116">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="5035f-117">O código a seguir demonstra essa chamada, onde `hToken` representa um token do Windows.</span><span class="sxs-lookup"><span data-stu-id="5035f-117">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. <span data-ttu-id="5035f-118">Comece a representação criando uma nova instância da <xref:System.Security.Principal.WindowsImpersonationContext> classe e inicializando-a com o <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> método da classe inicializada, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5035f-118">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. <span data-ttu-id="5035f-119">Quando você não precisar mais representar, chame o <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> método para reverter a representação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5035f-119">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="5035f-120">Se o código confiável já tiver anexado um <xref:System.Security.Principal.WindowsPrincipal> objeto ao thread, você poderá chamar o método de instância **Impersonate**, que não assume um token de conta.</span><span class="sxs-lookup"><span data-stu-id="5035f-120">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="5035f-121">Observe que isso só é útil quando o objeto **WindowsPrincipal** no thread representa um usuário diferente daquele no qual o processo está em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="5035f-121">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="5035f-122">Por exemplo, você pode encontrar essa situação usando o ASP.NET com a autenticação do Windows ativada e a representação desativada.</span><span class="sxs-lookup"><span data-stu-id="5035f-122">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="5035f-123">Nesse caso, o processo é executado em uma conta configurada no Serviços de Informações da Internet (IIS), enquanto a entidade atual representa o usuário do Windows que está acessando a página.</span><span class="sxs-lookup"><span data-stu-id="5035f-123">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="5035f-124">Observe que nem **Impersonate** nem **Undo** altera o objeto **principal** ( <xref:System.Security.Principal.IPrincipal> ) associado ao contexto de chamada atual.</span><span class="sxs-lookup"><span data-stu-id="5035f-124">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="5035f-125">Em vez disso, a representação e a reversão alteram o token associado ao processo do sistema operacional atual.</span><span class="sxs-lookup"><span data-stu-id="5035f-125">Rather, impersonation and reverting change the token associated with the current operating system process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5035f-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="5035f-126">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [<span data-ttu-id="5035f-127">Objetos Principal e Identity</span><span class="sxs-lookup"><span data-stu-id="5035f-127">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="5035f-128">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="5035f-128">Interoperating with Unmanaged Code</span></span>](../../framework/interop/index.md)
- [<span data-ttu-id="5035f-129">Segurança de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5035f-129">ASP.NET Core Security</span></span>](/aspnet/core/security/)
