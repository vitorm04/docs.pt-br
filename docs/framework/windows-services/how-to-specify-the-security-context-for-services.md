---
title: 'Como: Especificar o contexto de segurança para serviços'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
author: ghogen
ms.openlocfilehash: 88dc9c40a2b8ff0ac9bba26c991ba2a4ac2dcb43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952432"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="37b22-102">Como: Especificar o contexto de segurança para serviços</span><span class="sxs-lookup"><span data-stu-id="37b22-102">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="37b22-103">Por padrão, os serviços são executados em um contexto de segurança diferente do que o usuário que fez logon.</span><span class="sxs-lookup"><span data-stu-id="37b22-103">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="37b22-104">Os serviços são executados no contexto da conta padrão do sistema, chamada `LocalSystem`, que oferece a eles privilégios de acesso a recursos do sistema diferentes que os do usuário.</span><span class="sxs-lookup"><span data-stu-id="37b22-104">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="37b22-105">Você pode alterar esse comportamento para especificar outra conta de usuário diferente com a qual o serviço deverá ser executado.</span><span class="sxs-lookup"><span data-stu-id="37b22-105">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="37b22-106">Você define o contexto de segurança manipulando a propriedade <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> para o processo no qual o serviço é executado.</span><span class="sxs-lookup"><span data-stu-id="37b22-106">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="37b22-107">Essa propriedade permite que você defina o serviço para uma entre quatro tipos de conta:</span><span class="sxs-lookup"><span data-stu-id="37b22-107">This property allows you to set the service to one of four account types:</span></span>  
  
- <span data-ttu-id="37b22-108">`User`, que faz com que o sistema solicite um nome de usuário e uma senha válidos quando o serviço é instalado e executado no contexto de uma conta especificada por um único usuário na rede;</span><span class="sxs-lookup"><span data-stu-id="37b22-108">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
- <span data-ttu-id="37b22-109">`LocalService`, que é executado no contexto de uma conta que age como um usuário sem privilégios no computador local e apresenta credenciais anônimas para qualquer servidor remoto;</span><span class="sxs-lookup"><span data-stu-id="37b22-109">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
- <span data-ttu-id="37b22-110">`LocalSystem`, que é executado no contexto de uma conta que fornece privilégios locais abrangentes e apresenta as credenciais do computador para qualquer servidor remoto;</span><span class="sxs-lookup"><span data-stu-id="37b22-110">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
- <span data-ttu-id="37b22-111">`NetworkService`, que é executado no contexto de uma conta que age como um usuário sem privilégios no computador local e apresenta as credenciais do computador para qualquer servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="37b22-111">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="37b22-112">Para obter mais informações, consulte a enumeração <xref:System.ServiceProcess.ServiceAccount>.</span><span class="sxs-lookup"><span data-stu-id="37b22-112">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="37b22-113">Para especificar o contexto de segurança de um serviço</span><span class="sxs-lookup"><span data-stu-id="37b22-113">To specify the security context for a service</span></span>  
  
1. <span data-ttu-id="37b22-114">Depois de criar o serviço, adicione os instaladores necessários para ele.</span><span class="sxs-lookup"><span data-stu-id="37b22-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="37b22-115">Para obter mais informações, confira [Como: Adicionar instaladores ao aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="37b22-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="37b22-116">No designer, acesse a classe `ProjectInstaller` e clique no instalador do processo de serviço para o serviço com o qual você está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="37b22-116">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="37b22-117">Para cada aplicativo de serviço, há pelo menos dois componentes de instalação na classe `ProjectInstaller` – um que instala os processos para todos os serviços no projeto e um instalador para cada serviço que o aplicativo contém.</span><span class="sxs-lookup"><span data-stu-id="37b22-117">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="37b22-118">Nesse caso, você desejará selecionar <xref:System.ServiceProcess.ServiceProcessInstaller>.</span><span class="sxs-lookup"><span data-stu-id="37b22-118">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3. <span data-ttu-id="37b22-119">Na janela **Propriedades**, defina a <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> para o valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="37b22-119">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37b22-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37b22-120">See also</span></span>

- [<span data-ttu-id="37b22-121">Introdução aos Aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="37b22-121">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="37b22-122">Como: adicionar instaladores ao aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="37b22-122">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="37b22-123">Como: criar serviços do Windows</span><span class="sxs-lookup"><span data-stu-id="37b22-123">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
