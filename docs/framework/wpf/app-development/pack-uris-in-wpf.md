---
title: URIs "pack://" no WPF
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: 59c72d9ae12a014a8c47cb3b2852b337b173446c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580628"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="07e7a-102">URIs "pack://" no WPF</span><span class="sxs-lookup"><span data-stu-id="07e7a-102">Pack URIs in WPF</span></span>

<span data-ttu-id="07e7a-103">No Windows Presentation Foundation (WPF), os URIs (identificadores de recursos uniformes) são usados para identificar e carregar arquivos de várias maneiras, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="07e7a-103">In Windows Presentation Foundation (WPF), uniform resource identifiers (URIs) are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="07e7a-104">Especificar o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] a ser mostrado quando um aplicativo é iniciado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="07e7a-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="07e7a-105">Carregar imagens.</span><span class="sxs-lookup"><span data-stu-id="07e7a-105">Loading images.</span></span>

- <span data-ttu-id="07e7a-106">Navegar até as páginas.</span><span class="sxs-lookup"><span data-stu-id="07e7a-106">Navigating to pages.</span></span>

- <span data-ttu-id="07e7a-107">Carregar arquivos de dados não executáveis.</span><span class="sxs-lookup"><span data-stu-id="07e7a-107">Loading non-executable data files.</span></span>

<span data-ttu-id="07e7a-108">Além disso, os URIs podem ser usados para identificar e carregar arquivos de uma variedade de locais, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="07e7a-108">Furthermore, URIs can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="07e7a-109">O assembly atual.</span><span class="sxs-lookup"><span data-stu-id="07e7a-109">The current assembly.</span></span>

- <span data-ttu-id="07e7a-110">Um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="07e7a-110">A referenced assembly.</span></span>

- <span data-ttu-id="07e7a-111">Um local relativo a um assembly.</span><span class="sxs-lookup"><span data-stu-id="07e7a-111">A location relative to an assembly.</span></span>

- <span data-ttu-id="07e7a-112">O site de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-112">The application's site of origin.</span></span>

<span data-ttu-id="07e7a-113">Para fornecer um mecanismo consistente para identificar e carregar esses tipos de arquivos desses locais, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aproveita a extensibilidade do *esquema de URI de pacote*.</span><span class="sxs-lookup"><span data-stu-id="07e7a-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="07e7a-114">Este tópico fornece uma visão geral do esquema, aborda como construir URIs de pacote para uma variedade de cenários, discute URIs absolutos e relativos e resolução de URI, antes de mostrar como usar URIs de pacote de marcação e código.</span><span class="sxs-lookup"><span data-stu-id="07e7a-114">This topic provides an overview of the scheme, covers how to construct pack URIs for a variety of scenarios, discusses absolute and relative URIs and URI resolution, before showing how to use pack URIs from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="07e7a-115">O esquema de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="07e7a-115">The Pack URI Scheme</span></span>

<span data-ttu-id="07e7a-116">O esquema de URI de pacote é usado pela especificação OPC ( [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) ), que descreve um modelo para organizar e identificar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-116">The pack URI scheme is used by the [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="07e7a-117">Os principais elementos desse modelo são pacotes e partes, onde um *pacote* é um contêiner lógico para uma ou mais *partes*lógicas.</span><span class="sxs-lookup"><span data-stu-id="07e7a-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="07e7a-118">A imagem a seguir ilustra esse conceito.</span><span class="sxs-lookup"><span data-stu-id="07e7a-118">The following figure illustrates this concept.</span></span>

