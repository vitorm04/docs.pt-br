---
title: "Como implantar aplicativos .NET existentes para o serviço de aplicativo do Azure"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Como implantar aplicativos .NET existentes para o serviço de aplicativo do Azure"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 84bffe7aad6bbffb40519c9146d8156159d55850
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-deploy-existing-net-apps-to-azure-app-service"></a><span data-ttu-id="79374-103">Como implantar aplicativos .NET existentes para o serviço de aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="79374-103">How to deploy existing .NET apps to Azure App Service</span></span> 

<span data-ttu-id="79374-104">O recurso de aplicativos Web do serviço de aplicativo do Azure é uma plataforma de computação totalmente gerenciado que é otimizada para hospedar aplicativos web e sites.</span><span class="sxs-lookup"><span data-stu-id="79374-104">The Web Apps feature of Azure App Service is a fully managed compute platform that is optimized for hosting websites and web apps.</span></span> <span data-ttu-id="79374-105">Esta oferta de PaaS no Microsoft Azure permite você se concentre em sua lógica de negócios, enquanto o Azure se encarrega da infraestrutura para executar e dimensionar seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="79374-105">This PaaS offering in Microsoft Azure lets you focus on your business logic, while Azure takes care of the infrastructure to run and scale your apps.</span></span>

## <a name="validate-sites-and-migrate-to-app-service-with-azure-app-service-migration-assistant"></a><span data-ttu-id="79374-106">Validar sites e migrar para o serviço de aplicativo com o Assistente de migração do serviço de aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="79374-106">Validate sites and migrate to App Service with Azure App Service Migration Assistant</span></span>

<span data-ttu-id="79374-107">Quando você cria um novo aplicativo no Visual Studio, mover o aplicativo de serviço de aplicativo normalmente é simples.</span><span class="sxs-lookup"><span data-stu-id="79374-107">When you create a new application in Visual Studio, moving the app to App Service usually is straightforward.</span></span> <span data-ttu-id="79374-108">No entanto, se você planeja migrar um aplicativo existente para o serviço de aplicativo, primeiro você precisa avaliar se todas as dependências do aplicativo são compatíveis com o serviço de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79374-108">However, if you are planning to migrate an existing application to App Service, first you need to evaluate whether all your application's dependencies are compatible with App Service.</span></span> <span data-ttu-id="79374-109">Isso inclui dependências, como servidor de sistema operacional e qualquer software de terceiros que está instalado no servidor.</span><span class="sxs-lookup"><span data-stu-id="79374-109">This includes dependencies like server OS and any third-party software that's installed on the server.</span></span>

<span data-ttu-id="79374-110">Você pode usar [Assistente de migração do serviço de aplicativo do Azure](https://www.migratetoazure.net/) para analisar os sites e, em seguida, migrá-los de servidores de web do Windows e Linux para o serviço de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79374-110">You can use [Azure App Service Migration Assistant](https://www.migratetoazure.net/) to analyze sites and then migrate them from Windows and Linux web servers to App Service.</span></span> <span data-ttu-id="79374-111">Como parte da migração, a ferramenta cria aplicativos web e bancos de dados no Azure conforme necessário, publica o conteúdo e publica seu banco de dados.</span><span class="sxs-lookup"><span data-stu-id="79374-111">As part of the migration, the tool creates web apps and databases on Azure as needed, publishes content, and publishes your database.</span></span>

<span data-ttu-id="79374-112">Azure aplicativo serviço Assistente de migração dá suporte à migração do IIS em execução no Windows Server para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="79374-112">Azure App Service Migration Assistant supports migrating from IIS running on Windows Server to the cloud.</span></span> <span data-ttu-id="79374-113">Serviço de aplicativo oferece suporte ao Windows Server 2003 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="79374-113">App Service supports Windows Server 2003 and later versions.</span></span>

> ![https://www.migratetoazure.net/Images/ImageCanvas.png](./media/image5.png)
>
> <span data-ttu-id="79374-115">**Figura 4-5.**</span><span class="sxs-lookup"><span data-stu-id="79374-115">**Figure 4-5.**</span></span> <span data-ttu-id="79374-116">Usando o Assistente de migração do serviço de aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="79374-116">Using Azure App Service Migration Assistant</span></span>

<span data-ttu-id="79374-117">Assistente de migração do serviço de aplicativo é uma ferramenta que move os sites de seus servidores web na nuvem do Azure.</span><span class="sxs-lookup"><span data-stu-id="79374-117">App Service Migration Assistant is a tool that moves your websites from your web servers to the Azure cloud.</span></span>

<span data-ttu-id="79374-118">Depois que um site é migrado para o serviço de aplicativo, o site tem tudo o que precisa para executar com segurança e eficiência.</span><span class="sxs-lookup"><span data-stu-id="79374-118">After a website is migrated to App Service, the site has everything it needs to run safely and efficiently.</span></span> <span data-ttu-id="79374-119">Sites são configurados e executados automaticamente no serviço em nuvem do Azure PaaS (serviço de aplicativo).</span><span class="sxs-lookup"><span data-stu-id="79374-119">Sites are set up and run automatically in the Azure cloud PaaS service (App Service).</span></span>

<span data-ttu-id="79374-120">A ferramenta de migração do serviço de aplicativo pode analisar seus sites e relatar sobre sua compatibilidade para mover para o serviço de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="79374-120">The App Service migration tool can analyze your websites and report on their compatibility for moving to App Service.</span></span> <span data-ttu-id="79374-121">Se você estiver satisfeito com a análise, você pode deixar Assistente de migração do serviço de aplicativo migrar conteúdo, dados e as configurações para você.</span><span class="sxs-lookup"><span data-stu-id="79374-121">If you're happy with the analysis, you can let App Service Migration Assistant migrate content, data, and settings for you.</span></span> <span data-ttu-id="79374-122">Se um site não é totalmente compatível, a ferramenta de migração informa o que você precisa ajustar para que funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="79374-122">If a site is not quite compatible, the migration tool tells you what you need to adjust to make it work.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="79374-123">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="79374-123">Additional resources</span></span>

-   <span data-ttu-id="79374-124">**Assistente de migração do serviço de aplicativo do Azure**</span><span class="sxs-lookup"><span data-stu-id="79374-124">**Azure App Service Migration Assistant**</span></span>

    [<span data-ttu-id="79374-125">https://www.migratetoazure.net/</span><span class="sxs-lookup"><span data-stu-id="79374-125">https://www.migratetoazure.net/</span></span>](https://www.migratetoazure.net/)

>[!div class="step-by-step"]
<span data-ttu-id="79374-126">[Anterior](what-about-cloud-optimized-applications.md)
[Próximo](deploy-existing-net-apps-as-windows-containers.md)</span><span class="sxs-lookup"><span data-stu-id="79374-126">[Previous](what-about-cloud-optimized-applications.md)
[Next](deploy-existing-net-apps-as-windows-containers.md)</span></span>
