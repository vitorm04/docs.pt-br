---
title: URIs de pacote
description: Saiba mais sobre as várias maneiras de usar URIs (identificadores de recursos uniformes) para identificar e carregar arquivos no Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: 1d19dec0d846659f8de6ed518a7f98d224354a82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621685"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="f53e4-103">URIs "pack://" no WPF</span><span class="sxs-lookup"><span data-stu-id="f53e4-103">Pack URIs in WPF</span></span>

<span data-ttu-id="f53e4-104">No Windows Presentation Foundation (WPF), os URIs (identificadores de recursos uniformes) são usados para identificar e carregar arquivos de várias maneiras, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f53e4-104">In Windows Presentation Foundation (WPF), uniform resource identifiers (URIs) are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="f53e4-105">Especificando o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] a ser mostrado quando um aplicativo é iniciado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="f53e4-105">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="f53e4-106">Carregar imagens.</span><span class="sxs-lookup"><span data-stu-id="f53e4-106">Loading images.</span></span>

- <span data-ttu-id="f53e4-107">Navegar até as páginas.</span><span class="sxs-lookup"><span data-stu-id="f53e4-107">Navigating to pages.</span></span>

- <span data-ttu-id="f53e4-108">Carregar arquivos de dados não executáveis.</span><span class="sxs-lookup"><span data-stu-id="f53e4-108">Loading non-executable data files.</span></span>

<span data-ttu-id="f53e4-109">Além disso, os URIs podem ser usados para identificar e carregar arquivos de uma variedade de locais, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f53e4-109">Furthermore, URIs can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="f53e4-110">O assembly atual.</span><span class="sxs-lookup"><span data-stu-id="f53e4-110">The current assembly.</span></span>

- <span data-ttu-id="f53e4-111">Um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f53e4-111">A referenced assembly.</span></span>

- <span data-ttu-id="f53e4-112">Um local relativo a um assembly.</span><span class="sxs-lookup"><span data-stu-id="f53e4-112">A location relative to an assembly.</span></span>

- <span data-ttu-id="f53e4-113">O site de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-113">The application's site of origin.</span></span>

<span data-ttu-id="f53e4-114">Para fornecer um mecanismo consistente para identificar e carregar esses tipos de arquivos desses locais, o WPF aproveita a extensibilidade do esquema de *URI de pacote*.</span><span class="sxs-lookup"><span data-stu-id="f53e4-114">To provide a consistent mechanism for identifying and loading these types of files from these locations, WPF leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="f53e4-115">Este tópico fornece uma visão geral do esquema, aborda como construir URIs de pacote para uma variedade de cenários, discute URIs absolutos e relativos e resolução de URI, antes de mostrar como usar URIs de pacote de marcação e código.</span><span class="sxs-lookup"><span data-stu-id="f53e4-115">This topic provides an overview of the scheme, covers how to construct pack URIs for a variety of scenarios, discusses absolute and relative URIs and URI resolution, before showing how to use pack URIs from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="f53e4-116">O esquema de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="f53e4-116">The Pack URI Scheme</span></span>