![Diagrama de partes e pacote](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="07e7a-120">Para identificar partes, a especificação OPC aproveita a extensibilidade do RFC 2396 (Uniform Resource Identifiers (URI): sintaxe genérica) para definir o esquema de URI de pacote.</span><span class="sxs-lookup"><span data-stu-id="07e7a-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack URI scheme.</span></span>

<span data-ttu-id="07e7a-121">O esquema especificado por um URI é definido por seu prefixo; http, FTP e arquivo são exemplos bem conhecidos.</span><span class="sxs-lookup"><span data-stu-id="07e7a-121">The scheme that is specified by a URI is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="07e7a-122">O esquema de URI de pacote usa "Pack" como seu esquema e contém dois componentes: autoridade e caminho.</span><span class="sxs-lookup"><span data-stu-id="07e7a-122">The pack URI scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="07e7a-123">A seguir está o formato de um pacote URI.</span><span class="sxs-lookup"><span data-stu-id="07e7a-123">The following is the format for a pack URI.</span></span>

<span data-ttu-id="07e7a-124">*caminho* de / de*autoridade* Pack://</span><span class="sxs-lookup"><span data-stu-id="07e7a-124">pack://*authority*/*path*</span></span>

<span data-ttu-id="07e7a-125">A *autoridade* especifica o tipo de pacote no qual uma parte está contida, enquanto o *caminho* especifica o local de uma parte dentro de um pacote.</span><span class="sxs-lookup"><span data-stu-id="07e7a-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="07e7a-126">Esse conceito é ilustrado pela figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="07e7a-126">This concept is illustrated by the following figure:</span></span>

![Relação entre pacote, autoridade e caminho](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="07e7a-128">Os pacotes e peças são análogos a aplicativos e arquivos, pois um aplicativo (pacote) pode incluir um ou mais arquivos (peças), incluindo:</span><span class="sxs-lookup"><span data-stu-id="07e7a-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="07e7a-129">Arquivos de recursos que são compilados no assembly local.</span><span class="sxs-lookup"><span data-stu-id="07e7a-129">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="07e7a-130">Arquivos de recursos que são compilados em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="07e7a-130">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="07e7a-131">Arquivos de recursos que são compilados em um assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="07e7a-131">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="07e7a-132">Arquivos de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-132">Content files.</span></span>

- <span data-ttu-id="07e7a-133">Arquivos de site de origem.</span><span class="sxs-lookup"><span data-stu-id="07e7a-133">Site of origin files.</span></span>

<span data-ttu-id="07e7a-134">Para acessar esses tipos de arquivos, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dá suporte a duas autoridades: application:///e siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="07e7a-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="07e7a-135">A autoridade application:/// identifica arquivos de dados de aplicativo que são conhecidos no tempo de compilação, incluindo arquivos de recurso e conteúdo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="07e7a-136">A autoridade siteoforigin:/// identifica arquivos de site de origem.</span><span class="sxs-lookup"><span data-stu-id="07e7a-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="07e7a-137">O escopo de cada autoridade é mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="07e7a-137">The scope of each authority is shown in the following figure.</span></span>

![Diagrama de URI de pacote](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="07e7a-139">O componente de autoridade de um URI de pacote é um URI inserido que aponta para um pacote e deve estar em conformidade com o RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="07e7a-139">The authority component of a pack URI is an embedded URI that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="07e7a-140">Além disso, o caractere “/” deve ser substituído pelo caractere “,”; caracteres reservados como “%” e “?” devem ser ignorados.</span><span class="sxs-lookup"><span data-stu-id="07e7a-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="07e7a-141">Para ver os detalhes, consulte o OPC.</span><span class="sxs-lookup"><span data-stu-id="07e7a-141">See the OPC for details.</span></span>

<span data-ttu-id="07e7a-142">As seções a seguir explicam como construir URIs de pacote usando essas duas autoridades em conjunto com os caminhos apropriados para identificar recursos, conteúdo e site de arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="07e7a-142">The following sections explain how to construct pack URIs using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="07e7a-143">URIs de pacote de arquivo de recurso</span><span class="sxs-lookup"><span data-stu-id="07e7a-143">Resource File Pack URIs</span></span>

<span data-ttu-id="07e7a-144">Os arquivos de recurso são configurados como MSBuild `Resource` itens e são compilados em assemblies.</span><span class="sxs-lookup"><span data-stu-id="07e7a-144">Resource files are configured as MSBuild `Resource` items and are compiled into assemblies.</span></span> <span data-ttu-id="07e7a-145">O WPF dá suporte à construção de URIs de pacote que podem ser usados para identificar arquivos de recursos que são compilados no assembly local ou compilados em um assembly que é referenciado do assembly local.</span><span class="sxs-lookup"><span data-stu-id="07e7a-145">WPF supports the construction of pack URIs that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="07e7a-146">Arquivo de recurso de assembly local</span><span class="sxs-lookup"><span data-stu-id="07e7a-146">Local Assembly Resource File</span></span>

<span data-ttu-id="07e7a-147">O pacote URI para um arquivo de recurso que é compilado no assembly local usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="07e7a-147">The pack URI for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="07e7a-148">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="07e7a-148">**Authority**: application:///.</span></span>

- <span data-ttu-id="07e7a-149">**Caminho**: o nome do arquivo de recurso, incluindo seu caminho, em relação à raiz da pasta de projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="07e7a-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="07e7a-150">O exemplo a seguir mostra o pacote URI para um arquivo de recurso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que está localizado na raiz da pasta do projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="07e7a-150">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="07e7a-151">O exemplo a seguir mostra o pacote URI para um arquivo de recurso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que está localizado em uma subpasta da pasta do projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="07e7a-151">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="07e7a-152">Arquivo de recurso de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="07e7a-152">Referenced Assembly Resource File</span></span>

<span data-ttu-id="07e7a-153">O pacote URI para um arquivo de recurso que é compilado em um assembly referenciado usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="07e7a-153">The pack URI for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="07e7a-154">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="07e7a-154">**Authority**: application:///.</span></span>

- <span data-ttu-id="07e7a-155">**Caminho**: o nome de um arquivo de recurso compilado em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="07e7a-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="07e7a-156">O caminho deve estar de acordo com o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="07e7a-156">The path must conform to the following format:</span></span>

  <span data-ttu-id="07e7a-157">*AssemblyShortName*{ *; Versão*] { *; PublicKey*]; componente/*caminho*</span><span class="sxs-lookup"><span data-stu-id="07e7a-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="07e7a-158">**AssemblyShortName**: o nome curto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="07e7a-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="07e7a-159">**;Version** [opcional]: a versão do assembly referenciado que contém o arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="07e7a-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="07e7a-160">É usada quando são carregados dois ou mais assemblies referenciados com o mesmo nome curto.</span><span class="sxs-lookup"><span data-stu-id="07e7a-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="07e7a-161">**;PublicKey** [opcional]: a chave pública que foi usada para assinar o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="07e7a-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="07e7a-162">É usada quando são carregados dois ou mais assemblies referenciados com o mesmo nome curto.</span><span class="sxs-lookup"><span data-stu-id="07e7a-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="07e7a-163">**;component**: especifica que o assembly referenciado é referenciado a partir do assembly local.</span><span class="sxs-lookup"><span data-stu-id="07e7a-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="07e7a-164">**/Path**: o nome do arquivo de recurso, incluindo o caminho, em relação à raiz da pasta de projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="07e7a-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="07e7a-165">O exemplo a seguir mostra o pacote URI para um arquivo de recurso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que está localizado na raiz da pasta do projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="07e7a-165">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="07e7a-166">O exemplo a seguir mostra o pacote URI para um arquivo de recurso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que está localizado em uma subpasta da pasta do projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="07e7a-166">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="07e7a-167">O exemplo a seguir mostra o pacote URI para um arquivo de recurso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que está localizado na pasta raiz de uma pasta de projeto de assembly específica de versão referenciada.</span><span class="sxs-lookup"><span data-stu-id="07e7a-167">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="07e7a-168">Observe que a sintaxe do pack URI para arquivos de recurso de assembly referenciados pode ser usada somente com a autoridade application:///.</span><span class="sxs-lookup"><span data-stu-id="07e7a-168">Note that the pack URI syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="07e7a-169">Por exemplo, não há suporte para o seguinte no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07e7a-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="07e7a-170">URIs de pacote de arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="07e7a-170">Content File Pack URIs</span></span>

<span data-ttu-id="07e7a-171">O pacote URI para um arquivo de conteúdo usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="07e7a-171">The pack URI for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="07e7a-172">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="07e7a-172">**Authority**: application:///.</span></span>

- <span data-ttu-id="07e7a-173">**Caminho**: o nome do arquivo de conteúdo, incluindo o caminho em relação ao local do sistema de arquivos do principal assembly executável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="07e7a-174">O exemplo a seguir mostra o pacote URI para um arquivo de conteúdo de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], localizado na mesma pasta que o assembly executável.</span><span class="sxs-lookup"><span data-stu-id="07e7a-174">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="07e7a-175">O exemplo a seguir mostra o pacote URI para um arquivo de conteúdo de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], localizado em uma subpasta que é relativa ao assembly executável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-175">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> <span data-ttu-id="07e7a-176">Não é possível navegar para arquivos de conteúdo HTML.</span><span class="sxs-lookup"><span data-stu-id="07e7a-176">HTML content files cannot be navigated to.</span></span> <span data-ttu-id="07e7a-177">O esquema de URI dá suporte apenas à navegação para arquivos HTML que estão localizados no site de origem.</span><span class="sxs-lookup"><span data-stu-id="07e7a-177">The URI scheme only supports navigation to HTML files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="07e7a-178">URIs de pacote de site de origem</span><span class="sxs-lookup"><span data-stu-id="07e7a-178">Site of Origin Pack URIs</span></span>

<span data-ttu-id="07e7a-179">O URI do pacote para um arquivo de site de origem usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="07e7a-179">The pack URI for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="07e7a-180">**Autoridade**: siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="07e7a-180">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="07e7a-181">**Caminho**: o nome do arquivo de site de origem, incluindo o caminho em relação ao local a partir do qual o assembly executável foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="07e7a-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="07e7a-182">O exemplo a seguir mostra o pacote URI para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site de origem de arquivo, armazenado no local do qual o assembly executável é iniciado.</span><span class="sxs-lookup"><span data-stu-id="07e7a-182">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="07e7a-183">O exemplo a seguir mostra o pacote URI para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site de origem de arquivo, armazenado na subpasta que é relativa ao local do qual o assembly executável do aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="07e7a-183">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="07e7a-184">Arquivos de paginação</span><span class="sxs-lookup"><span data-stu-id="07e7a-184">Page Files</span></span>

<span data-ttu-id="07e7a-185">Os arquivos XAML que são configurados como MSBuild `Page` itens são compilados em assemblies da mesma maneira que os arquivos de recursos.</span><span class="sxs-lookup"><span data-stu-id="07e7a-185">XAML files that are configured as MSBuild `Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="07e7a-186">Consequentemente, os itens do MSBuild `Page` podem ser identificados usando URIs de pacote para arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="07e7a-186">Consequently, MSBuild `Page` items can be identified using pack URIs for resource files.</span></span>

<span data-ttu-id="07e7a-187">Os tipos de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos que normalmente são configurados como MSBuild `Page` itens têm um dos seguintes como seu elemento raiz:</span><span class="sxs-lookup"><span data-stu-id="07e7a-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as MSBuild`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="07e7a-188">URIs de pacote absoluto versus relativo</span><span class="sxs-lookup"><span data-stu-id="07e7a-188">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="07e7a-189">Um URI de pacote totalmente qualificado inclui o esquema, a autoridade e o caminho, e é considerado um URI de pacote absoluto.</span><span class="sxs-lookup"><span data-stu-id="07e7a-189">A fully qualified pack URI includes the scheme, the authority, and the path, and it is considered an absolute pack URI.</span></span> <span data-ttu-id="07e7a-190">Como uma simplificação para os desenvolvedores, os elementos de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] geralmente permitem que você defina atributos apropriados com um URI de pacote relativo, que inclui apenas o caminho.</span><span class="sxs-lookup"><span data-stu-id="07e7a-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack URI, which includes only the path.</span></span>

