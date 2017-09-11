---
title: "Implantação do .NET Core Application"
description: "Implantação de um aplicativo .NET Core."
keywords: "Implantação do .NET e .NET Core"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: da7a31a0-8072-4f23-82aa-8a19184cb701
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 199bb132df201175dbdbdd19634de5c3551b5f3b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="net-core-application-deployment"></a><span data-ttu-id="932ad-104">Implantação de um aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="932ad-104">.NET Core application deployment</span></span>

<span data-ttu-id="932ad-105">Você pode criar dois tipos de implantações de aplicativos do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="932ad-105">You can create two types of deployments for .NET Core applications:</span></span>

- <span data-ttu-id="932ad-106">Implantação dependente de estrutura.</span><span class="sxs-lookup"><span data-stu-id="932ad-106">Framework-dependent deployment.</span></span> <span data-ttu-id="932ad-107">Como o nome indica, a FDD (implantação dependente de estrutura) se baseia na presença de uma versão compartilhada em todo o sistema do .NET Core no sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="932ad-107">As the name implies, framework-dependent deployment (FDD) relies on the presence of a shared system-wide version of .NET Core on the target system.</span></span> <span data-ttu-id="932ad-108">Como o .NET Core já está presente, seu aplicativo também é portátil entre instalações do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="932ad-108">Because .NET Core is already present, your app is also portable between installations of .NET Core.</span></span> <span data-ttu-id="932ad-109">Seu aplicativo conterá somente seu próprio código e as dependências de terceiros que estiverem fora de bibliotecas .NET Core.</span><span class="sxs-lookup"><span data-stu-id="932ad-109">Your app contains only its own code and any third-party dependencies that are outside of the .NET Core libraries.</span></span> <span data-ttu-id="932ad-110">As FDDs contêm arquivos *.dll* que podem ser iniciados por meio do [utilitário dotnet](../tools/dotnet.md) na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="932ad-110">FDDs contain *.dll* files that can be launched by using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span> <span data-ttu-id="932ad-111">Por exemplo, `dotnet app.dll` executa um aplicativo chamado `app`.</span><span class="sxs-lookup"><span data-stu-id="932ad-111">For example, `dotnet app.dll` runs an application named `app`.</span></span>

- <span data-ttu-id="932ad-112">Implantação autocontida.</span><span class="sxs-lookup"><span data-stu-id="932ad-112">Self-contained deployment.</span></span> <span data-ttu-id="932ad-113">Ao contrário da FDD, a SCD (implantação autocontida) não se baseia na presença de componentes compartilhados no sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="932ad-113">Unlike FDD, a self-contained deployment (SCD) doesn't rely on the presence of shared components on the target system.</span></span> <span data-ttu-id="932ad-114">Todos os componentes, inclusive as bibliotecas e o tempo de execução do .NET Core, são incluídos com o aplicativo e isolados de outros aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="932ad-114">All components, including both the .NET Core libraries and the .NET Core runtime, are included with the application and are isolated from other .NET Core applications.</span></span> <span data-ttu-id="932ad-115">As SCDs incluem um arquivo executável (como o *app.exe* em plataformas Windows para um aplicativo chamado `app`), que é uma versão renomeada do host específico da plataforma .NET Core, e um arquivo *.dll* (como *app.dll*), que é o aplicativo real.</span><span class="sxs-lookup"><span data-stu-id="932ad-115">SCDs include an executable (such as *app.exe* on Windows platforms for an application named `app`), which is  a renamed version of the platform-specific .NET Core host, and a *.dll* file (such as *app.dll*), which is the actual application.</span></span>

## <a name="framework-dependent-deployments-fdd"></a><span data-ttu-id="932ad-116">FDD (implantação dependente de estrutura)</span><span class="sxs-lookup"><span data-stu-id="932ad-116">Framework-dependent deployments (FDD)</span></span>

<span data-ttu-id="932ad-117">Para uma FDD, seu aplicativo é implantado apenas em dependências de terceiros.</span><span class="sxs-lookup"><span data-stu-id="932ad-117">For an FDD, you deploy only your app and any third-party dependencies.</span></span> <span data-ttu-id="932ad-118">Você não precisa implantar o .NET Core, pois o aplicativo usará a versão do .NET Core presente no sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="932ad-118">You don't have to deploy .NET Core, since your app will use the version of .NET Core that's present on the target system.</span></span> <span data-ttu-id="932ad-119">Este é o modelo de implantação padrão para aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="932ad-119">This is the default deployment model for .NET Core apps.</span></span>

### <a name="why-create-a-framework-dependent-deployment"></a><span data-ttu-id="932ad-120">Por que criar uma implantação dependente de estrutura?</span><span class="sxs-lookup"><span data-stu-id="932ad-120">Why create a framework-dependent deployment?</span></span>

