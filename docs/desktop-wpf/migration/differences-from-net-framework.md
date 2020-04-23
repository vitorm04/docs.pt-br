---
title: Diferenças entre o .NET Framework e o .NET Core
description: Descreve as diferenças entre a implementação de .NET Framework do Windows Presentation Foundation (WPF) e do WPF do .NET Core. Ao migrar seu aplicativo, você deve considerar essas incompatibilidades.
author: thraka
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 341e576f17c522fbcbb9c417176e9d4a13ab1b18
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82072203"
---
# <a name="differences-in-wpf"></a><span data-ttu-id="c407f-104">Diferenças no WPF</span><span class="sxs-lookup"><span data-stu-id="c407f-104">Differences in WPF</span></span>

<span data-ttu-id="c407f-105">Este artigo descreve as diferenças entre Windows Presentation Foundation (WPF) no .NET Core e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c407f-105">This article describes the differences between Windows Presentation Foundation (WPF) on .NET Core and .NET Framework.</span></span> <span data-ttu-id="c407f-106">O WPF para .NET Core é uma [estrutura de código-fonte aberto](https://github.com/dotnet/wpf) bifurcada do WPF original para .NET Framework código-fonte.</span><span class="sxs-lookup"><span data-stu-id="c407f-106">WPF for .NET Core is an [open-source framework](https://github.com/dotnet/wpf) forked from the original WPF for .NET Framework source code.</span></span>

<span data-ttu-id="c407f-107">Há alguns recursos de .NET Framework para os quais o .NET Core não dá suporte.</span><span class="sxs-lookup"><span data-stu-id="c407f-107">There are a few features of .NET Framework that .NET Core doesn't support.</span></span> <span data-ttu-id="c407f-108">Para obter mais informações sobre tecnologias sem suporte, consulte [.NET Framework Technologies indisponíveis no .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="c407f-108">For more information on unsupported technologies, see [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a><span data-ttu-id="c407f-109">Projetos no estilo SDK</span><span class="sxs-lookup"><span data-stu-id="c407f-109">SDK-style projects</span></span>

<span data-ttu-id="c407f-110">O .NET Core usa arquivos de projeto no estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="c407f-110">.NET Core uses SDK-style project files.</span></span> <span data-ttu-id="c407f-111">Esses arquivos de projeto são diferentes dos arquivos de projeto .NET Framework tradicionais gerenciados pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c407f-111">These project files are different from the traditional .NET Framework project files managed by Visual Studio.</span></span> <span data-ttu-id="c407f-112">Para migrar seus aplicativos .NET Framework WPF para o .NET Core, você deve converter seus projetos.</span><span class="sxs-lookup"><span data-stu-id="c407f-112">To migrate your .NET Framework WPF apps to .NET Core, you must convert your projects.</span></span> <span data-ttu-id="c407f-113">Para obter mais informações, consulte [migrar aplicativos do WPF para o .NET Core 3,0](convert-project-from-net-framework.md).</span><span class="sxs-lookup"><span data-stu-id="c407f-113">For more information, see [Migrate WPF apps to .NET Core 3.0](convert-project-from-net-framework.md).</span></span>

## <a name="nuget-package-references"></a><span data-ttu-id="c407f-114">Referências do pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="c407f-114">NuGet package references</span></span>

<span data-ttu-id="c407f-115">Se seu aplicativo .NET Framework listar suas dependências do NuGet em um arquivo *Packages. config* , migre para o [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) formato:</span><span class="sxs-lookup"><span data-stu-id="c407f-115">If your .NET Framework app lists its NuGet dependencies in a *packages.config* file, migrate to the [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) format:</span></span>

1. <span data-ttu-id="c407f-116">No Visual Studio, abra o painel **Gerenciador de soluções** .</span><span class="sxs-lookup"><span data-stu-id="c407f-116">In Visual Studio, open the **Solution Explorer** pane.</span></span>
1. <span data-ttu-id="c407f-117">Em seu projeto do WPF, clique com o botão direito do mouse em **Packages. config** > **Migrate Packages. config para PackageReference**.</span><span class="sxs-lookup"><span data-stu-id="c407f-117">In your WPF project, right-click **packages.config** > **Migrate packages.config to PackageReference**.</span></span>

![Atualizando para o PackageReference](media/differences-from-net-framework/package-reference-migration.png)

<span data-ttu-id="c407f-119">Uma caixa de diálogo será exibida mostrando as dependências do NuGet de nível superior calculadas e perguntando quais outros pacotes NuGet devem ser promovidos para o nível superior.</span><span class="sxs-lookup"><span data-stu-id="c407f-119">A dialog will appear showing calculated top-level NuGet dependencies and asking which other NuGet packages should be promoted to top level.</span></span> <span data-ttu-id="c407f-120">Selecione **OK** e o arquivo *Packages. config* será removido do projeto e `<PackageReference>` os elementos serão adicionados ao arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="c407f-120">Select **OK** and the *packages.config* file will be removed from the project and `<PackageReference>` elements will be added to the project file.</span></span>