<span data-ttu-id="07e7a-191">Por exemplo, considere o seguinte URI de pacote absoluto para um arquivo de recurso no assembly local.</span><span class="sxs-lookup"><span data-stu-id="07e7a-191">For example, consider the following absolute pack URI for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="07e7a-192">O URI de pacote relativo que se refere a esse arquivo de recurso seria o seguinte.</span><span class="sxs-lookup"><span data-stu-id="07e7a-192">The relative pack URI that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="07e7a-193">Como os arquivos de site de origem não estão associados a assemblies, eles só podem ser referidos com URIs de pacote absolutos.</span><span class="sxs-lookup"><span data-stu-id="07e7a-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack URIs.</span></span>

<span data-ttu-id="07e7a-194">Por padrão, um URI de pacote relativo é considerado relativo ao local da marcação ou código que contém a referência.</span><span class="sxs-lookup"><span data-stu-id="07e7a-194">By default, a relative pack URI is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="07e7a-195">No entanto, se uma barra invertida à esquerda for usada, a referência de URI de pacote relativa será considerada relativa à raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-195">If a leading backslash is used, however, the relative pack URI reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="07e7a-196">Considere, por exemplo, a estrutura de projeto a seguir.</span><span class="sxs-lookup"><span data-stu-id="07e7a-196">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="07e7a-197">Se página1. XAML contiver um URI que faz referência a \SubFolder\Page2.XAML *raiz*, a referência poderá usar o seguinte URI de pacote relativo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-197">If Page1.xaml contains a URI that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`Page2.xaml`