<span data-ttu-id="932ad-121">Implantar uma FDD traz uma série de vantagens:</span><span class="sxs-lookup"><span data-stu-id="932ad-121">Deploying an FDD has a number of advantages:</span></span>

- <span data-ttu-id="932ad-122">Você não precisa definir previamente em quais sistemas operacionais de destino o aplicativo .NET Core será executado.</span><span class="sxs-lookup"><span data-stu-id="932ad-122">You don't have to define the target operating systems that your .NET Core app will run on in advance.</span></span> <span data-ttu-id="932ad-123">Como o .NET Core usa um formato comum de arquivo PE comum para executáveis e bibliotecas independentemente do sistema operacional, ele pode executar seu aplicativo independentemente do sistema operacional subjacente.</span><span class="sxs-lookup"><span data-stu-id="932ad-123">Because .NET Core uses a common PE file format for executables and libraries regardless of operating system, .NET Core can execute your app regardless of the underlying operating system.</span></span> <span data-ttu-id="932ad-124">Para obter mais informações sobre o formato de arquivo PE, consulte [Formato de Arquivo do Assembly .NET](../../standard/assembly-format.md).</span><span class="sxs-lookup"><span data-stu-id="932ad-124">For more information on the PE file format, see [.NET Assembly File Format](../../standard/assembly-format.md).</span></span>

- <span data-ttu-id="932ad-125">O tamanho do seu pacote de implantação é pequeno.</span><span class="sxs-lookup"><span data-stu-id="932ad-125">The size of your deployment package is small.</span></span> <span data-ttu-id="932ad-126">Você deve implantar apenas o aplicativo e as respectivas dependências, mas não o .NET Core em si.</span><span class="sxs-lookup"><span data-stu-id="932ad-126">You only deploy your app and its dependencies, not .NET Core itself.</span></span>

- <span data-ttu-id="932ad-127">Vários aplicativos usam a mesma instalação do .NET Core, o que reduz o uso de memória e espaço em disco nos sistemas host.</span><span class="sxs-lookup"><span data-stu-id="932ad-127">Multiple apps use the same .NET Core installation, which reduces both disk space and memory usage on host systems.</span></span>

<span data-ttu-id="932ad-128">Contudo, também há algumas desvantagens:</span><span class="sxs-lookup"><span data-stu-id="932ad-128">There are also a few disadvantages:</span></span>

- <span data-ttu-id="932ad-129">Seu aplicativo poderá ser executado somente se a versão do .NET Core de destino, ou uma versão posterior, já estiver instalada no sistema host.</span><span class="sxs-lookup"><span data-stu-id="932ad-129">Your app can run only if the version of .NET Core that you target, or a later version, is already installed on the host system.</span></span>

- <span data-ttu-id="932ad-130">É possível que o tempo de execução e as bibliotecas do .NET Core sejam alteradas em versões futuras, sem seu conhecimento.</span><span class="sxs-lookup"><span data-stu-id="932ad-130">It's possible for the .NET Core runtime and libraries to change without your knowledge in future releases.</span></span> <span data-ttu-id="932ad-131">Em casos raros, isso pode alterar o comportamento do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="932ad-131">In rare cases, this may change the behavior of your app.</span></span>

## <a name="self-contained-deployments-scd"></a><span data-ttu-id="932ad-132">SCD (implantação autocontida)</span><span class="sxs-lookup"><span data-stu-id="932ad-132">Self-contained deployments (SCD)</span></span>

<span data-ttu-id="932ad-133">No caso de uma implantação autocontida, você implanta o aplicativo e as dependências de terceiros necessárias, juntamente com a versão do .NET Core que usou para criar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="932ad-133">For a self-contained deployment, you deploy your app and any required third-party dependencies along with the version of .NET Core that you used to build the app.</span></span> <span data-ttu-id="932ad-134">A criação de uma SCD não inclui as [dependências nativas do .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) de várias plataformas, por isso elas devem estar presentes antes de executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="932ad-134">Creating an SCD doesn't include the [native dependencies of .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) on various platforms, so these must be present before the app runs.</span></span>

<span data-ttu-id="932ad-135">Implantações FDD e SCD usam executáveis de host separadas, para que você possa assinar um executável de host para um SCD com sua assinatura do publicador.</span><span class="sxs-lookup"><span data-stu-id="932ad-135">FDD and SCD deployments use separate host executables, so you can sign a host executable for an SCD with your publisher signature.</span></span>

### <a name="why-deploy-a-self-contained-deployment"></a><span data-ttu-id="932ad-136">Por que fazer uma implantação autocontida?</span><span class="sxs-lookup"><span data-stu-id="932ad-136">Why deploy a self-contained deployment?</span></span>

<span data-ttu-id="932ad-137">Implantar uma implantação autocontida apresenta duas vantagens principais:</span><span class="sxs-lookup"><span data-stu-id="932ad-137">Deploying a Self-contained deployment has two major advantages:</span></span>

