---
title: Exemplo de migração para o .NET Core 3.1
description: Mostrando como migrar um aplicativo de exemplo destinado a .NET Framework para o .NET Core 3,1.
ms.date: 05/12/2020
ms.openlocfilehash: ef8a0c24ec81a21eb89411ed4c9a543d4d70d89f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423379"
---
# <a name="example-of-migrating-to-net-core-31"></a><span data-ttu-id="7b198-103">Exemplo de migração para o .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="7b198-103">Example of migrating to .NET Core 3.1</span></span>

<span data-ttu-id="7b198-104">Neste capítulo, apresentamos diretrizes práticas para ajudá-lo a realizar uma migração de seu aplicativo existente do .NET Framework para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-104">In this chapter, we present practical guidelines to help you perform a migration of your existing application from .NET Framework to .NET Core.</span></span>

<span data-ttu-id="7b198-105">Apresentamos um processo bem estruturado que você pode seguir e as coisas mais importantes a serem consideradas em cada etapa.</span><span class="sxs-lookup"><span data-stu-id="7b198-105">We present a well-structured process you can follow and the most important things to consider on each step.</span></span>

<span data-ttu-id="7b198-106">Em seguida, documentamos um processo de migração passo a passo para um aplicativo de desktop de exemplo, tanto de WinForms quanto de versões do WPF.</span><span class="sxs-lookup"><span data-stu-id="7b198-106">We then document a step-by-step migration process for a sample desktop application, both from WinForms and WPF versions.</span></span>

## <a name="migration-process-overview"></a><span data-ttu-id="7b198-107">Visão geral do processo de migração</span><span class="sxs-lookup"><span data-stu-id="7b198-107">Migration process overview</span></span>

<span data-ttu-id="7b198-108">O processo de migração consiste em quatro etapas sequenciais:</span><span class="sxs-lookup"><span data-stu-id="7b198-108">The migration process consists of four sequential steps:</span></span>

1. <span data-ttu-id="7b198-109">**Preparação**: entenda as dependências que o projeto tem para ter uma ideia do que está em frente.</span><span class="sxs-lookup"><span data-stu-id="7b198-109">**Preparation**: Understand the dependencies the project has to have an idea of what's ahead.</span></span> <span data-ttu-id="7b198-110">Nesta etapa, você pega o projeto atual em um estado que simplifica o ponto de inicialização para a migração.</span><span class="sxs-lookup"><span data-stu-id="7b198-110">In this step, you take the current project into a state that simplifies the startup point for the migration.</span></span>

2. <span data-ttu-id="7b198-111">**Migrar arquivo de projeto:** os projetos do .NET Core usam o novo formato de projeto em estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="7b198-111">**Migrate Project File:** .NET Core projects use the new SDK-style project format.</span></span> <span data-ttu-id="7b198-112">Crie um novo arquivo de projeto com esse formato ou atualize o que você precisa para usar o estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="7b198-112">Create a new project file with this format or update the one you have to use the SDK style.</span></span>

3. <span data-ttu-id="7b198-113">**Corrigir código e compilar:** Compile o código no .NET Core que aborda as diferenças de nível de API entre o .NET Framework e o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-113">**Fix code and build:** Build the code in .NET Core addressing API-level differences between .NET Framework and .NET Core.</span></span> <span data-ttu-id="7b198-114">Se necessário, atualize pacotes de terceiros para aqueles que dão suporte ao .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-114">If needed, update third-party packages to the ones that support .NET Core.</span></span>

4. <span data-ttu-id="7b198-115">**Executar e testar:** Pode haver diferenças que não aparecem até o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7b198-115">**Run and test:** There might be differences that don't show up until run time.</span></span> <span data-ttu-id="7b198-116">Portanto, não se esqueça de executar o aplicativo e testar se tudo funciona conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="7b198-116">So, don't forget to run the application and test that everything works as expected.</span></span>

### <a name="preparation"></a><span data-ttu-id="7b198-117">Preparação</span><span class="sxs-lookup"><span data-stu-id="7b198-117">Preparation</span></span>

#### <a name="migrate-packagesconfig-file"></a><span data-ttu-id="7b198-118">Migrar arquivo Packages. config</span><span class="sxs-lookup"><span data-stu-id="7b198-118">Migrate packages.config file</span></span>

<span data-ttu-id="7b198-119">Em um aplicativo .NET Framework, todas as referências a pacotes externos são declaradas no arquivo *Packages. config* .</span><span class="sxs-lookup"><span data-stu-id="7b198-119">In a .NET Framework application, all references to external packages are declared in the *packages.config* file.</span></span> <span data-ttu-id="7b198-120">No .NET Core, não há mais a necessidade de usar o arquivo *Packages. config* .</span><span class="sxs-lookup"><span data-stu-id="7b198-120">In .NET Core, there's no longer the need to use the *packages.config* file.</span></span> <span data-ttu-id="7b198-121">Em vez disso, use a propriedade [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) dentro do arquivo de projeto para especificar os pacotes NuGet para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b198-121">Instead, use the [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) property inside the project file to specify the NuGet packages for your app.</span></span>