<span data-ttu-id="07e7a-198">Se página1. XAML contiver um URI que faz referência a \Page2.XAML *raiz*, a referência poderá usar o seguinte URI de pacote relativo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-198">If Page1.xaml contains a URI that references *Root*\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="07e7a-199">Resolução de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="07e7a-199">Pack URI Resolution</span></span>

<span data-ttu-id="07e7a-200">O formato dos URIs de pacote possibilita que URIs de pacote para diferentes tipos de arquivos tenham a mesma aparência.</span><span class="sxs-lookup"><span data-stu-id="07e7a-200">The format of pack URIs makes it possible for pack URIs for different types of files to look the same.</span></span> <span data-ttu-id="07e7a-201">Por exemplo, considere o seguinte URI absoluto do pacote.</span><span class="sxs-lookup"><span data-stu-id="07e7a-201">For example, consider the following absolute pack URI.</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="07e7a-202">Esse URI de pacote absoluto pode se referir a um arquivo de recurso no assembly local ou um arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-202">This absolute pack URI could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="07e7a-203">O mesmo é verdadeiro para o seguinte URI relativo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-203">The same is true for the following relative URI.</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="07e7a-204">Para determinar o tipo de arquivo ao qual um URI de pacote se refere, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolve URIs para arquivos de recursos em assemblies locais e arquivos de conteúdo usando a seguinte heurística:</span><span class="sxs-lookup"><span data-stu-id="07e7a-204">In order to determine the type of file that a pack URI refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves URIs for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="07e7a-205">Investigue os metadados do assembly para um atributo <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> que corresponda ao URI do pacote.</span><span class="sxs-lookup"><span data-stu-id="07e7a-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack URI.</span></span>