<span data-ttu-id="c407f-121">Quando seu projeto usa `<PackageReference>`, os pacotes não são armazenados localmente em uma pasta de *pacotes* , eles são armazenados globalmente.</span><span class="sxs-lookup"><span data-stu-id="c407f-121">When your project uses `<PackageReference>`, packages aren't stored locally in a *Packages* folder, they're stored globally.</span></span> <span data-ttu-id="c407f-122">Abra o arquivo de projeto e remova `<Analyzer>` todos os elementos que referenciaram a pasta *pacotes* .</span><span class="sxs-lookup"><span data-stu-id="c407f-122">Open the project file and remove any `<Analyzer>` elements that referred to the *Packages* folder.</span></span> <span data-ttu-id="c407f-123">Esses analisadores são incluídos automaticamente com as referências do pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="c407f-123">These analyzers are automatically included with the NuGet package references.</span></span>

## <a name="code-access-security"></a><span data-ttu-id="c407f-124">Segurança de Acesso do Código</span><span class="sxs-lookup"><span data-stu-id="c407f-124">Code Access Security</span></span>

<span data-ttu-id="c407f-125">A CAS (segurança de acesso ao código) não tem suporte do .NET Core ou do WPF para .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c407f-125">Code Access Security (CAS) is not supported by .NET Core or WPF for .NET Core.</span></span> <span data-ttu-id="c407f-126">Todas as funcionalidades relacionadas ao CAS são tratadas sob a suposição de confiança total.</span><span class="sxs-lookup"><span data-stu-id="c407f-126">All CAS-related functionality is treated under the assumption of full-trust.</span></span> <span data-ttu-id="c407f-127">O WPF para .NET Core remove o código relacionado ao CAS.</span><span class="sxs-lookup"><span data-stu-id="c407f-127">WPF for .NET Core removes CAS-related code.</span></span> <span data-ttu-id="c407f-128">A superfície da API pública desses tipos ainda existe para garantir que as chamadas nesses tipos tenham sucesso.</span><span class="sxs-lookup"><span data-stu-id="c407f-128">The public API surface of these types still exists to ensure that calls into these types succeed.</span></span>

<span data-ttu-id="c407f-129">Os tipos relacionados ao CAS definidos publicamente foram movidos para fora dos assemblies do WPF e para os assemblies da biblioteca .NET principal.</span><span class="sxs-lookup"><span data-stu-id="c407f-129">Publicly defined CAS-related types were moved out of the WPF assemblies and into the Core .NET library assemblies.</span></span> <span data-ttu-id="c407f-130">Os assemblies do WPF têm o encaminhamento de tipo definido para o novo local dos tipos movidos.</span><span class="sxs-lookup"><span data-stu-id="c407f-130">The WPF assemblies have type-forwarding set to the new location of the moved types.</span></span>

| <span data-ttu-id="c407f-131">Assembly de origem</span><span class="sxs-lookup"><span data-stu-id="c407f-131">Source assembly</span></span> | <span data-ttu-id="c407f-132">Assembly de destino</span><span class="sxs-lookup"><span data-stu-id="c407f-132">Target assembly</span></span> | <span data-ttu-id="c407f-133">Type</span><span class="sxs-lookup"><span data-stu-id="c407f-133">Type</span></span>                |
| --------------- | --------------- | ------------------- |
| <span data-ttu-id="c407f-134">*WindowsBase.dll*</span><span class="sxs-lookup"><span data-stu-id="c407f-134">*WindowsBase.dll*</span></span> | <span data-ttu-id="c407f-135">*System. Security. Permissions. dll*</span><span class="sxs-lookup"><span data-stu-id="c407f-135">*System.Security.Permissions.dll*</span></span> | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| <span data-ttu-id="c407f-136">*System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="c407f-136">*System.Xaml.dll*</span></span> | <span data-ttu-id="c407f-137">*System. Security. Permissions. dll*</span><span class="sxs-lookup"><span data-stu-id="c407f-137">*System.Security.Permissions.dll*</span></span> | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| <span data-ttu-id="c407f-138">*System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="c407f-138">*System.Xaml.dll*</span></span> | <span data-ttu-id="c407f-139">*System. Windows. Extension. dll*</span><span class="sxs-lookup"><span data-stu-id="c407f-139">*System.Windows.Extension.dll*</span></span>    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> <span data-ttu-id="c407f-140">Para minimizar o conflito de portamento, a funcionalidade para armazenar e recuperar informações relacionadas às propriedades a seguir foi mantida no `XamlAccessLevel` tipo.</span><span class="sxs-lookup"><span data-stu-id="c407f-140">In order to minimize porting friction, the functionality for storing and retrieving information related to the following properties was retained in the `XamlAccessLevel` type.</span></span>
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a><span data-ttu-id="c407f-141">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c407f-141">Next steps</span></span>

- [<span data-ttu-id="c407f-142">Saiba como portar um aplicativo .NET Framework WPF para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c407f-142">Learn how to port a .NET Framework WPF app to .NET Core.</span></span>](convert-project-from-net-framework.md)