<span data-ttu-id="7b198-122">Portanto, você precisa fazer a transição de um formato para outro.</span><span class="sxs-lookup"><span data-stu-id="7b198-122">So, you need to transition from one format to another.</span></span> <span data-ttu-id="7b198-123">Você pode fazer a atualização manualmente, tomando as dependências contidas no arquivo *Packages. config* e migrando-as para o arquivo de projeto com o `PackageReference` formato.</span><span class="sxs-lookup"><span data-stu-id="7b198-123">You can do the update manually, taking the dependencies contained in the *packages.config* file and migrating them to the project file with the `PackageReference` format.</span></span> <span data-ttu-id="7b198-124">Ou, você pode permitir que o Visual Studio faça o trabalho para você: clique com o botão direito do mouse no arquivo *Packages. config* e selecione a opção **Migrate Packages. config para PackageReference** .</span><span class="sxs-lookup"><span data-stu-id="7b198-124">Or, you can let Visual Studio do the work for you: right-click on the *packages.config* file and select the **Migrate packages.config to PackageReference** option.</span></span>

#### <a name="verify-every-dependency-compatibility-in-net-core"></a><span data-ttu-id="7b198-125">Verificar cada compatibilidade de dependência no .NET Core</span><span class="sxs-lookup"><span data-stu-id="7b198-125">Verify every dependency compatibility in .NET Core</span></span>