2. <span data-ttu-id="07e7a-206">Se o atributo <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> for encontrado, o caminho do URI do pacote se referirá a um arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack URI refers to a content file.</span></span>

3. <span data-ttu-id="07e7a-207">Se o atributo <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> não for encontrado, investigue os arquivos de recurso definidos que são compilados no assembly local.</span><span class="sxs-lookup"><span data-stu-id="07e7a-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="07e7a-208">Se um arquivo de recurso que corresponde ao caminho do URI do pacote for encontrado, o caminho do pacote URI se referirá a um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="07e7a-208">If a resource file that matches the path of the pack URI is found, the path of the pack URI refers to a resource file.</span></span>

5. <span data-ttu-id="07e7a-209">Se o recurso não for encontrado, o <xref:System.Uri> criado internamente será inválido.</span><span class="sxs-lookup"><span data-stu-id="07e7a-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

<span data-ttu-id="07e7a-210">A resolução de URI não se aplica a URIs que se referem ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="07e7a-210">URI resolution does not apply for URIs that refer to the following:</span></span>

- <span data-ttu-id="07e7a-211">Arquivos de conteúdo em assemblies referenciados: não há suporte para esses tipos de arquivo pelo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07e7a-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

- <span data-ttu-id="07e7a-212">Arquivos inseridos em assemblies referenciados: URIs que os identificam são exclusivos porque incluem o nome do assembly referenciado e o sufixo `;component`.</span><span class="sxs-lookup"><span data-stu-id="07e7a-212">Embedded files in referenced assemblies: URIs that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="07e7a-213">Arquivos de site de origem: os URIs que os identificam são exclusivos porque são os únicos arquivos que podem ser identificados por URIs de pacote que contêm a autoridade siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="07e7a-213">Site of origin files: URIs that identify them are unique because they are the only files that can be identified by pack URIs that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="07e7a-214">Uma simplificação que a resolução de URI de pacote permite é que o código seja, de certa forma, independente dos locais dos arquivos de conteúdo e de recursos.</span><span class="sxs-lookup"><span data-stu-id="07e7a-214">One simplification that pack URI resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="07e7a-215">Por exemplo, se você tiver um arquivo de recurso no assembly local que é reconfigurado para ser um arquivo de conteúdo, o pacote URI para o recurso permanecerá o mesmo, assim como o código que usa o pack URI.</span><span class="sxs-lookup"><span data-stu-id="07e7a-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack URI for the resource remains the same, as does the code that uses the pack URI.</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="07e7a-216">Programando com URIs de pacote</span><span class="sxs-lookup"><span data-stu-id="07e7a-216">Programming with Pack URIs</span></span>

