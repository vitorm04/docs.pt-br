---
title: Representando e revertendo
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97b15ea2202ca410dd517db63a7145d27f62bb48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018587"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="5c6b2-102">Representando e revertendo</span><span class="sxs-lookup"><span data-stu-id="5c6b2-102">Impersonating and Reverting</span></span>
<span data-ttu-id="5c6b2-103">Às vezes, talvez seja necessário obter um token de conta do Windows para representar uma conta do Windows.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-103">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="5c6b2-104">Por exemplo, seu aplicativo baseado no ASP.NET pode ter que atuar em nome de vários usuários em momentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-104">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="5c6b2-105">Seu aplicativo pode aceitar um token que representa um administrador de serviços de informações da Internet (IIS), representar o usuário, executar uma operação e reverter para a identidade anterior.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-105">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="5c6b2-106">Em seguida, ele pode aceitar um token do IIS que representa um usuário com poucos direitos, executar alguma operação e reverter novamente.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-106">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="5c6b2-107">Em situações em que seu aplicativo deve representar uma conta do Windows que não foi anexada ao thread atual pelo IIS, você deve recuperar o token dessa conta e usá-lo para ativar a conta.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-107">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="5c6b2-108">Você pode fazer isso executando as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="5c6b2-108">You can do this by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="5c6b2-109">Recuperar um token de conta para um usuário específico, fazendo uma chamada não gerenciado **LogonUser** método.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-109">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="5c6b2-110">Esse método não está na biblioteca de classes base do .NET Framework, mas está localizado no não gerenciado **advapi32.dll**.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-110">This method is not in the .NET Framework base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="5c6b2-111">Acessando os métodos no código não gerenciado é uma operação avançada e está além do escopo desta discussão.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-111">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="5c6b2-112">Para obter mais informações, consulte [interoperação com código não gerenciado](../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="5c6b2-112">For more information, see [Interoperating with Unmanaged Code](../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="5c6b2-113">Para obter mais informações sobre o **LogonUser** método e **advapi32.dll**, consulte a documentação do SDK da plataforma.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-113">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2. <span data-ttu-id="5c6b2-114">Criar uma nova instância dos **WindowsIdentity** classe, passando o token.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-114">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="5c6b2-115">O código a seguir demonstra essa chamada, onde `hToken` representa um token do Windows.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-115">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. <span data-ttu-id="5c6b2-116">Comece a criar uma nova instância da representação de <xref:System.Security.Principal.WindowsImpersonationContext> classe e inicializá-la com o <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> método da classe inicializada, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-116">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. <span data-ttu-id="5c6b2-117">Quando você não precisa representar, chame o <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> método para reverter a representação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-117">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="5c6b2-118">Se confiável código já anexou um <xref:System.Security.Principal.WindowsPrincipal> do objeto para o thread, você pode chamar o método de instância **Impersonate**, que não utilize um token de conta.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-118">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="5c6b2-119">Observe que isso é útil somente quando o **WindowsPrincipal** objeto no thread representa um usuário diferente em que o processo está em execução atualmente.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-119">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="5c6b2-120">Por exemplo, você pode encontrar essa situação usando o ASP.NET com autenticação de Windows ativado e desativado de representação.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-120">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="5c6b2-121">Nesse caso, o processo está em execução em uma conta configurada em serviços de informações da Internet (IIS), enquanto a entidade atual representa o usuário do Windows que está acessando a página.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-121">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="5c6b2-122">Observe que nem **Impersonate** nem **desfazer** alterações a **Principal** objeto (<xref:System.Security.Principal.IPrincipal>) associado com o contexto de chamada atual.</span><span class="sxs-lookup"><span data-stu-id="5c6b2-122">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="5c6b2-123">Em vez disso, representação e alteração Revertendo o token associado com o processo de sistema operacional atual...</span><span class="sxs-lookup"><span data-stu-id="5c6b2-123">Rather, impersonation and reverting change the token associated with the current operating system process..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c6b2-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c6b2-124">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [<span data-ttu-id="5c6b2-125">Objetos Principal e Identity</span><span class="sxs-lookup"><span data-stu-id="5c6b2-125">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
- [<span data-ttu-id="5c6b2-126">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="5c6b2-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