<span data-ttu-id="7b198-126">Depois de migrar as referências de pacote, você deve verificar a compatibilidade de cada referência.</span><span class="sxs-lookup"><span data-stu-id="7b198-126">Once you've migrated the package references, you must check each reference for compatibility.</span></span> <span data-ttu-id="7b198-127">Você pode explorar as dependências de cada pacote NuGet que seu aplicativo está usando no [NuGet.org](https://www.nuget.org/). Se o pacote tiver dependências .NET Standard, ele vai funcionar no .NET Core porque o .NET Core 3,1 [oferece suporte](../../standard/net-standard.md#net-implementation-support) a todas as versões do .net Standard.</span><span class="sxs-lookup"><span data-stu-id="7b198-127">You can explore the dependencies of each NuGet package your application is using on [nuget.org](https://www.nuget.org/). If the package has .NET Standard dependencies, then it's going to work on .NET Core because .NET Core 3.1 [supports](../../standard/net-standard.md#net-implementation-support) all versions of .NET Standard.</span></span> <span data-ttu-id="7b198-128">A imagem a seguir mostra as dependências para o `Castle.Windsor` pacote:</span><span class="sxs-lookup"><span data-stu-id="7b198-128">The following image shows the dependencies for the `Castle.Windsor` package:</span></span>

![Captura de tela das dependências do NuGet para o pacote Castle. Windsor](./media/example-migration-core/nuget-dependencies.png)

<span data-ttu-id="7b198-130">Para verificar a compatibilidade do pacote, você pode usar a ferramenta <http://fuget.org> que oferece informações mais detalhadas sobre as versões e dependências.</span><span class="sxs-lookup"><span data-stu-id="7b198-130">To check the package compatibility, you can use the tool <http://fuget.org> that offers a more detailed information about versions and dependencies.</span></span>

<span data-ttu-id="7b198-131">Talvez o projeto faça referência a versões mais antigas do pacote que não dão suporte ao .NET Core, mas você pode encontrar versões mais recentes que dão suporte a ela.</span><span class="sxs-lookup"><span data-stu-id="7b198-131">Maybe the project is referencing older package versions that don't support .NET Core, but you might find newer versions that do support it.</span></span> <span data-ttu-id="7b198-132">Portanto, a atualização de pacotes para versões mais recentes é geralmente uma boa recomendação.</span><span class="sxs-lookup"><span data-stu-id="7b198-132">So, updating packages to newer versions is generally a good recommendation.</span></span> <span data-ttu-id="7b198-133">No entanto, você deve considerar que a atualização da versão do pacote pode introduzir algumas alterações significativas que forçariam a atualização do código.</span><span class="sxs-lookup"><span data-stu-id="7b198-133">However, you should consider that updating the package version can introduce some breaking changes that would force you to update your code.</span></span>

<span data-ttu-id="7b198-134">O que acontecerá se você não encontrar uma versão compatível?</span><span class="sxs-lookup"><span data-stu-id="7b198-134">What happens if you don't find a compatible version?</span></span> <span data-ttu-id="7b198-135">E se você simplesmente não quiser atualizar a versão de um pacote devido a essas alterações significativas?</span><span class="sxs-lookup"><span data-stu-id="7b198-135">What if you just don't want to update the version of a package because of these breaking changes?</span></span> <span data-ttu-id="7b198-136">Não se preocupe porque é possível depender de .NET Framework pacotes de um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-136">Don't worry because it's possible to depend on .NET Framework packages from a .NET Core application.</span></span> <span data-ttu-id="7b198-137">Não se esqueça de testá-lo extensivamente, pois isso poderá causar erros em tempo de execução se o pacote externo chamar uma API que não está disponível no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-137">Don't forget to test it extensively because it can cause run-time errors if the external package calls an API that isn't available on .NET Core.</span></span> <span data-ttu-id="7b198-138">Isso é ótimo para quando você estiver usando um pacote antigo que não será atualizado e você pode simplesmente redirecionar para trabalhar no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-138">This is great for when you're using an old package that isn't going to be updated and you can just retarget to work on the .NET Core.</span></span>

#### <a name="check-for-api-compatibility"></a><span data-ttu-id="7b198-139">Verificar compatibilidade de API</span><span class="sxs-lookup"><span data-stu-id="7b198-139">Check for API compatibility</span></span>

<span data-ttu-id="7b198-140">Como a superfície da API no .NET Framework e no .NET Core são semelhantes, mas não idênticas, você deve verificar quais APIs estão disponíveis no .NET Core e quais não são.</span><span class="sxs-lookup"><span data-stu-id="7b198-140">Since the API surface in .NET Framework and .NET Core is similar but not identical, you must check which APIs are available on .NET Core and which aren't.</span></span> <span data-ttu-id="7b198-141">Você pode usar a ferramenta do analisador de portabilidade .NET para retonar as APIs usadas que não estão presentes no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-141">You can use the .NET Portability Analyzer tool to surface APIs used that aren't present on .NET Core.</span></span> <span data-ttu-id="7b198-142">Ele examina o nível binário do seu aplicativo, extrai todas as APIs que são chamadas e, em seguida, lista quais APIs não estão disponíveis em sua estrutura de destino (o .NET Core 3,1, nesse caso).</span><span class="sxs-lookup"><span data-stu-id="7b198-142">It looks at the binary level of your app, extracts all the APIs that are called, and then lists which APIs aren't available on your target framework (.NET Core 3.1 in this case).</span></span>

<span data-ttu-id="7b198-143">Você pode encontrar mais informações sobre essa ferramenta em:</span><span class="sxs-lookup"><span data-stu-id="7b198-143">You can find more information about this tool at:</span></span>

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

<span data-ttu-id="7b198-144">Um aspecto interessante dessa ferramenta é que ela só faz a superfície das diferenças de seu próprio código e não do código de pacotes externos, que não podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="7b198-144">An interesting aspect of this tool is that it only surfaces the differences from your own code and not code from external packages, which you can't change.</span></span> <span data-ttu-id="7b198-145">Lembre-se de que você deve ter atualizado a maioria desses pacotes para que eles funcionem com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-145">Remember you should have updated most of these packages to make them work with .NET Core.</span></span>

### <a name="migrate-project-file"></a><span data-ttu-id="7b198-146">Migrar arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="7b198-146">Migrate project file</span></span>

#### <a name="create-the-new-net-core-project"></a><span data-ttu-id="7b198-147">Criar o novo projeto .NET Core</span><span class="sxs-lookup"><span data-stu-id="7b198-147">Create the new .NET Core project</span></span>

<span data-ttu-id="7b198-148">Na maioria dos casos, você desejará atualizar seu projeto existente para o novo formato .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-148">In most of the cases, you'll want to update your existing project to the new .NET Core format.</span></span> <span data-ttu-id="7b198-149">No entanto, você também pode criar um novo projeto mantendo o antigo.</span><span class="sxs-lookup"><span data-stu-id="7b198-149">However, you can also create a new project while maintaining the old one.</span></span> <span data-ttu-id="7b198-150">A principal desvantagem de atualizar o projeto antigo é que você perde o suporte do designer, o que pode ser importante para você.</span><span class="sxs-lookup"><span data-stu-id="7b198-150">The main drawback from updating the old project is that you lose designer support, which may be important for you.</span></span> <span data-ttu-id="7b198-151">Se você quiser continuar usando o designer, deverá criar um novo projeto do .NET Core em paralelo com o antigo e compartilhar os ativos.</span><span class="sxs-lookup"><span data-stu-id="7b198-151">If you want to keep using the designer, you must create a new .NET Core project in parallel with the old one and share assets.</span></span> <span data-ttu-id="7b198-152">Se você precisar modificar elementos da interface do usuário no designer, poderá alternar para o projeto antigo para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="7b198-152">If you need to modify UI elements in the designer, you can switch to the old project to do that.</span></span> <span data-ttu-id="7b198-153">E, como os ativos são vinculados, eles também serão atualizados no projeto do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-153">And since assets are linked, they'll be updated in the .NET Core project as well.</span></span>

<span data-ttu-id="7b198-154">O [projeto em estilo SDK](../../core/project-sdk/msbuild-props.md) para .NET Core é muito mais simples do que .NET Framework formato de projeto.</span><span class="sxs-lookup"><span data-stu-id="7b198-154">The [SDK-style project](../../core/project-sdk/msbuild-props.md) for .NET Core is a lot simpler than .NET Framework's project format.</span></span> <span data-ttu-id="7b198-155">E além das entradas mencionadas anteriormente `PackageReference` , você não precisará fazer muito mais.</span><span class="sxs-lookup"><span data-stu-id="7b198-155">And apart from the previously mentioned `PackageReference` entries, you won't need to do much more.</span></span> <span data-ttu-id="7b198-156">O novo formato de projeto inclui determinadas extensões de arquivo [por padrão](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects), `.cs` como `.xaml` arquivos e, sem a necessidade de incluí-los explicitamente no arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="7b198-156">The new project format includes certain file extensions [by default](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects), such as `.cs` and `.xaml` files, without the need to explicitly include them in the project file.</span></span>

#### <a name="assemblyinfo-considerations"></a><span data-ttu-id="7b198-157">Considerações sobre o Assembly.info</span><span class="sxs-lookup"><span data-stu-id="7b198-157">Assembly.info considerations</span></span>

<span data-ttu-id="7b198-158">Os atributos são gerados automaticamente em projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-158">Attributes are autogenerated on .NET Core projects.</span></span> <span data-ttu-id="7b198-159">Se o projeto contiver um arquivo *AssemblyInfo.cs* , as definições serão duplicadas, o que causará conflitos de compilação.</span><span class="sxs-lookup"><span data-stu-id="7b198-159">If the project contains an *AssemblyInfo.cs* file, the definitions will be duplicated, which will cause compilation conflicts.</span></span> <span data-ttu-id="7b198-160">Você pode excluir o arquivo *AssemblyInfo.cs* mais antigo ou desabilitar a geração automática adicionando a seguinte entrada ao arquivo de projeto do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="7b198-160">You can delete the older *AssemblyInfo.cs* file or disable autogeneration by adding the following entry to the .NET Core project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a><span data-ttu-id="7b198-161">Recursos</span><span class="sxs-lookup"><span data-stu-id="7b198-161">Resources</span></span>

<span data-ttu-id="7b198-162">Os recursos inseridos são incluídos automaticamente, mas os recursos não são, portanto, você precisa migrar os recursos para o novo arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="7b198-162">Embedded resources are included automatically but resources aren't, so you need to migrate the resources to the new project file.</span></span>

#### <a name="package-references"></a><span data-ttu-id="7b198-163">Referências de pacote</span><span class="sxs-lookup"><span data-stu-id="7b198-163">Package references</span></span>

<span data-ttu-id="7b198-164">Com a opção **Migrate Packages. config para PackageReference** , você pode facilmente mover suas referências de pacote externo para o novo formato conforme mencionado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7b198-164">With the **Migrate packages.config to PackageReference** option, you can easily move your external package references to the new format as previously mentioned.</span></span>

#### <a name="update-package-references"></a><span data-ttu-id="7b198-165">Referências do pacote de atualização</span><span class="sxs-lookup"><span data-stu-id="7b198-165">Update package references</span></span>

<span data-ttu-id="7b198-166">Atualize as versões dos pacotes que você encontrou para serem compatíveis, conforme mostrado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="7b198-166">Update the versions of the packages you've found to be compatible, as shown in the previous section.</span></span>

### <a name="fix-the-code-and-build"></a><span data-ttu-id="7b198-167">Corrigir o código e compilar</span><span class="sxs-lookup"><span data-stu-id="7b198-167">Fix the code and build</span></span>

#### <a name="microsoftwindowscompatibility"></a><span data-ttu-id="7b198-168">Microsoft. Windows. Compatibility</span><span class="sxs-lookup"><span data-stu-id="7b198-168">Microsoft.Windows.Compatibility</span></span>

<span data-ttu-id="7b198-169">Se seu aplicativo depende de APIs que não estão disponíveis no .NET Core, como registro, ACLs ou WCF, você precisa incluir uma referência ao `Microsoft.Windows.Compatibility` pacote para adicionar essas APIs específicas do Windows.</span><span class="sxs-lookup"><span data-stu-id="7b198-169">If your application depends on APIs that aren't available on .NET Core, such as Registry, ACLs, or WCF, you have to include a reference to the `Microsoft.Windows.Compatibility` package to add these Windows-specific APIs.</span></span> <span data-ttu-id="7b198-170">Eles funcionam no .NET Core, mas não são incluídos, pois não são de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="7b198-170">They work on .NET Core but aren't included as they aren't cross-platform.</span></span>

<span data-ttu-id="7b198-171">Há uma ferramenta chamada API Analyzer ( <https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer> ) que ajuda a identificar APIs que não são compatíveis com seu código.</span><span class="sxs-lookup"><span data-stu-id="7b198-171">There's a tool called API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) that helps you identify APIs that aren't compatible with your code.</span></span>

#### <a name="use-if-directives"></a><span data-ttu-id="7b198-172">Usar as \# diretivas If</span><span class="sxs-lookup"><span data-stu-id="7b198-172">Use \#if directives</span></span>

<span data-ttu-id="7b198-173">Se você precisar de caminhos de execução diferentes ao direcionar .NET Framework e o .NET Core, deverá usar constantes de compilação.</span><span class="sxs-lookup"><span data-stu-id="7b198-173">If you need different execution paths when targeting .NET Framework and .NET Core, you should use compilation constants.</span></span> <span data-ttu-id="7b198-174">Adicione algumas \# diretivas If ao seu código para manter a mesma base de código para ambos os destinos.</span><span class="sxs-lookup"><span data-stu-id="7b198-174">Add some \#if directives to your code to keep the same code base for both targets.</span></span>

#### <a name="technologies-not-available-on-net-core"></a><span data-ttu-id="7b198-175">Tecnologias não disponíveis no .NET Core</span><span class="sxs-lookup"><span data-stu-id="7b198-175">Technologies not available on .NET Core</span></span>

<span data-ttu-id="7b198-176">Algumas tecnologias não estão disponíveis no .NET Core, como:</span><span class="sxs-lookup"><span data-stu-id="7b198-176">Some technologies aren't available on .NET Core, such as:</span></span>

* <span data-ttu-id="7b198-177">AppDomains</span><span class="sxs-lookup"><span data-stu-id="7b198-177">AppDomains</span></span>
* <span data-ttu-id="7b198-178">Comunicação remota</span><span class="sxs-lookup"><span data-stu-id="7b198-178">Remoting</span></span>
* <span data-ttu-id="7b198-179">Segurança de Acesso do Código</span><span class="sxs-lookup"><span data-stu-id="7b198-179">Code Access Security</span></span>
* <span data-ttu-id="7b198-180">Servidor WCF</span><span class="sxs-lookup"><span data-stu-id="7b198-180">WCF Server</span></span>
* <span data-ttu-id="7b198-181">Fluxo de trabalho do Windows</span><span class="sxs-lookup"><span data-stu-id="7b198-181">Windows Workflow</span></span>

<span data-ttu-id="7b198-182">É por isso que você precisa encontrar uma substituição para essas tecnologias se você as estiver usando em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b198-182">That's why you need to find a replacement for these technologies if you're using them in your application.</span></span> <span data-ttu-id="7b198-183">Para obter mais informações, consulte o artigo [.NET Framework tecnologias indisponíveis no .NET Core](../../core/porting/net-framework-tech-unavailable.md) .</span><span class="sxs-lookup"><span data-stu-id="7b198-183">For more information, see the [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md) article.</span></span>

#### <a name="regenerate-autogenerated-clients"></a><span data-ttu-id="7b198-184">Regenerar clientes gerados automaticamente</span><span class="sxs-lookup"><span data-stu-id="7b198-184">Regenerate autogenerated clients</span></span>

<span data-ttu-id="7b198-185">Se seu aplicativo usar código gerado automaticamente, como um cliente WCF, talvez seja necessário gerar novamente esse código para o .NET Core de destino.</span><span class="sxs-lookup"><span data-stu-id="7b198-185">If your application uses autogenerated code, such as a WCF client, you may need to regenerate this code to target .NET Core.</span></span> <span data-ttu-id="7b198-186">Às vezes, você pode encontrar algumas referências ausentes, já que elas não podem ser incluídas como parte do conjunto de assemblies do .NET Core padrão.</span><span class="sxs-lookup"><span data-stu-id="7b198-186">Sometimes, you can find some missing references since they may not be included as part of the default .NET Core assemblies set.</span></span> <span data-ttu-id="7b198-187">Usando uma ferramenta como <https://apisof.net/> , você pode facilmente localizar o assembly no qual a referência ausente reside e adicioná-lo do NuGet.</span><span class="sxs-lookup"><span data-stu-id="7b198-187">Using a tool like <https://apisof.net/>, you can easily locate the assembly the missing reference lives in and add it from NuGet.</span></span>

#### <a name="rolling-back-package-versions"></a><span data-ttu-id="7b198-188">Revertendo versões de pacote</span><span class="sxs-lookup"><span data-stu-id="7b198-188">Rolling back package versions</span></span>

<span data-ttu-id="7b198-189">Como regra geral, mencionamos anteriormente que você atualiza melhor cada versão de pacote para ser compatível com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-189">As a general rule, we've previously stated that you better update every single package version to be compatible with .NET Core.</span></span> <span data-ttu-id="7b198-190">No entanto, você pode descobrir que a direcionamento de uma versão atualizada e compatível de um assembly não é paga.</span><span class="sxs-lookup"><span data-stu-id="7b198-190">However, you can find that targeting an updated and compatible version of an assembly just doesn't pay off.</span></span> <span data-ttu-id="7b198-191">Se o custo da alteração não for aceitável, você poderá considerar a reversão de versões do pacote, mantendo aquelas que você usa em .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b198-191">If the cost of change isn't acceptable, you can consider rolling back package versions keeping the ones you use on .NET Framework.</span></span> <span data-ttu-id="7b198-192">Embora eles possam não ser direcionados ao .NET Core, eles devem funcionar bem, a menos que chamem algumas APIs sem suporte.</span><span class="sxs-lookup"><span data-stu-id="7b198-192">Although they may not be targeting .NET Core, they should work well unless they call some unsupported APIs.</span></span>

### <a name="run-and-test"></a><span data-ttu-id="7b198-193">Executar e testar</span><span class="sxs-lookup"><span data-stu-id="7b198-193">Run and test</span></span>

<span data-ttu-id="7b198-194">Depois de criar seu aplicativo sem erros, você pode iniciar a última etapa da migração testando cada funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="7b198-194">Once you have your application building with no errors, you can start the last step of the migration by testing every functionality.</span></span>

<span data-ttu-id="7b198-195">Nesta etapa final, você pode encontrar vários problemas diferentes dependendo da complexidade do seu aplicativo e das dependências e das APIs que você está usando.</span><span class="sxs-lookup"><span data-stu-id="7b198-195">In this final step, you can find several different issues depending on the complexity of your application and the dependencies and APIs you're using.</span></span>

<span data-ttu-id="7b198-196">Por exemplo, se você usar arquivos de configuração (*app. config*), poderá encontrar alguns erros em tempo de execução, como seções de configuração não presentes.</span><span class="sxs-lookup"><span data-stu-id="7b198-196">For example, if you use configuration files (*app.config*), you may find some errors at run time like Configuration Sections not present.</span></span> <span data-ttu-id="7b198-197">O uso do `Microsoft.Extensions.Configuration` pacote NuGet deve corrigir esse erro.</span><span class="sxs-lookup"><span data-stu-id="7b198-197">Using the `Microsoft.Extensions.Configuration` NuGet package should fix that error.</span></span>

<span data-ttu-id="7b198-198">Outro motivo para erros é o uso dos `BeginInvoke` métodos e `EndInvoke` porque eles não têm suporte no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-198">Another reason for errors is the use of the `BeginInvoke` and `EndInvoke` methods because they aren't supported on .NET Core.</span></span> <span data-ttu-id="7b198-199">Eles não têm suporte no .NET Core porque têm uma dependência de comunicação remota, que não existe no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-199">They aren't supported on .NET Core because they have a dependency on Remoting, which doesn't exist on .NET Core.</span></span> <span data-ttu-id="7b198-200">Para resolver esse problema, tente usar a `await` palavra-chave (quando disponível) ou o <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="7b198-200">To solve this issue, try to use the `await` keyword (when available) or the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="7b198-201">Você pode usar analisadores de compatibilidade para permitir que você identifique APIs e padrões de código em seu código que podem causar problemas em tempo de execução com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-201">You can use compatibility analyzers to let you identify APIs and code patterns in your code that can potentially cause problems at run time with .NET Core.</span></span> <span data-ttu-id="7b198-202">Vá para <http://github.com/dotnet/platform-compat> e use o analisador de API do .net em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7b198-202">Go to <http://github.com/dotnet/platform-compat> and use the .NET API analyzer on your project.</span></span>

## <a name="migrating-a-windows-forms-application"></a><span data-ttu-id="7b198-203">Migrando um aplicativo Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7b198-203">Migrating a Windows Forms application</span></span>

<span data-ttu-id="7b198-204">Para demonstrar um processo de migração completo de um aplicativo Windows Forms, optamos por migrar o aplicativo de exemplo eShop disponível em <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="7b198-204">To showcase a complete migration process of a Windows Forms application, we've chosen to migrate the eShop sample application available at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms>.</span></span> <span data-ttu-id="7b198-205">Você pode encontrar o resultado completo da migração em <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="7b198-205">You can find the complete result of the migration at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms>.</span></span>

<span data-ttu-id="7b198-206">Este aplicativo mostra um catálogo de produtos e permite que o usuário navegue, filtre e pesquise produtos.</span><span class="sxs-lookup"><span data-stu-id="7b198-206">This application shows a product catalog and allows the user to navigate, filter, and search for products.</span></span> <span data-ttu-id="7b198-207">Do ponto de vista da arquitetura, o aplicativo depende de um serviço WCF externo que serve como uma fachada para um banco de dados back-end.</span><span class="sxs-lookup"><span data-stu-id="7b198-207">From an architecture point of view, the app relies on an external WCF service that serves as a façade to a back-end database.</span></span>

<span data-ttu-id="7b198-208">Você pode ver a janela principal do aplicativo na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="7b198-208">You can see the main application window in the following picture:</span></span>

![Janela principal do aplicativo](./media/example-migration-core/main-application-window.png)

<span data-ttu-id="7b198-210">Se você abrir o arquivo de projeto *. csproj* , poderá ver algo assim:</span><span class="sxs-lookup"><span data-stu-id="7b198-210">If you open the *.csproj* project file, you can see something like this:</span></span>

![Captura de tela do conteúdo do arquivo csproj](./media/example-migration-core/csproj-file.png)

<span data-ttu-id="7b198-212">Como mencionado anteriormente, o projeto do .NET Core tem um estilo mais compacto e você precisa migrar a estrutura do projeto para o novo estilo de SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-212">As previously mentioned, .NET Core project has a more compact style and you need to migrate the project structure to the new .NET Core SDK style.</span></span>

<span data-ttu-id="7b198-213">Na Gerenciador de soluções, clique com o botão direito do mouse no projeto Windows Forms e selecione **descarregar**  >  **edição**do projeto.</span><span class="sxs-lookup"><span data-stu-id="7b198-213">In the Solution Explorer, right click on the Windows Forms project and select **Unload Project** > **Edit**.</span></span>

<span data-ttu-id="7b198-214">Agora você pode atualizar o arquivo. csproj.</span><span class="sxs-lookup"><span data-stu-id="7b198-214">Now you can update the .csproj file.</span></span> <span data-ttu-id="7b198-215">Você excluirá todo o conteúdo e o substituirá pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="7b198-215">You'll delete the entire content and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWindowsForms>true</UseWindowsForms>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="7b198-216">Salve e recarregue o projeto.</span><span class="sxs-lookup"><span data-stu-id="7b198-216">Save and reload the project.</span></span> <span data-ttu-id="7b198-217">Agora você concluiu a atualização do arquivo de projeto e o projeto está direcionando o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-217">You're now done updating the project file and the project is targeting the .NET Core.</span></span>

<span data-ttu-id="7b198-218">Se você compilar o projeto neste ponto, encontrará alguns erros relacionados à referência do cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="7b198-218">If you compile the project at this point, you'll find some errors related to the WCF client reference.</span></span> <span data-ttu-id="7b198-219">Como esse código é gerado automaticamente, você deve gerá-lo novamente para o .NET Core de destino.</span><span class="sxs-lookup"><span data-stu-id="7b198-219">Since this code is autogenerated, you must regenerate it to target .NET Core.</span></span>

![Captura de tela de erros de compilação no Visual Studio](./media/example-migration-core/winforms-compilation-errors.png)

<span data-ttu-id="7b198-221">Exclua o arquivo *Reference.cs* e gere um novo cliente de serviço.</span><span class="sxs-lookup"><span data-stu-id="7b198-221">Delete the *Reference.cs* file and generate a new Service Client.</span></span>

<span data-ttu-id="7b198-222">Clique com o botão direito do mouse em **Serviços conectados** e selecione a opção **Adicionar serviço conectado** .</span><span class="sxs-lookup"><span data-stu-id="7b198-222">Right-click on **Connected Services** and select the **Add Connected Service** option.</span></span>

![Captura de tela do menu serviços conectados com a opção Adicionar serviço conectado selecionada](./media/example-migration-core/add-connected-service.png)

<span data-ttu-id="7b198-224">A janela Serviços conectados é aberta.</span><span class="sxs-lookup"><span data-stu-id="7b198-224">The Connected Services window opens.</span></span> <span data-ttu-id="7b198-225">Selecione a opção **Microsoft WCF Web Service** .</span><span class="sxs-lookup"><span data-stu-id="7b198-225">Select the **Microsoft WCF Web Service** option.</span></span>

![Captura de tela da janela de serviços conectados](./media/example-migration-core/connected-services-window.png)

<span data-ttu-id="7b198-227">Se você tiver o serviço WCF na mesma solução que temos neste exemplo, você pode selecionar a opção **Discover** em vez de especificar uma URL de serviço.</span><span class="sxs-lookup"><span data-stu-id="7b198-227">If you have the WCF Service in the same solution as we have in this example, you can select the **Discover** option instead of specifying a service URL.</span></span>

![Captura de tela da janela Configurar referência do serviço Web WCF](./media/example-migration-core/configure-wcf-reference.png)

<span data-ttu-id="7b198-229">Quando o serviço estiver localizado, a ferramenta refletirá o contrato de API implementado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="7b198-229">Once the service is located, the tool reflects the API contract implemented by the service.</span></span> <span data-ttu-id="7b198-230">Altere o nome do namespace para que ele seja `eShopServiceReference` conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="7b198-230">Change the name of the namespace to be `eShopServiceReference` as shown in the following image:</span></span>

![Captura de tela do contrato de API e o namespace alterado](./media/example-migration-core/api-contract-namespace.png)

<span data-ttu-id="7b198-232">Selecione o botão **concluir** .</span><span class="sxs-lookup"><span data-stu-id="7b198-232">Select the **Finish** button.</span></span> <span data-ttu-id="7b198-233">Após alguns instantes, você verá o código gerado.</span><span class="sxs-lookup"><span data-stu-id="7b198-233">After a while, you'll see the generated code.</span></span>

<span data-ttu-id="7b198-234">Você deve ver três arquivos gerados automaticamente:</span><span class="sxs-lookup"><span data-stu-id="7b198-234">You should see three autogenerated files:</span></span>

1. <span data-ttu-id="7b198-235">*Introdução*: um link para o GitHub para fornecer algumas informações sobre o WCF.</span><span class="sxs-lookup"><span data-stu-id="7b198-235">*Getting Started*: a link to GitHub to provide some information on WCF.</span></span>
2. <span data-ttu-id="7b198-236">*ConnectedService. JSON*: parâmetros de configuração para se conectar ao serviço.</span><span class="sxs-lookup"><span data-stu-id="7b198-236">*ConnectedService.json*: configuration parameters to connect to the service.</span></span>
3. <span data-ttu-id="7b198-237">*Reference.cs*: o código do cliente WCF real.</span><span class="sxs-lookup"><span data-stu-id="7b198-237">*Reference.cs*: the actual WCF client code.</span></span>

![Captura de tela da janela de Gerenciador de Soluções com os três arquivos gerados automaticamente](./media/example-migration-core/autogenerated-files.png)

<span data-ttu-id="7b198-239">Se você compilar novamente, verá muitos erros provenientes de arquivos *. cs* dentro da pasta *auxiliar* .</span><span class="sxs-lookup"><span data-stu-id="7b198-239">If you compile again, you'll see many errors coming from *.cs* files inside the *Helper* folder.</span></span> <span data-ttu-id="7b198-240">Essa pasta estava presente na versão .NET Framework, mas não está incluída no Old *. csproj*.</span><span class="sxs-lookup"><span data-stu-id="7b198-240">This folder was present in the .NET Framework version but not included in the old *.csproj*.</span></span> <span data-ttu-id="7b198-241">Mas com o novo projeto no estilo SDK, todos os arquivos de código presentes abaixo do local do arquivo de projeto são incluídos por padrão.</span><span class="sxs-lookup"><span data-stu-id="7b198-241">But with the new SDK-style project, every code file present underneath the project file location is included by default.</span></span> <span data-ttu-id="7b198-242">Ou seja, o novo projeto .NET Core tenta compilar os arquivos dentro da pasta *auxiliar* .</span><span class="sxs-lookup"><span data-stu-id="7b198-242">That is, the new .NET Core project tries to compile the files inside the *Helper* folder.</span></span> <span data-ttu-id="7b198-243">Como essa pasta não é necessária, você pode excluí-la com segurança.</span><span class="sxs-lookup"><span data-stu-id="7b198-243">Since that folder isn't needed, you can safely delete it.</span></span>

<span data-ttu-id="7b198-244">Se você compilar o projeto novamente e executá-lo, não verá as imagens do produto.</span><span class="sxs-lookup"><span data-stu-id="7b198-244">If you compile the project again and execute it, you won't see the product images.</span></span> <span data-ttu-id="7b198-245">O problema é que agora o caminho para os arquivos foi ligeiramente alterado.</span><span class="sxs-lookup"><span data-stu-id="7b198-245">The problem is that now the path to the files has slightly changed.</span></span> <span data-ttu-id="7b198-246">Para corrigir esse problema, você precisa adicionar outro nível de profundidade no caminho, atualizando no arquivo `CatalogView.cs` a linha:</span><span class="sxs-lookup"><span data-stu-id="7b198-246">To fix this issue, you need to add another level of depth in the path, updating in the file `CatalogView.cs` the line:</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="7b198-247">para</span><span class="sxs-lookup"><span data-stu-id="7b198-247">to</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="7b198-248">Após essa alteração, você pode verificar se o aplicativo é iniciado e executado conforme o esperado no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-248">After this change, you can check that the application launches and runs as expected on .NET Core.</span></span>

## <a name="migrating-a-wpf-application"></a><span data-ttu-id="7b198-249">Migrando um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="7b198-249">Migrating a WPF application</span></span>

<span data-ttu-id="7b198-250">Usaremos o aplicativo de `Shop.ClassicWPF` exemplo para executar a migração.</span><span class="sxs-lookup"><span data-stu-id="7b198-250">We'll use the `Shop.ClassicWPF` sample application to perform the migration.</span></span> <span data-ttu-id="7b198-251">A imagem a seguir mostra uma captura de tela do aplicativo antes da migração:</span><span class="sxs-lookup"><span data-stu-id="7b198-251">The following image shows a screenshot of the app before migration:</span></span>

![Aplicativo de exemplo antes da migração](./media/example-migration-core/app-before-migration.png)

<span data-ttu-id="7b198-253">Esse aplicativo usa um banco de dados SQL Server Express local para armazenar as informações do catálogo de produtos.</span><span class="sxs-lookup"><span data-stu-id="7b198-253">This application uses a local SQL Server Express database to hold the product catalog information.</span></span> <span data-ttu-id="7b198-254">Esse banco de dados é acessado diretamente do aplicativo do WPF.</span><span class="sxs-lookup"><span data-stu-id="7b198-254">This database is accessed directly from the WPF application.</span></span>

<span data-ttu-id="7b198-255">Primeiro, você deve atualizar o arquivo *. csproj* para o novo estilo do SDK usado por aplicativos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-255">First, you must update the *.csproj* file to the new SDK style used by .NET Core applications.</span></span> <span data-ttu-id="7b198-256">Você seguirá as mesmas etapas descritas na Windows Forms migração: você descarregará o projeto, abrirá o arquivo *. csproj* , atualizará seu conteúdo e recarregará o projeto.</span><span class="sxs-lookup"><span data-stu-id="7b198-256">You'll follow the same steps described in the Windows Forms migration: you'll unload the project, open the *.csproj* file, update its contents, and reload the project.</span></span>

<span data-ttu-id="7b198-257">Nesse caso, exclua todo o conteúdo do arquivo *. csproj* e substitua-o pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="7b198-257">In this case, delete all the content of the *.csproj* file and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWPF>true</UseWPF>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="7b198-258">Se você recarregar o projeto e compilá-lo, obterá o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="7b198-258">If you reload the project and compile it, you'll get the following error:</span></span>

![Captura de tela de erros de compilação no Visual Studio](./media/example-migration-core/wpf-compilation-error.png)

<span data-ttu-id="7b198-260">Como você excluiu todo o conteúdo *. csproj* , você perdeu uma especificação de referência de projeto presente no projeto antigo.</span><span class="sxs-lookup"><span data-stu-id="7b198-260">Since you've deleted all the *.csproj* contents, you've lost a project reference specification present in the old project.</span></span> <span data-ttu-id="7b198-261">Você só precisa adicionar essa linha ao arquivo *. csproj* para incluir a referência do projeto de volta:</span><span class="sxs-lookup"><span data-stu-id="7b198-261">You just need to add this line to the *.csproj* file to include the project reference back:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

<span data-ttu-id="7b198-262">Você também pode permitir que o Visual Studio o ajude clicando com o botão direito do mouse no nó **dependências** e selecionando **Adicionar referência de projeto**.</span><span class="sxs-lookup"><span data-stu-id="7b198-262">You can also let Visual Studio help you by right-clicking on the **Dependencies** node and selecting **Add Project Reference**.</span></span> <span data-ttu-id="7b198-263">Selecione o projeto da solução e clique em **OK**:</span><span class="sxs-lookup"><span data-stu-id="7b198-263">Select the project from the solution and click **OK**:</span></span>

![Captura de tela da caixa de diálogo Gerenciador de referências com o projeto eShop. sqlfornecetor selecionado](./media/example-migration-core/reference-manager.png)

<span data-ttu-id="7b198-265">Depois de adicionar a referência de projeto ausente, o aplicativo é compilado e executado conforme o esperado no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b198-265">Once you add the missing project reference, the application compiles and runs as expected on .NET Core.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7b198-266">[Anterior](windows-migration.md) 
> [Avançar](deploy-modern-applications.md)</span><span class="sxs-lookup"><span data-stu-id="7b198-266">[Previous](windows-migration.md)
[Next](deploy-modern-applications.md)</span></span>