<span data-ttu-id="07e7a-217">Muitas classes de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implementam propriedades que podem ser definidas com URIs de pacote, incluindo:</span><span class="sxs-lookup"><span data-stu-id="07e7a-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack URIs, including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="07e7a-218">Essas propriedades podem ser definidas a partir de marcação e código.</span><span class="sxs-lookup"><span data-stu-id="07e7a-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="07e7a-219">Esta seção demonstra as construções básicas para ambos e, depois, mostra exemplos de cenários comuns.</span><span class="sxs-lookup"><span data-stu-id="07e7a-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="07e7a-220">Utilizando URIs de pacote em marcação</span><span class="sxs-lookup"><span data-stu-id="07e7a-220">Using Pack URIs in Markup</span></span>

<span data-ttu-id="07e7a-221">Um URI de pacote é especificado na marcação definindo o elemento de um atributo com o URI pack.</span><span class="sxs-lookup"><span data-stu-id="07e7a-221">A pack URI is specified in markup by setting the element of an attribute with the pack URI.</span></span> <span data-ttu-id="07e7a-222">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="07e7a-222">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="07e7a-223">A tabela 1 ilustra os vários URIs de pacote absolutos que você pode especificar na marcação.</span><span class="sxs-lookup"><span data-stu-id="07e7a-223">Table 1 illustrates the various absolute pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="07e7a-224">Tabela 1: URIs de pacote absolutos em marcação</span><span class="sxs-lookup"><span data-stu-id="07e7a-224">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="07e7a-225">Arquivo</span><span class="sxs-lookup"><span data-stu-id="07e7a-225">File</span></span>|<span data-ttu-id="07e7a-226">URI de pacote absoluto</span><span class="sxs-lookup"><span data-stu-id="07e7a-226">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="07e7a-227">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="07e7a-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="07e7a-228">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="07e7a-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="07e7a-229">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="07e7a-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="07e7a-230">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="07e7a-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="07e7a-231">Arquivo de recurso em assembly referenciado com controle de versão</span><span class="sxs-lookup"><span data-stu-id="07e7a-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="07e7a-232">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="07e7a-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="07e7a-233">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="07e7a-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="07e7a-234">Arquivo de site de origem</span><span class="sxs-lookup"><span data-stu-id="07e7a-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="07e7a-235">Arquivo de site de origem em subpasta</span><span class="sxs-lookup"><span data-stu-id="07e7a-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="07e7a-236">A tabela 2 ilustra os vários URIs de pacote relativos que você pode especificar na marcação.</span><span class="sxs-lookup"><span data-stu-id="07e7a-236">Table 2 illustrates the various relative pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="07e7a-237">Tabela 2: URIs de pacote relativos em marcação</span><span class="sxs-lookup"><span data-stu-id="07e7a-237">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="07e7a-238">Arquivo</span><span class="sxs-lookup"><span data-stu-id="07e7a-238">File</span></span>|<span data-ttu-id="07e7a-239">URI de pacote relativo</span><span class="sxs-lookup"><span data-stu-id="07e7a-239">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="07e7a-240">Arquivo de recurso em assembly local</span><span class="sxs-lookup"><span data-stu-id="07e7a-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="07e7a-241">Arquivo de recurso em subpasta de assembly local</span><span class="sxs-lookup"><span data-stu-id="07e7a-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="07e7a-242">Arquivo de recurso em assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="07e7a-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="07e7a-243">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="07e7a-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="07e7a-244">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="07e7a-244">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="07e7a-245">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="07e7a-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="07e7a-246">Utilizando URIs de pacote em código</span><span class="sxs-lookup"><span data-stu-id="07e7a-246">Using Pack URIs in Code</span></span>