<span data-ttu-id="f53e4-117">O esquema de URI de pacote é usado pela especificação OPC ( [Open Packaging Conventions](https://www.ecma-international.org/publications/standards/Ecma-376.htm) ), que descreve um modelo para organizar e identificar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-117">The pack URI scheme is used by the [Open Packaging Conventions](https://www.ecma-international.org/publications/standards/Ecma-376.htm) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="f53e4-118">Os principais elementos desse modelo são pacotes e partes, onde um *pacote* é um contêiner lógico para uma ou mais *partes*lógicas.</span><span class="sxs-lookup"><span data-stu-id="f53e4-118">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="f53e4-119">A imagem a seguir ilustra esse conceito.</span><span class="sxs-lookup"><span data-stu-id="f53e4-119">The following figure illustrates this concept.</span></span>

![Diagrama de partes e pacote](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="f53e4-121">Para identificar partes, a especificação OPC aproveita a extensibilidade do RFC 2396 (Uniform Resource Identifiers (URI): sintaxe genérica) para definir o esquema de URI de pacote.</span><span class="sxs-lookup"><span data-stu-id="f53e4-121">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack URI scheme.</span></span>

<span data-ttu-id="f53e4-122">O esquema especificado por um URI é definido por seu prefixo; http, FTP e arquivo são exemplos bem conhecidos.</span><span class="sxs-lookup"><span data-stu-id="f53e4-122">The scheme that is specified by a URI is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="f53e4-123">O esquema de URI de pacote usa "Pack" como seu esquema e contém dois componentes: autoridade e caminho.</span><span class="sxs-lookup"><span data-stu-id="f53e4-123">The pack URI scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="f53e4-124">A seguir está o formato de um pacote URI.</span><span class="sxs-lookup"><span data-stu-id="f53e4-124">The following is the format for a pack URI.</span></span>

<span data-ttu-id="f53e4-125">caminho de*autoridade* / *path* Pack://</span><span class="sxs-lookup"><span data-stu-id="f53e4-125">pack://*authority*/*path*</span></span>

<span data-ttu-id="f53e4-126">A *autoridade* especifica o tipo de pacote no qual uma parte está contida, enquanto o *caminho* especifica o local de uma parte dentro de um pacote.</span><span class="sxs-lookup"><span data-stu-id="f53e4-126">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="f53e4-127">Esse conceito é ilustrado pela figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="f53e4-127">This concept is illustrated by the following figure:</span></span>

![Relação entre pacote, autoridade e caminho](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="f53e4-129">Os pacotes e peças são análogos a aplicativos e arquivos, pois um aplicativo (pacote) pode incluir um ou mais arquivos (peças), incluindo:</span><span class="sxs-lookup"><span data-stu-id="f53e4-129">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="f53e4-130">Arquivos de recursos que são compilados no assembly local.</span><span class="sxs-lookup"><span data-stu-id="f53e4-130">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="f53e4-131">Arquivos de recursos que são compilados em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f53e4-131">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="f53e4-132">Arquivos de recursos que são compilados em um assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="f53e4-132">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="f53e4-133">Arquivos de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-133">Content files.</span></span>

- <span data-ttu-id="f53e4-134">Arquivos de site de origem.</span><span class="sxs-lookup"><span data-stu-id="f53e4-134">Site of origin files.</span></span>

<span data-ttu-id="f53e4-135">Para acessar esses tipos de arquivos, o WPF dá suporte a duas autoridades: application:///e siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="f53e4-135">To access these types of files, WPF supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="f53e4-136">A autoridade application:/// identifica arquivos de dados de aplicativo que são conhecidos no tempo de compilação, incluindo arquivos de recurso e conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-136">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="f53e4-137">A autoridade siteoforigin:/// identifica arquivos de site de origem.</span><span class="sxs-lookup"><span data-stu-id="f53e4-137">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="f53e4-138">O escopo de cada autoridade é mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="f53e4-138">The scope of each authority is shown in the following figure.</span></span>

![Diagrama de URI de pacote](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="f53e4-140">O componente de autoridade de um URI de pacote é um URI inserido que aponta para um pacote e deve estar em conformidade com o RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="f53e4-140">The authority component of a pack URI is an embedded URI that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="f53e4-141">Além disso, o caractere “/” deve ser substituído pelo caractere “,”; caracteres reservados como “%” e “?” devem ser ignorados.</span><span class="sxs-lookup"><span data-stu-id="f53e4-141">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="f53e4-142">Para ver os detalhes, consulte o OPC.</span><span class="sxs-lookup"><span data-stu-id="f53e4-142">See the OPC for details.</span></span>

<span data-ttu-id="f53e4-143">As seções a seguir explicam como construir URIs de pacote usando essas duas autoridades em conjunto com os caminhos apropriados para identificar recursos, conteúdo e site de arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="f53e4-143">The following sections explain how to construct pack URIs using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="f53e4-144">URIs de pacote de arquivo de recurso</span><span class="sxs-lookup"><span data-stu-id="f53e4-144">Resource File Pack URIs</span></span>

<span data-ttu-id="f53e4-145">Os arquivos de recurso são configurados como itens do MSBuild `Resource` e são compilados em assemblies.</span><span class="sxs-lookup"><span data-stu-id="f53e4-145">Resource files are configured as MSBuild `Resource` items and are compiled into assemblies.</span></span> <span data-ttu-id="f53e4-146">O WPF dá suporte à construção de URIs de pacote que podem ser usados para identificar arquivos de recursos que são compilados no assembly local ou compilados em um assembly que é referenciado do assembly local.</span><span class="sxs-lookup"><span data-stu-id="f53e4-146">WPF supports the construction of pack URIs that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="f53e4-147">Arquivo de recurso de assembly local</span><span class="sxs-lookup"><span data-stu-id="f53e4-147">Local Assembly Resource File</span></span>

<span data-ttu-id="f53e4-148">O pacote URI para um arquivo de recurso que é compilado no assembly local usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="f53e4-148">The pack URI for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="f53e4-149">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="f53e4-149">**Authority**: application:///.</span></span>

- <span data-ttu-id="f53e4-150">**Caminho**: o nome do arquivo de recurso, incluindo seu caminho, em relação à raiz da pasta de projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="f53e4-150">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="f53e4-151">O exemplo a seguir mostra o pacote URI para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado na raiz da pasta do projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="f53e4-151">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="f53e4-152">O exemplo a seguir mostra o pacote URI para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado em uma subpasta da pasta do projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="f53e4-152">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="f53e4-153">Arquivo de recurso de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f53e4-153">Referenced Assembly Resource File</span></span>

<span data-ttu-id="f53e4-154">O pacote URI para um arquivo de recurso que é compilado em um assembly referenciado usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="f53e4-154">The pack URI for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="f53e4-155">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="f53e4-155">**Authority**: application:///.</span></span>

- <span data-ttu-id="f53e4-156">**Caminho**: o nome de um arquivo de recurso compilado em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f53e4-156">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="f53e4-157">O caminho deve estar de acordo com o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="f53e4-157">The path must conform to the following format:</span></span>

  <span data-ttu-id="f53e4-158">*AssemblyShortName*{*; Versão*] {*; PublicKey*]; componente/*caminho*</span><span class="sxs-lookup"><span data-stu-id="f53e4-158">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="f53e4-159">**AssemblyShortName**: o nome curto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f53e4-159">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="f53e4-160">**;Version** [opcional]: a versão do assembly referenciado que contém o arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="f53e4-160">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="f53e4-161">É usada quando são carregados dois ou mais assemblies referenciados com o mesmo nome curto.</span><span class="sxs-lookup"><span data-stu-id="f53e4-161">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="f53e4-162">**;PublicKey** [opcional]: a chave pública que foi usada para assinar o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f53e4-162">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="f53e4-163">É usada quando são carregados dois ou mais assemblies referenciados com o mesmo nome curto.</span><span class="sxs-lookup"><span data-stu-id="f53e4-163">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="f53e4-164">**;component**: especifica que o assembly referenciado é referenciado a partir do assembly local.</span><span class="sxs-lookup"><span data-stu-id="f53e4-164">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="f53e4-165">**/Path**: o nome do arquivo de recurso, incluindo o caminho, em relação à raiz da pasta de projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f53e4-165">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="f53e4-166">O exemplo a seguir mostra o pacote URI para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado na raiz da pasta do projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f53e4-166">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="f53e4-167">O exemplo a seguir mostra o pacote URI para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado em uma subpasta da pasta do projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f53e4-167">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="f53e4-168">O exemplo a seguir mostra o pacote URI para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado na pasta raiz de uma pasta de projeto de assembly específica da versão referenciada.</span><span class="sxs-lookup"><span data-stu-id="f53e4-168">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="f53e4-169">Observe que a sintaxe do pack URI para arquivos de recurso de assembly referenciados pode ser usada somente com a autoridade application:///.</span><span class="sxs-lookup"><span data-stu-id="f53e4-169">Note that the pack URI syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="f53e4-170">Por exemplo, não há suporte para o seguinte no WPF.</span><span class="sxs-lookup"><span data-stu-id="f53e4-170">For example, the following is not supported in WPF.</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="f53e4-171">URIs de pacote de arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="f53e4-171">Content File Pack URIs</span></span>

<span data-ttu-id="f53e4-172">O pacote URI para um arquivo de conteúdo usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="f53e4-172">The pack URI for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="f53e4-173">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="f53e4-173">**Authority**: application:///.</span></span>

- <span data-ttu-id="f53e4-174">**Caminho**: o nome do arquivo de conteúdo, incluindo o caminho em relação ao local do sistema de arquivos do principal assembly executável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-174">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="f53e4-175">O exemplo a seguir mostra o pacote URI para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de conteúdo, localizado na mesma pasta que o assembly executável.</span><span class="sxs-lookup"><span data-stu-id="f53e4-175">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="f53e4-176">O exemplo a seguir mostra o pacote URI para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de conteúdo, localizado em uma subpasta que é relativa ao assembly executável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-176">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> <span data-ttu-id="f53e4-177">Não é possível navegar para arquivos de conteúdo HTML.</span><span class="sxs-lookup"><span data-stu-id="f53e4-177">HTML content files cannot be navigated to.</span></span> <span data-ttu-id="f53e4-178">O esquema de URI dá suporte apenas à navegação para arquivos HTML que estão localizados no site de origem.</span><span class="sxs-lookup"><span data-stu-id="f53e4-178">The URI scheme only supports navigation to HTML files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="f53e4-179">URIs de pacote de site de origem</span><span class="sxs-lookup"><span data-stu-id="f53e4-179">Site of Origin Pack URIs</span></span>

<span data-ttu-id="f53e4-180">O URI do pacote para um arquivo de site de origem usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="f53e4-180">The pack URI for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="f53e4-181">**Autoridade**: siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="f53e4-181">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="f53e4-182">**Caminho**: o nome do arquivo de site de origem, incluindo o caminho em relação ao local a partir do qual o assembly executável foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="f53e4-182">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="f53e4-183">O exemplo a seguir mostra o URI do pacote para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de site de origem, armazenado no local do qual o assembly executável é iniciado.</span><span class="sxs-lookup"><span data-stu-id="f53e4-183">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="f53e4-184">O exemplo a seguir mostra o URI do pacote para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de site de origem, armazenado na subpasta que é relativa ao local do qual o assembly executável do aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="f53e4-184">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="f53e4-185">Arquivos de paginação</span><span class="sxs-lookup"><span data-stu-id="f53e4-185">Page Files</span></span>

<span data-ttu-id="f53e4-186">Os arquivos XAML que são configurados como `Page` itens do MSBuild são compilados em assemblies da mesma maneira que os arquivos de recursos.</span><span class="sxs-lookup"><span data-stu-id="f53e4-186">XAML files that are configured as MSBuild `Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="f53e4-187">Consequentemente, `Page` os itens do MSBuild podem ser identificados usando URIs de pacote para arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="f53e4-187">Consequently, MSBuild `Page` items can be identified using pack URIs for resource files.</span></span>

<span data-ttu-id="f53e4-188">Os tipos de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos que normalmente são configurados como `Page` itens do MSBuild têm um dos seguintes como seu elemento raiz:</span><span class="sxs-lookup"><span data-stu-id="f53e4-188">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as MSBuild`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="f53e4-189">URIs de pacote absoluto versus relativo</span><span class="sxs-lookup"><span data-stu-id="f53e4-189">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="f53e4-190">Um URI de pacote totalmente qualificado inclui o esquema, a autoridade e o caminho, e é considerado um URI de pacote absoluto.</span><span class="sxs-lookup"><span data-stu-id="f53e4-190">A fully qualified pack URI includes the scheme, the authority, and the path, and it is considered an absolute pack URI.</span></span> <span data-ttu-id="f53e4-191">Como uma simplificação para os desenvolvedores, os [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementos normalmente permitem que você defina atributos apropriados com um URI de pacote relativo, que inclui apenas o caminho.</span><span class="sxs-lookup"><span data-stu-id="f53e4-191">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack URI, which includes only the path.</span></span>

<span data-ttu-id="f53e4-192">Por exemplo, considere o seguinte URI de pacote absoluto para um arquivo de recurso no assembly local.</span><span class="sxs-lookup"><span data-stu-id="f53e4-192">For example, consider the following absolute pack URI for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="f53e4-193">O URI de pacote relativo que se refere a esse arquivo de recurso seria o seguinte.</span><span class="sxs-lookup"><span data-stu-id="f53e4-193">The relative pack URI that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="f53e4-194">Como os arquivos de site de origem não estão associados a assemblies, eles só podem ser referidos com URIs de pacote absolutos.</span><span class="sxs-lookup"><span data-stu-id="f53e4-194">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack URIs.</span></span>

<span data-ttu-id="f53e4-195">Por padrão, um URI de pacote relativo é considerado relativo ao local da marcação ou código que contém a referência.</span><span class="sxs-lookup"><span data-stu-id="f53e4-195">By default, a relative pack URI is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="f53e4-196">No entanto, se uma barra invertida à esquerda for usada, a referência de URI de pacote relativa será considerada relativa à raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-196">If a leading backslash is used, however, the relative pack URI reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="f53e4-197">Considere, por exemplo, a estrutura de projeto a seguir.</span><span class="sxs-lookup"><span data-stu-id="f53e4-197">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="f53e4-198">Se página1. XAML contiver um URI que faz referência a \SubFolder\Page2.XAML *raiz*, a referência poderá usar o seguinte URI de pacote relativo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-198">If Page1.xaml contains a URI that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`Page2.xaml`

<span data-ttu-id="f53e4-199">Se página1. XAML contiver um URI que faz referência a \Page2.XAML *raiz*, a referência poderá usar o seguinte URI de pacote relativo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-199">If Page1.xaml contains a URI that references *Root*\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="f53e4-200">Resolução de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="f53e4-200">Pack URI Resolution</span></span>

<span data-ttu-id="f53e4-201">O formato dos URIs de pacote possibilita que URIs de pacote para diferentes tipos de arquivos tenham a mesma aparência.</span><span class="sxs-lookup"><span data-stu-id="f53e4-201">The format of pack URIs makes it possible for pack URIs for different types of files to look the same.</span></span> <span data-ttu-id="f53e4-202">Por exemplo, considere o seguinte URI absoluto do pacote.</span><span class="sxs-lookup"><span data-stu-id="f53e4-202">For example, consider the following absolute pack URI.</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="f53e4-203">Esse URI de pacote absoluto pode se referir a um arquivo de recurso no assembly local ou um arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-203">This absolute pack URI could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="f53e4-204">O mesmo é verdadeiro para o seguinte URI relativo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-204">The same is true for the following relative URI.</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="f53e4-205">Para determinar o tipo de arquivo ao qual um URI de pacote se refere, o WPF resolve URIs de arquivos de recursos em assemblies locais e arquivos de conteúdo usando a seguinte heurística:</span><span class="sxs-lookup"><span data-stu-id="f53e4-205">In order to determine the type of file that a pack URI refers to, WPF resolves URIs for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="f53e4-206">Investigue os metadados do assembly para um <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo que corresponda ao URI do pacote.</span><span class="sxs-lookup"><span data-stu-id="f53e4-206">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack URI.</span></span>

2. <span data-ttu-id="f53e4-207">Se o <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo for encontrado, o caminho do URI do pacote se referirá a um arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack URI refers to a content file.</span></span>

3. <span data-ttu-id="f53e4-208">Se o <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo não for encontrado, investigue os arquivos de recurso definidos que são compilados no assembly local.</span><span class="sxs-lookup"><span data-stu-id="f53e4-208">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="f53e4-209">Se um arquivo de recurso que corresponde ao caminho do URI do pacote for encontrado, o caminho do pacote URI se referirá a um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="f53e4-209">If a resource file that matches the path of the pack URI is found, the path of the pack URI refers to a resource file.</span></span>

5. <span data-ttu-id="f53e4-210">Se o recurso não for encontrado, o criado internamente <xref:System.Uri> será inválido.</span><span class="sxs-lookup"><span data-stu-id="f53e4-210">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

<span data-ttu-id="f53e4-211">A resolução de URI não se aplica a URIs que se referem ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="f53e4-211">URI resolution does not apply for URIs that refer to the following:</span></span>

- <span data-ttu-id="f53e4-212">Arquivos de conteúdo em assemblies referenciados: esses tipos de arquivo não são suportados pelo WPF.</span><span class="sxs-lookup"><span data-stu-id="f53e4-212">Content files in referenced assemblies: these file types are not supported by WPF.</span></span>

- <span data-ttu-id="f53e4-213">Arquivos inseridos em assemblies referenciados: URIs que os identificam são exclusivos porque incluem o nome do assembly referenciado e o `;component` sufixo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-213">Embedded files in referenced assemblies: URIs that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="f53e4-214">Arquivos de site de origem: os URIs que os identificam são exclusivos porque são os únicos arquivos que podem ser identificados por URIs de pacote que contêm a autoridade siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="f53e4-214">Site of origin files: URIs that identify them are unique because they are the only files that can be identified by pack URIs that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="f53e4-215">Uma simplificação que a resolução de URI de pacote permite é que o código seja, de certa forma, independente dos locais dos arquivos de conteúdo e de recursos.</span><span class="sxs-lookup"><span data-stu-id="f53e4-215">One simplification that pack URI resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="f53e4-216">Por exemplo, se você tiver um arquivo de recurso no assembly local que é reconfigurado para ser um arquivo de conteúdo, o pacote URI para o recurso permanecerá o mesmo, assim como o código que usa o pack URI.</span><span class="sxs-lookup"><span data-stu-id="f53e4-216">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack URI for the resource remains the same, as does the code that uses the pack URI.</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="f53e4-217">Programando com URIs de pacote</span><span class="sxs-lookup"><span data-stu-id="f53e4-217">Programming with Pack URIs</span></span>

<span data-ttu-id="f53e4-218">Muitas classes do WPF implementam propriedades que podem ser definidas com URIs de pacote, incluindo:</span><span class="sxs-lookup"><span data-stu-id="f53e4-218">Many WPF classes implement properties that can be set with pack URIs, including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="f53e4-219">Essas propriedades podem ser definidas a partir de marcação e código.</span><span class="sxs-lookup"><span data-stu-id="f53e4-219">These properties can be set from both markup and code.</span></span> <span data-ttu-id="f53e4-220">Esta seção demonstra as construções básicas para ambos e, depois, mostra exemplos de cenários comuns.</span><span class="sxs-lookup"><span data-stu-id="f53e4-220">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="f53e4-221">Utilizando URIs de pacote em marcação</span><span class="sxs-lookup"><span data-stu-id="f53e4-221">Using Pack URIs in Markup</span></span>

<span data-ttu-id="f53e4-222">Um URI de pacote é especificado na marcação definindo o elemento de um atributo com o URI pack.</span><span class="sxs-lookup"><span data-stu-id="f53e4-222">A pack URI is specified in markup by setting the element of an attribute with the pack URI.</span></span> <span data-ttu-id="f53e4-223">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f53e4-223">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="f53e4-224">A tabela 1 ilustra os vários URIs de pacote absolutos que você pode especificar na marcação.</span><span class="sxs-lookup"><span data-stu-id="f53e4-224">Table 1 illustrates the various absolute pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="f53e4-225">Tabela 1: URIs de pacote absolutos em marcação</span><span class="sxs-lookup"><span data-stu-id="f53e4-225">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="f53e4-226">Arquivo</span><span class="sxs-lookup"><span data-stu-id="f53e4-226">File</span></span>|<span data-ttu-id="f53e4-227">URI de pacote absoluto</span><span class="sxs-lookup"><span data-stu-id="f53e4-227">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="f53e4-228">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="f53e4-228">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="f53e4-229">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="f53e4-229">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="f53e4-230">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f53e4-230">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="f53e4-231">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f53e4-231">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="f53e4-232">Arquivo de recurso em assembly referenciado com controle de versão</span><span class="sxs-lookup"><span data-stu-id="f53e4-232">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="f53e4-233">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="f53e4-233">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="f53e4-234">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="f53e4-234">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="f53e4-235">Arquivo de site de origem</span><span class="sxs-lookup"><span data-stu-id="f53e4-235">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="f53e4-236">Arquivo de site de origem em subpasta</span><span class="sxs-lookup"><span data-stu-id="f53e4-236">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="f53e4-237">A tabela 2 ilustra os vários URIs de pacote relativos que você pode especificar na marcação.</span><span class="sxs-lookup"><span data-stu-id="f53e4-237">Table 2 illustrates the various relative pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="f53e4-238">Tabela 2: URIs de pacote relativos em marcação</span><span class="sxs-lookup"><span data-stu-id="f53e4-238">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="f53e4-239">Arquivo</span><span class="sxs-lookup"><span data-stu-id="f53e4-239">File</span></span>|<span data-ttu-id="f53e4-240">URI de pacote relativo</span><span class="sxs-lookup"><span data-stu-id="f53e4-240">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="f53e4-241">Arquivo de recurso em assembly local</span><span class="sxs-lookup"><span data-stu-id="f53e4-241">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="f53e4-242">Arquivo de recurso em subpasta de assembly local</span><span class="sxs-lookup"><span data-stu-id="f53e4-242">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="f53e4-243">Arquivo de recurso em assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f53e4-243">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="f53e4-244">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f53e4-244">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="f53e4-245">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="f53e4-245">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="f53e4-246">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="f53e4-246">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="f53e4-247">Utilizando URIs de pacote em código</span><span class="sxs-lookup"><span data-stu-id="f53e4-247">Using Pack URIs in Code</span></span>

<span data-ttu-id="f53e4-248">Você especifica um URI de pacote no código instanciando a <xref:System.Uri> classe e passando o URI do pacote como um parâmetro para o construtor.</span><span class="sxs-lookup"><span data-stu-id="f53e4-248">You specify a pack URI in code by instantiating the <xref:System.Uri> class and passing the pack URI as a parameter to the constructor.</span></span> <span data-ttu-id="f53e4-249">Isso é demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f53e4-249">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="f53e4-250">Por padrão, a <xref:System.Uri> classe considera os URIs do pacote como absoluto.</span><span class="sxs-lookup"><span data-stu-id="f53e4-250">By default, the <xref:System.Uri> class considers pack URIs to be absolute.</span></span> <span data-ttu-id="f53e4-251">Consequentemente, uma exceção é gerada quando uma instância da <xref:System.Uri> classe é criada com um URI de pacote relativo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-251">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack URI.</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="f53e4-252">Felizmente, a <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> sobrecarga do <xref:System.Uri> Construtor de classe aceita um parâmetro do tipo <xref:System.UriKind> para permitir que você especifique se um pacote URI é absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-252">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack URI is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="f53e4-253">Você deve especificar somente <xref:System.UriKind.Absolute> ou <xref:System.UriKind.Relative> quando tiver certeza de que o pacote URI fornecido é um ou outro.</span><span class="sxs-lookup"><span data-stu-id="f53e4-253">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack URI is one or the other.</span></span> <span data-ttu-id="f53e4-254">Se você não souber o tipo de URI de pacote que é usado, como quando um usuário insere um pacote URI em tempo de execução, use <xref:System.UriKind.RelativeOrAbsolute> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f53e4-254">If you don't know the type of pack URI that is used, such as when a user enters a pack URI at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="f53e4-255">A tabela 3 ilustra os vários URIs de pacote relativos que você pode especificar no código usando <xref:System.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f53e4-255">Table 3 illustrates the various relative pack URIs that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f53e4-256">Tabela 3: URIs de pacote absolutos em código</span><span class="sxs-lookup"><span data-stu-id="f53e4-256">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="f53e4-257">Arquivo</span><span class="sxs-lookup"><span data-stu-id="f53e4-257">File</span></span>|<span data-ttu-id="f53e4-258">URI de pacote absoluto</span><span class="sxs-lookup"><span data-stu-id="f53e4-258">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="f53e4-259">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="f53e4-259">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f53e4-260">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="f53e4-260">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f53e4-261">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f53e4-261">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f53e4-262">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f53e4-262">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f53e4-263">Arquivo de recurso em assembly referenciado com controle de versão</span><span class="sxs-lookup"><span data-stu-id="f53e4-263">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f53e4-264">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="f53e4-264">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f53e4-265">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="f53e4-265">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f53e4-266">Arquivo de site de origem</span><span class="sxs-lookup"><span data-stu-id="f53e4-266">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="f53e4-267">Arquivo de site de origem em subpasta</span><span class="sxs-lookup"><span data-stu-id="f53e4-267">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="f53e4-268">A tabela 4 ilustra os vários URIs de pacote relativos que você pode especificar no código usando <xref:System.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f53e4-268">Table 4 illustrates the various relative pack URIs that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f53e4-269">Tabela 4: URIs de pacote relativos em código</span><span class="sxs-lookup"><span data-stu-id="f53e4-269">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="f53e4-270">Arquivo</span><span class="sxs-lookup"><span data-stu-id="f53e4-270">File</span></span>|<span data-ttu-id="f53e4-271">URI de pacote relativo</span><span class="sxs-lookup"><span data-stu-id="f53e4-271">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="f53e4-272">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="f53e4-272">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="f53e4-273">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="f53e4-273">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="f53e4-274">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f53e4-274">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="f53e4-275">Arquivo de recurso em subpasta - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f53e4-275">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="f53e4-276">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="f53e4-276">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="f53e4-277">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="f53e4-277">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="f53e4-278">Cenários comuns de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="f53e4-278">Common Pack URI Scenarios</span></span>

<span data-ttu-id="f53e4-279">As seções anteriores discutiram como construir URIs de pacote para identificar recursos, conteúdo e site de arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="f53e4-279">The preceding sections have discussed how to construct pack URIs to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="f53e4-280">No WPF, essas construções são usadas de várias maneiras, e as seções a seguir abrangem vários usos comuns.</span><span class="sxs-lookup"><span data-stu-id="f53e4-280">In WPF, these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="f53e4-281">Especificando a interface do usuário para mostrar quando um aplicativo foi iniciado</span><span class="sxs-lookup"><span data-stu-id="f53e4-281">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="f53e4-282"><xref:System.Windows.Application.StartupUri%2A>Especifica o primeiro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a ser mostrado quando um aplicativo do WPF é iniciado.</span><span class="sxs-lookup"><span data-stu-id="f53e4-282"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a WPF application is launched.</span></span> <span data-ttu-id="f53e4-283">Para aplicativos autônomos, o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pode ser uma janela, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f53e4-283">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="f53e4-284">Aplicativos autônomos e aplicativos de navegador XAML (XBAPs) também podem especificar uma página como a interface do usuário inicial, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f53e4-284">Standalone applications and XAML browser applications (XBAPs) can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="f53e4-285">Se o aplicativo for um aplicativo autônomo e uma página for especificada com <xref:System.Windows.Application.StartupUri%2A> , o WPF abrirá um <xref:System.Windows.Navigation.NavigationWindow> para hospedar a página.</span><span class="sxs-lookup"><span data-stu-id="f53e4-285">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, WPF opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="f53e4-286">Para XBAPs, a página é mostrada no navegador de host.</span><span class="sxs-lookup"><span data-stu-id="f53e4-286">For XBAPs, the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="f53e4-287">Navegando até uma página</span><span class="sxs-lookup"><span data-stu-id="f53e4-287">Navigating to a Page</span></span>

<span data-ttu-id="f53e4-288">O exemplo a seguir mostra como navegar até uma página.</span><span class="sxs-lookup"><span data-stu-id="f53e4-288">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="f53e4-289">Para obter mais informações sobre as várias maneiras de navegar no WPF, consulte [visão geral de navegação](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f53e4-289">For more information on the various ways to navigate in WPF, see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="f53e4-290">Especificando um ícone de janela</span><span class="sxs-lookup"><span data-stu-id="f53e4-290">Specifying a Window Icon</span></span>

<span data-ttu-id="f53e4-291">O exemplo a seguir mostra como usar um URI para especificar um ícone de janela.</span><span class="sxs-lookup"><span data-stu-id="f53e4-291">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="f53e4-292">Para obter mais informações, consulte <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="f53e4-292">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="f53e4-293">Carregando arquivos de imagem, áudio e vídeo</span><span class="sxs-lookup"><span data-stu-id="f53e4-293">Loading Image, Audio, and Video Files</span></span>

<span data-ttu-id="f53e4-294">O WPF permite que os aplicativos usem uma ampla variedade de tipos de mídia, todos os quais podem ser identificados e carregados com URIs de pacote, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="f53e4-294">WPF allows applications to use a wide variety of media types, all of which can be identified and loaded with pack URIs, as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="f53e4-295">Para obter mais informações sobre como trabalhar com conteúdo de mídia, consulte [gráficos e multimídia](../graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="f53e4-295">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="f53e4-296">Carregando um dicionário de recursos a partir do site de origem</span><span class="sxs-lookup"><span data-stu-id="f53e4-296">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="f53e4-297">Os dicionários de recursos ( <xref:System.Windows.ResourceDictionary> ) podem ser usados para dar suporte a temas de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-297">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="f53e4-298">Uma maneira de criar e gerenciar temas é criando diferentes temas como dicionários de recursos localizados em um site de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-298">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="f53e4-299">Isso permite que temas sejam adicionados e atualizados sem recompilar e reimplantar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f53e4-299">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="f53e4-300">Esses dicionários de recursos podem ser identificados e carregados usando URIs de pacote, que são mostrados no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f53e4-300">These resource dictionaries can be identified and loaded using pack URIs, which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="f53e4-301">Para obter uma visão geral dos temas no WPF, consulte [estilização e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f53e4-301">For an overview of themes in WPF, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f53e4-302">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f53e4-302">See also</span></span>

- [<span data-ttu-id="f53e4-303">Arquivos de recurso, conteúdo e dados do aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="f53e4-303">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