- <span data-ttu-id="932ad-138">Você tem controle exclusivo sobre a versão do .NET Core que é implantada com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="932ad-138">You have sole control of the version of .NET Core that is deployed with your app.</span></span> <span data-ttu-id="932ad-139">A manutenção do .NET Core só pode ser feita por você.</span><span class="sxs-lookup"><span data-stu-id="932ad-139">.NET Core can be serviced only by you.</span></span>

- <span data-ttu-id="932ad-140">É possível ter certeza de que o sistema de destino pode executar seu aplicativo .NET Core, visto que você está fornecendo a versão do .NET Core na qual ele é executado.</span><span class="sxs-lookup"><span data-stu-id="932ad-140">You can be assured that the target system can run your .NET Core app, since you're providing the version of .NET Core that it will run on.</span></span>

<span data-ttu-id="932ad-141">Ela também apresenta algumas desvantagens:</span><span class="sxs-lookup"><span data-stu-id="932ad-141">It also has a number of disadvantages:</span></span>

- <span data-ttu-id="932ad-142">Como o .NET Core é incluído no seu pacote de implantação, você deve selecionar previamente as plataformas de destino para as quais você criará pacotes de implantação.</span><span class="sxs-lookup"><span data-stu-id="932ad-142">Because .NET Core is included in your deployment package, you must select the target platforms for which you build deployment packages in advance.</span></span>

- <span data-ttu-id="932ad-143">O tamanho do seu pacote de implantação é relativamente grande, visto que você precisa incluir o .NET Core, bem como seu aplicativo e suas dependências de terceiros.</span><span class="sxs-lookup"><span data-stu-id="932ad-143">The size of your deployment package is relatively large, since you have to include .NET Core as well as your app and its third-party dependencies.</span></span>

- <span data-ttu-id="932ad-144">Implantar vários aplicativos .NET Core autocontidos em um sistema pode consumir um volume significativo de espaço em disco, visto que cada aplicativo duplica os arquivos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="932ad-144">Deploying numerous self-contained .NET Core apps to a system can consume significant amounts of disk space, since each app duplicates .NET Core files.</span></span>

## <a name="step-by-step-examples"></a><span data-ttu-id="932ad-145">Exemplos passo a passo</span><span class="sxs-lookup"><span data-stu-id="932ad-145">Step-by-step examples</span></span>

<span data-ttu-id="932ad-146">Para obter exemplos passo a passo de como implantar aplicativos .NET Core com ferramentas da CLI, confira o artigo [Implantação de aplicativos .NET Core com ferramentas da CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="932ad-146">For step-by-step examples of deploying .NET Core apps with CLI tools, see [Deploying .NET Core Apps with CLI Tools](deploy-with-cli.md).</span></span> <span data-ttu-id="932ad-147">Para obter exemplos passo a passo de como implantar aplicativos .NET Core com o Visual Studio, confira o artigo [Implantação de aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="932ad-147">For step-by-step examples of deploying .NET Core apps with Visual Studio, see [Deploying .NET Core Apps with Visual Studio](deploy-with-vs.md).</span></span> <span data-ttu-id="932ad-148">Cada tópico inclui exemplos das seguintes implantações:</span><span class="sxs-lookup"><span data-stu-id="932ad-148">Each topic includes examples of the following deployments:</span></span>

- <span data-ttu-id="932ad-149">Implantação dependente de estrutura</span><span class="sxs-lookup"><span data-stu-id="932ad-149">Framework-dependent deployment</span></span>
- <span data-ttu-id="932ad-150">Implantação dependente de estrutura com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="932ad-150">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="932ad-151">Implantação autocontida</span><span class="sxs-lookup"><span data-stu-id="932ad-151">Self-contained deployment</span></span>
- <span data-ttu-id="932ad-152">Implantação autocontida com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="932ad-152">Self-contained deployment with third-party dependencies</span></span>

# <a name="see-also"></a><span data-ttu-id="932ad-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="932ad-153">See also</span></span>

<span data-ttu-id="932ad-154">[Implantação de aplicativos .NET Core com ferramentas da CLI](deploy-with-cli.md) </span><span class="sxs-lookup"><span data-stu-id="932ad-154">[Deploying .NET Core Apps with CLI Tools](deploy-with-cli.md) </span></span>  
<span data-ttu-id="932ad-155">[Implantação de aplicativos .NET Core com o Visual Studio](deploy-with-vs.md) </span><span class="sxs-lookup"><span data-stu-id="932ad-155">[Deploying .NET Core Apps with Visual Studio](deploy-with-vs.md) </span></span>  
<span data-ttu-id="932ad-156">[Pacotes, metapacotes e estruturas](../packages.md) </span><span class="sxs-lookup"><span data-stu-id="932ad-156">[Packages, Metapackages and Frameworks](../packages.md) </span></span>  
[<span data-ttu-id="932ad-157">Catálogo do Identificador de Tempo de Execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="932ad-157">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)