<span data-ttu-id="07e7a-247">Você especifica um URI de pacote no código instanciando a classe <xref:System.Uri> e passando o URI do pacote como um parâmetro para o construtor.</span><span class="sxs-lookup"><span data-stu-id="07e7a-247">You specify a pack URI in code by instantiating the <xref:System.Uri> class and passing the pack URI as a parameter to the constructor.</span></span> <span data-ttu-id="07e7a-248">Isso é demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="07e7a-248">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="07e7a-249">Por padrão, a classe <xref:System.Uri> considera que os URIs de pacote sejam absolutos.</span><span class="sxs-lookup"><span data-stu-id="07e7a-249">By default, the <xref:System.Uri> class considers pack URIs to be absolute.</span></span> <span data-ttu-id="07e7a-250">Consequentemente, uma exceção é gerada quando uma instância da classe <xref:System.Uri> é criada com um URI de pacote relativo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack URI.</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="07e7a-251">Felizmente, a sobrecarga de <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> do construtor da classe <xref:System.Uri> aceita um parâmetro do tipo <xref:System.UriKind> para permitir que você especifique se um pacote URI é absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack URI is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="07e7a-252">Você deve especificar somente <xref:System.UriKind.Absolute> ou <xref:System.UriKind.Relative> quando tiver certeza de que o pacote URI fornecido é um ou outro.</span><span class="sxs-lookup"><span data-stu-id="07e7a-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack URI is one or the other.</span></span> <span data-ttu-id="07e7a-253">Se você não souber o tipo de URI de pacote que é usado, como quando um usuário insere um pacote URI em tempo de execução, use <xref:System.UriKind.RelativeOrAbsolute> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="07e7a-253">If you don't know the type of pack URI that is used, such as when a user enters a pack URI at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="07e7a-254">A tabela 3 ilustra os vários URIs de pacote relativos que você pode especificar no código usando <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="07e7a-254">Table 3 illustrates the various relative pack URIs that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="07e7a-255">Tabela 3: URIs de pacote absolutos em código</span><span class="sxs-lookup"><span data-stu-id="07e7a-255">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="07e7a-256">Arquivo</span><span class="sxs-lookup"><span data-stu-id="07e7a-256">File</span></span>|<span data-ttu-id="07e7a-257">URI de pacote absoluto</span><span class="sxs-lookup"><span data-stu-id="07e7a-257">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="07e7a-258">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="07e7a-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="07e7a-259">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="07e7a-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="07e7a-260">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="07e7a-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="07e7a-261">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="07e7a-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="07e7a-262">Arquivo de recurso em assembly referenciado com controle de versão</span><span class="sxs-lookup"><span data-stu-id="07e7a-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="07e7a-263">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="07e7a-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="07e7a-264">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="07e7a-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="07e7a-265">Arquivo de site de origem</span><span class="sxs-lookup"><span data-stu-id="07e7a-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="07e7a-266">Arquivo de site de origem em subpasta</span><span class="sxs-lookup"><span data-stu-id="07e7a-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="07e7a-267">A tabela 4 ilustra os vários URIs de pacote relativos que você pode especificar no código usando <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="07e7a-267">Table 4 illustrates the various relative pack URIs that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="07e7a-268">Tabela 4: URIs de pacote relativos em código</span><span class="sxs-lookup"><span data-stu-id="07e7a-268">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="07e7a-269">Arquivo</span><span class="sxs-lookup"><span data-stu-id="07e7a-269">File</span></span>|<span data-ttu-id="07e7a-270">URI de pacote relativo</span><span class="sxs-lookup"><span data-stu-id="07e7a-270">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="07e7a-271">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="07e7a-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="07e7a-272">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="07e7a-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="07e7a-273">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="07e7a-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="07e7a-274">Arquivo de recurso em subpasta - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="07e7a-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="07e7a-275">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="07e7a-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="07e7a-276">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="07e7a-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="07e7a-277">Cenários comuns de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="07e7a-277">Common Pack URI Scenarios</span></span>

