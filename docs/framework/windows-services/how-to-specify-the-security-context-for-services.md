---
title: 'Como: Especificar o contexto de segurança para serviços'
description: Especifique o contexto de segurança para serviços. Os serviços executados no contexto de conta do sistema padrão têm outros direitos de acesso de recurso do sistema do que o usuário conectado.
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
ms.openlocfilehash: 4ed531cb520a781fd38f8bf5491da6948901a1d5
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925729"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="260b1-104">Como: Especificar o contexto de segurança para serviços</span><span class="sxs-lookup"><span data-stu-id="260b1-104">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="260b1-105">Por padrão, os serviços são executados em um contexto de segurança diferente do que o usuário que fez logon.</span><span class="sxs-lookup"><span data-stu-id="260b1-105">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="260b1-106">Os serviços são executados no contexto da conta padrão do sistema, chamada `LocalSystem`, que oferece a eles privilégios de acesso a recursos do sistema diferentes que os do usuário.</span><span class="sxs-lookup"><span data-stu-id="260b1-106">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="260b1-107">Você pode alterar esse comportamento para especificar outra conta de usuário diferente com a qual o serviço deverá ser executado.</span><span class="sxs-lookup"><span data-stu-id="260b1-107">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="260b1-108">Você define o contexto de segurança manipulando a propriedade <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> para o processo no qual o serviço é executado.</span><span class="sxs-lookup"><span data-stu-id="260b1-108">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="260b1-109">Essa propriedade permite que você defina o serviço para uma entre quatro tipos de conta:</span><span class="sxs-lookup"><span data-stu-id="260b1-109">This property allows you to set the service to one of four account types:</span></span>  
  
- <span data-ttu-id="260b1-110">`User`, que faz com que o sistema solicite um nome de usuário e uma senha válidos quando o serviço é instalado e executado no contexto de uma conta especificada por um único usuário na rede;</span><span class="sxs-lookup"><span data-stu-id="260b1-110">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
- <span data-ttu-id="260b1-111">`LocalService`, que é executado no contexto de uma conta que age como um usuário sem privilégios no computador local e apresenta credenciais anônimas para qualquer servidor remoto;</span><span class="sxs-lookup"><span data-stu-id="260b1-111">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
- <span data-ttu-id="260b1-112">`LocalSystem`, que é executado no contexto de uma conta que fornece privilégios locais abrangentes e apresenta as credenciais do computador para qualquer servidor remoto;</span><span class="sxs-lookup"><span data-stu-id="260b1-112">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
- <span data-ttu-id="260b1-113">`NetworkService`, que é executado no contexto de uma conta que age como um usuário sem privilégios no computador local e apresenta as credenciais do computador para qualquer servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="260b1-113">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="260b1-114">Para obter mais informações, consulte a enumeração <xref:System.ServiceProcess.ServiceAccount>.</span><span class="sxs-lookup"><span data-stu-id="260b1-114">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="260b1-115">Para especificar o contexto de segurança de um serviço</span><span class="sxs-lookup"><span data-stu-id="260b1-115">To specify the security context for a service</span></span>  
  
1. <span data-ttu-id="260b1-116">Depois de criar o serviço, adicione os instaladores necessários para ele.</span><span class="sxs-lookup"><span data-stu-id="260b1-116">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="260b1-117">Para obter mais informações, confira [Como adicionar instaladores no seu aplicativo de serviço](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="260b1-117">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="260b1-118">No designer, acesse a classe `ProjectInstaller` e clique no instalador do processo de serviço para o serviço com o qual você está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="260b1-118">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="260b1-119">Para cada aplicativo de serviço, há pelo menos dois componentes de instalação na classe `ProjectInstaller` – um que instala os processos para todos os serviços no projeto e um instalador para cada serviço que o aplicativo contém.</span><span class="sxs-lookup"><span data-stu-id="260b1-119">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="260b1-120">Nesse caso, você desejará selecionar <xref:System.ServiceProcess.ServiceProcessInstaller>.</span><span class="sxs-lookup"><span data-stu-id="260b1-120">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3. <span data-ttu-id="260b1-121">Na janela **Propriedades**, defina a <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> para o valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="260b1-121">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="260b1-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="260b1-122">See also</span></span>

- [<span data-ttu-id="260b1-123">Introdução a aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="260b1-123">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="260b1-124">Como: Adicionar instaladores ao aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="260b1-124">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="260b1-125">Como: Criar serviços Windows</span><span class="sxs-lookup"><span data-stu-id="260b1-125">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