<span data-ttu-id="07e7a-278">As seções anteriores discutiram como construir URIs de pacote para identificar recursos, conteúdo e site de arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="07e7a-278">The preceding sections have discussed how to construct pack URIs to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="07e7a-279">Em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], essas construções são usadas de várias maneiras, e as seções a seguir abrangem vários usos comuns.</span><span class="sxs-lookup"><span data-stu-id="07e7a-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="07e7a-280">Especificando a interface do usuário para mostrar quando um aplicativo foi iniciado</span><span class="sxs-lookup"><span data-stu-id="07e7a-280">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="07e7a-281"><xref:System.Windows.Application.StartupUri%2A> especifica a primeira [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a ser mostrada quando um aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é iniciado.</span><span class="sxs-lookup"><span data-stu-id="07e7a-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="07e7a-282">Para aplicativos autônomos, o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pode ser uma janela, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="07e7a-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="07e7a-283">Os aplicativos e [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] autônomos também podem especificar uma página como a interface do usuário inicial, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="07e7a-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="07e7a-284">Se o aplicativo for um aplicativo autônomo e uma página for especificada com <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] abrirá um <xref:System.Windows.Navigation.NavigationWindow> para hospedar a página.</span><span class="sxs-lookup"><span data-stu-id="07e7a-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="07e7a-285">Por [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], a página é mostrada no navegador de host.</span><span class="sxs-lookup"><span data-stu-id="07e7a-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="07e7a-286">Navegando até uma página</span><span class="sxs-lookup"><span data-stu-id="07e7a-286">Navigating to a Page</span></span>

<span data-ttu-id="07e7a-287">O exemplo a seguir mostra como navegar até uma página.</span><span class="sxs-lookup"><span data-stu-id="07e7a-287">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="07e7a-288">Para obter mais informações sobre as várias maneiras de navegar no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consulte [visão geral de navegação](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="07e7a-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="07e7a-289">Especificando um ícone de janela</span><span class="sxs-lookup"><span data-stu-id="07e7a-289">Specifying a Window Icon</span></span>

<span data-ttu-id="07e7a-290">O exemplo a seguir mostra como usar um URI para especificar um ícone de janela.</span><span class="sxs-lookup"><span data-stu-id="07e7a-290">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="07e7a-291">Para obter mais informações, consulte <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="07e7a-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="07e7a-292">Carregando arquivos de imagem, áudio e vídeo</span><span class="sxs-lookup"><span data-stu-id="07e7a-292">Loading Image, Audio, and Video Files</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="07e7a-293">permite que os aplicativos usem uma ampla variedade de tipos de mídia, todos os quais podem ser identificados e carregados com URIs de pacote, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="07e7a-293">allows applications to use a wide variety of media types, all of which can be identified and loaded with pack URIs, as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="07e7a-294">Para obter mais informações sobre como trabalhar com conteúdo de mídia, consulte [gráficos e multimídia](../graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="07e7a-294">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="07e7a-295">Carregando um dicionário de recursos a partir do site de origem</span><span class="sxs-lookup"><span data-stu-id="07e7a-295">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="07e7a-296">Os dicionários de recursos (<xref:System.Windows.ResourceDictionary>) podem ser usados para dar suporte a temas de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="07e7a-297">Uma maneira de criar e gerenciar temas é criando diferentes temas como dicionários de recursos localizados em um site de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="07e7a-298">Isso permite que temas sejam adicionados e atualizados sem recompilar e reimplantar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07e7a-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="07e7a-299">Esses dicionários de recursos podem ser identificados e carregados usando URIs de pacote, que são mostrados no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="07e7a-299">These resource dictionaries can be identified and loaded using pack URIs, which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="07e7a-300">Para obter uma visão geral dos temas no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consulte [estilização e modelagem](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="07e7a-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../controls/styling-and-templating.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="07e7a-301">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07e7a-301">See also</span></span>

- [<span data-ttu-id="07e7a-302">Arquivos de recursos, de conteúdo e de dados de aplicativos do WPF</span><span class="sxs-lookup"><span data-stu-id="07e7a-302">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
