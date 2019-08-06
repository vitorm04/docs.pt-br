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
ms.openlocfilehash: f9ea4acfc7ba86d3424bb11af0de685651f99c61
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796746"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="2baa7-102">URIs "pack://" no WPF</span><span class="sxs-lookup"><span data-stu-id="2baa7-102">Pack URIs in WPF</span></span>

<span data-ttu-id="2baa7-103">No Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] o é usado para identificar e carregar arquivos de várias maneiras, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2baa7-103">In Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="2baa7-104">Especificando o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] a ser mostrado quando um aplicativo é iniciado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="2baa7-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="2baa7-105">Carregar imagens.</span><span class="sxs-lookup"><span data-stu-id="2baa7-105">Loading images.</span></span>

- <span data-ttu-id="2baa7-106">Navegar até as páginas.</span><span class="sxs-lookup"><span data-stu-id="2baa7-106">Navigating to pages.</span></span>

- <span data-ttu-id="2baa7-107">Carregar arquivos de dados não executáveis.</span><span class="sxs-lookup"><span data-stu-id="2baa7-107">Loading non-executable data files.</span></span>

<span data-ttu-id="2baa7-108">Além disso [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , o pode ser usado para identificar e carregar arquivos de uma variedade de locais, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2baa7-108">Furthermore, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="2baa7-109">O assembly atual.</span><span class="sxs-lookup"><span data-stu-id="2baa7-109">The current assembly.</span></span>

- <span data-ttu-id="2baa7-110">Um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2baa7-110">A referenced assembly.</span></span>

- <span data-ttu-id="2baa7-111">Um local relativo a um assembly.</span><span class="sxs-lookup"><span data-stu-id="2baa7-111">A location relative to an assembly.</span></span>

- <span data-ttu-id="2baa7-112">O site de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-112">The application's site of origin.</span></span>

<span data-ttu-id="2baa7-113">Para fornecer um mecanismo consistente para identificar e carregar esses tipos de arquivos desses locais, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] o aproveita a extensibilidade do esquema de *URI de pacote*.</span><span class="sxs-lookup"><span data-stu-id="2baa7-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="2baa7-114">Este tópico fornece uma visão geral do esquema, aborda como construir o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para uma variedade de cenários, discute absoluto e relativo [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] e [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolução, antes de mostrar como usar o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] de ambas as marcações e o código.</span><span class="sxs-lookup"><span data-stu-id="2baa7-114">This topic provides an overview of the scheme, covers how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for a variety of scenarios, discusses absolute and relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] and [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution, before showing how to use pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="2baa7-115">O esquema de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="2baa7-115">The Pack URI Scheme</span></span>

<span data-ttu-id="2baa7-116">O esquema [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de pacote é usado pela especificação OPC ( [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) ), que descreve um modelo para organizar e identificar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-116">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme is used by the [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="2baa7-117">Os principais elementos desse modelo são pacotes e partes, onde um *pacote* é um contêiner lógico para uma ou mais *partes*lógicas.</span><span class="sxs-lookup"><span data-stu-id="2baa7-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="2baa7-118">A imagem a seguir ilustra esse conceito.</span><span class="sxs-lookup"><span data-stu-id="2baa7-118">The following figure illustrates this concept.</span></span>

![Diagrama de partes e pacote](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="2baa7-120">Para identificar partes, a especificação OPC aproveita a extensibilidade do RFC 2396 (Uniform Resource Identifiers (URI): Sintaxe genérica) para definir o esquema [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de pacote.</span><span class="sxs-lookup"><span data-stu-id="2baa7-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme.</span></span>

<span data-ttu-id="2baa7-121">O esquema especificado por um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é definido por seu prefixo; http, FTP e arquivo são exemplos bem conhecidos.</span><span class="sxs-lookup"><span data-stu-id="2baa7-121">The scheme that is specified by a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="2baa7-122">O esquema [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de pacote usa "Pack" como seu esquema e contém dois componentes: autoridade e caminho.</span><span class="sxs-lookup"><span data-stu-id="2baa7-122">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="2baa7-123">A seguir está o formato de um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2baa7-123">The following is the format for a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

<span data-ttu-id="2baa7-124">pack://*authority*/*path*</span><span class="sxs-lookup"><span data-stu-id="2baa7-124">pack://*authority*/*path*</span></span>

<span data-ttu-id="2baa7-125">A *autoridade* especifica o tipo de pacote no qual uma parte está contida, enquanto o *caminho* especifica o local de uma parte dentro de um pacote.</span><span class="sxs-lookup"><span data-stu-id="2baa7-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="2baa7-126">Esse conceito é ilustrado pela figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="2baa7-126">This concept is illustrated by the following figure:</span></span>

![Relação entre pacote, autoridade e caminho](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="2baa7-128">Os pacotes e peças são análogos a aplicativos e arquivos, pois um aplicativo (pacote) pode incluir um ou mais arquivos (peças), incluindo:</span><span class="sxs-lookup"><span data-stu-id="2baa7-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="2baa7-129">Arquivos de recursos que são compilados no assembly local.</span><span class="sxs-lookup"><span data-stu-id="2baa7-129">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="2baa7-130">Arquivos de recursos que são compilados em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2baa7-130">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="2baa7-131">Arquivos de recursos que são compilados em um assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="2baa7-131">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="2baa7-132">Arquivos de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-132">Content files.</span></span>

- <span data-ttu-id="2baa7-133">Arquivos de site de origem.</span><span class="sxs-lookup"><span data-stu-id="2baa7-133">Site of origin files.</span></span>

<span data-ttu-id="2baa7-134">Para acessar esses tipos de arquivos, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] o dá suporte a duas autoridades: Application:///e siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="2baa7-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="2baa7-135">A autoridade application:/// identifica arquivos de dados de aplicativo que são conhecidos no tempo de compilação, incluindo arquivos de recurso e conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="2baa7-136">A autoridade siteoforigin:/// identifica arquivos de site de origem.</span><span class="sxs-lookup"><span data-stu-id="2baa7-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="2baa7-137">O escopo de cada autoridade é mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2baa7-137">The scope of each authority is shown in the following figure.</span></span>

![Diagrama de URI de pacote](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="2baa7-139">O componente de autoridade de um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pacote é um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] inserido que aponta para um pacote e deve estar em conformidade com o RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="2baa7-139">The authority component of a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is an embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="2baa7-140">Além disso, o caractere “/” deve ser substituído pelo caractere “,”; caracteres reservados como “%” e “?” devem ser ignorados.</span><span class="sxs-lookup"><span data-stu-id="2baa7-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="2baa7-141">Para ver os detalhes, consulte o OPC.</span><span class="sxs-lookup"><span data-stu-id="2baa7-141">See the OPC for details.</span></span>

<span data-ttu-id="2baa7-142">As seções a seguir explicam como construir [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] o pacote usando essas duas autoridades em conjunto com os caminhos apropriados para identificar recursos, conteúdo e site de arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="2baa7-142">The following sections explain how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="2baa7-143">URIs de pacote de arquivo de recurso</span><span class="sxs-lookup"><span data-stu-id="2baa7-143">Resource File Pack URIs</span></span>

<span data-ttu-id="2baa7-144">Os arquivos de recurso são [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] configurados como `Resource` itens e são compilados em assemblies.</span><span class="sxs-lookup"><span data-stu-id="2baa7-144">Resource files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource` items and are compiled into assemblies.</span></span> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="2baa7-145">dá suporte à construção do [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pacote que pode ser usada para identificar arquivos de recursos que são compilados no assembly local ou compilados em um assembly que é referenciado do assembly local.</span><span class="sxs-lookup"><span data-stu-id="2baa7-145">supports the construction of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="2baa7-146">Arquivo de recurso de assembly local</span><span class="sxs-lookup"><span data-stu-id="2baa7-146">Local Assembly Resource File</span></span>

<span data-ttu-id="2baa7-147">O pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um arquivo de recurso que é compilado no assembly local usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="2baa7-147">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="2baa7-148">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="2baa7-148">**Authority**: application:///.</span></span>

- <span data-ttu-id="2baa7-149">**Caminho**: O nome do arquivo de recurso, incluindo seu caminho, relativo à raiz da pasta do projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="2baa7-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="2baa7-150">O exemplo a seguir mostra o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pacote para [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo de recurso que está localizado na raiz da pasta do projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="2baa7-150">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="2baa7-151">O exemplo a seguir mostra o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pacote para [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo de recurso que está localizado em uma subpasta da pasta do projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="2baa7-151">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="2baa7-152">Arquivo de recurso de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2baa7-152">Referenced Assembly Resource File</span></span>

<span data-ttu-id="2baa7-153">O pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um arquivo de recurso que é compilado em um assembly referenciado usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="2baa7-153">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="2baa7-154">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="2baa7-154">**Authority**: application:///.</span></span>

- <span data-ttu-id="2baa7-155">**Caminho**: O nome de um arquivo de recurso que é compilado em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2baa7-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="2baa7-156">O caminho deve estar de acordo com o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="2baa7-156">The path must conform to the following format:</span></span>

  <span data-ttu-id="2baa7-157">*AssemblyShortName*{ *;Version*]{ *;PublicKey*];component/*Path*</span><span class="sxs-lookup"><span data-stu-id="2baa7-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="2baa7-158">**AssemblyShortName**: o nome curto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2baa7-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="2baa7-159">**;Version** [opcional]: a versão do assembly referenciado que contém o arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="2baa7-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="2baa7-160">É usada quando são carregados dois ou mais assemblies referenciados com o mesmo nome curto.</span><span class="sxs-lookup"><span data-stu-id="2baa7-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="2baa7-161">**;PublicKey** [opcional]: a chave pública que foi usada para assinar o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2baa7-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="2baa7-162">É usada quando são carregados dois ou mais assemblies referenciados com o mesmo nome curto.</span><span class="sxs-lookup"><span data-stu-id="2baa7-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="2baa7-163">**;component**: especifica que o assembly referenciado é referenciado a partir do assembly local.</span><span class="sxs-lookup"><span data-stu-id="2baa7-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="2baa7-164">**/Path**: o nome do arquivo de recurso, incluindo o caminho, em relação à raiz da pasta de projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2baa7-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="2baa7-165">O exemplo a seguir mostra o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pacote para [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo de recurso que está localizado na raiz da pasta do projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2baa7-165">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="2baa7-166">O exemplo a seguir mostra o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pacote para [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo de recurso que está localizado em uma subpasta da pasta do projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2baa7-166">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="2baa7-167">O exemplo a seguir mostra o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pacote para [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo de recurso que está localizado na pasta raiz de uma pasta de projeto de assembly específica de versão referenciada.</span><span class="sxs-lookup"><span data-stu-id="2baa7-167">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="2baa7-168">Observe que a sintaxe [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] do pacote para arquivos de recurso de assembly referenciados pode ser usada somente com a autoridade Application:///.</span><span class="sxs-lookup"><span data-stu-id="2baa7-168">Note that the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="2baa7-169">Por exemplo, não há suporte para o seguinte [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]no.</span><span class="sxs-lookup"><span data-stu-id="2baa7-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="2baa7-170">URIs de pacote de arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="2baa7-170">Content File Pack URIs</span></span>

<span data-ttu-id="2baa7-171">O pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um arquivo de conteúdo usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="2baa7-171">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="2baa7-172">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="2baa7-172">**Authority**: application:///.</span></span>

- <span data-ttu-id="2baa7-173">**Caminho**: O nome do arquivo de conteúdo, incluindo seu caminho relativo ao local do sistema de arquivos do assembly executável principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="2baa7-174">O exemplo a seguir mostra o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pacote para [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo de conteúdo, localizado na mesma pasta que o assembly executável.</span><span class="sxs-lookup"><span data-stu-id="2baa7-174">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="2baa7-175">O exemplo a seguir mostra o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pacote para [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo de conteúdo, localizado em uma subpasta que é relativa ao assembly executável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-175">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> <span data-ttu-id="2baa7-176">Não é possível navegar para arquivos de conteúdo HTML.</span><span class="sxs-lookup"><span data-stu-id="2baa7-176">HTML content files cannot be navigated to.</span></span> <span data-ttu-id="2baa7-177">O [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquema dá suporte apenas à navegação para arquivos HTML que estão localizados no site de origem.</span><span class="sxs-lookup"><span data-stu-id="2baa7-177">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme only supports navigation to HTML files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="2baa7-178">URIs de pacote de site de origem</span><span class="sxs-lookup"><span data-stu-id="2baa7-178">Site of Origin Pack URIs</span></span>

<span data-ttu-id="2baa7-179">O pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um arquivo de site de origem usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="2baa7-179">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="2baa7-180">**Autoridade**: siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="2baa7-180">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="2baa7-181">**Caminho**: O nome do arquivo de site de origem, incluindo seu caminho relativo ao local do qual o assembly executável foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="2baa7-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="2baa7-182">O exemplo a seguir mostra o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pacote para [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo de site de origem, armazenado no local do qual o assembly executável é iniciado.</span><span class="sxs-lookup"><span data-stu-id="2baa7-182">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="2baa7-183">O exemplo a seguir mostra o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pacote para [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo de site de origem, armazenado na subpasta que é relativa ao local do qual o assembly executável do aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="2baa7-183">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="2baa7-184">Arquivos de paginação</span><span class="sxs-lookup"><span data-stu-id="2baa7-184">Page Files</span></span>

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="2baa7-185">os arquivos configurados [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] como `Page` itens são compilados em assemblies da mesma maneira que os arquivos de recursos.</span><span class="sxs-lookup"><span data-stu-id="2baa7-185">files that are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="2baa7-186">Consequentemente [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] , `Page` os itens podem ser identificados [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] usando o pacote para arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="2baa7-186">Consequently, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items can be identified using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files.</span></span>

<span data-ttu-id="2baa7-187">Os tipos de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos que normalmente são configurados como [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` itens têm um dos seguintes como seu elemento raiz:</span><span class="sxs-lookup"><span data-stu-id="2baa7-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="2baa7-188">Absoluto versus URIs de pacote relativas</span><span class="sxs-lookup"><span data-stu-id="2baa7-188">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="2baa7-189">Um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] totalmente qualificado inclui o esquema, a autoridade e o caminho, e é considerado um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]absoluto.</span><span class="sxs-lookup"><span data-stu-id="2baa7-189">A fully qualified pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] includes the scheme, the authority, and the path, and it is considered an absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="2baa7-190">Como uma simplificação para os [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] desenvolvedores, os elementos normalmente permitem que você defina atributos apropriados com [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]um pacote relativo, que inclui apenas o caminho.</span><span class="sxs-lookup"><span data-stu-id="2baa7-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], which includes only the path.</span></span>

<span data-ttu-id="2baa7-191">Por exemplo, considere o seguinte pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] absoluto para um arquivo de recurso no assembly local.</span><span class="sxs-lookup"><span data-stu-id="2baa7-191">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="2baa7-192">O pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] relativo que se refere a esse arquivo de recurso seria o seguinte.</span><span class="sxs-lookup"><span data-stu-id="2baa7-192">The relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="2baa7-193">Como os arquivos de site de origem não estão associados a assemblies, eles só podem ser referenciados com [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]o pacote absoluto.</span><span class="sxs-lookup"><span data-stu-id="2baa7-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span></span>

<span data-ttu-id="2baa7-194">Por padrão, um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] relativo é considerado relativo ao local da marcação ou código que contém a referência.</span><span class="sxs-lookup"><span data-stu-id="2baa7-194">By default, a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="2baa7-195">No entanto, se uma barra invertida à esquerda for usada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , a referência de pacote relativa será considerada relativa à raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-195">If a leading backslash is used, however, the relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="2baa7-196">Considere, por exemplo, a estrutura de projeto a seguir.</span><span class="sxs-lookup"><span data-stu-id="2baa7-196">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="2baa7-197">Se página1. XAML contiver [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] um que faça referência a \SubFolder\Page2.XAML *raiz*, a referência poderá usar o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]seguinte pacote relativo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-197">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`Page2.xaml`

<span data-ttu-id="2baa7-198">Se página1. XAML contiver [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] um que faça referência a \Page2.XAML *raiz*, a referência poderá usar o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]seguinte pacote relativo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-198">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="2baa7-199">Resolução de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="2baa7-199">Pack URI Resolution</span></span>

<span data-ttu-id="2baa7-200">O formato do pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] torna possível que o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para diferentes tipos de arquivos tenha a mesma aparência.</span><span class="sxs-lookup"><span data-stu-id="2baa7-200">The format of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] makes it possible for pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for different types of files to look the same.</span></span> <span data-ttu-id="2baa7-201">Por exemplo, considere o seguinte pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]absoluto.</span><span class="sxs-lookup"><span data-stu-id="2baa7-201">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="2baa7-202">Esse pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] absoluto pode se referir a um arquivo de recurso no assembly local ou um arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-202">This absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="2baa7-203">O mesmo é verdadeiro para o seguinte relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2baa7-203">The same is true for the following relative [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="2baa7-204">Para determinar o tipo de arquivo ao qual um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] se refere, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] o resolve [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] os arquivos de recurso em assemblies locais e arquivos de conteúdo usando a seguinte heurística:</span><span class="sxs-lookup"><span data-stu-id="2baa7-204">In order to determine the type of file that a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="2baa7-205">Investigue os metadados do assembly para <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> um atributo que corresponda ao [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]pacote.</span><span class="sxs-lookup"><span data-stu-id="2baa7-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

2. <span data-ttu-id="2baa7-206">Se o <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo for encontrado, o caminho do pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] fará referência a um arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a content file.</span></span>

3. <span data-ttu-id="2baa7-207">Se o <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo não for encontrado, investigue os arquivos de recurso definidos que são compilados no assembly local.</span><span class="sxs-lookup"><span data-stu-id="2baa7-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="2baa7-208">Se um arquivo de recurso que corresponde ao caminho do pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for encontrado, o caminho do pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] se referirá a um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="2baa7-208">If a resource file that matches the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a resource file.</span></span>

5. <span data-ttu-id="2baa7-209">Se o recurso não for encontrado, o criado <xref:System.Uri> internamente será inválido.</span><span class="sxs-lookup"><span data-stu-id="2baa7-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]<span data-ttu-id="2baa7-210">a resolução não se aplica [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] ao que se refere ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="2baa7-210">resolution does not apply for [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that refer to the following:</span></span>

- <span data-ttu-id="2baa7-211">Arquivos de conteúdo em assemblies referenciados: esses tipos de arquivo não [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]são suportados pelo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

- <span data-ttu-id="2baa7-212">Arquivos inseridos em assemblies referenciados: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que os identificam são exclusivos porque incluem o nome do assembly referenciado e o `;component` sufixo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-212">Embedded files in referenced assemblies: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="2baa7-213">Arquivos de site de origem [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] : que os identificam são exclusivos porque são os únicos arquivos que podem ser identificados pelo [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pacote que contêm a autoridade siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="2baa7-213">Site of origin files: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they are the only files that can be identified by pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="2baa7-214">Uma simplificação que [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] a resolução de pacote permite é que o código seja, de certa forma, independente dos locais dos arquivos de conteúdo e de recursos.</span><span class="sxs-lookup"><span data-stu-id="2baa7-214">One simplification that pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="2baa7-215">Por exemplo, se você tiver um arquivo de recurso no assembly local que é reconfigurado para ser um arquivo de conteúdo, o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para o recurso permanecerá o mesmo, assim como o código que usa o [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]pacote.</span><span class="sxs-lookup"><span data-stu-id="2baa7-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the resource remains the same, as does the code that uses the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="2baa7-216">Programando com URIs de pacote</span><span class="sxs-lookup"><span data-stu-id="2baa7-216">Programming with Pack URIs</span></span>

<span data-ttu-id="2baa7-217">Muitas [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implementam propriedades que podem ser definidas com [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]o pacote, incluindo:</span><span class="sxs-lookup"><span data-stu-id="2baa7-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="2baa7-218">Essas propriedades podem ser definidas a partir de marcação e código.</span><span class="sxs-lookup"><span data-stu-id="2baa7-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="2baa7-219">Esta seção demonstra as construções básicas para ambos e, depois, mostra exemplos de cenários comuns.</span><span class="sxs-lookup"><span data-stu-id="2baa7-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="2baa7-220">Utilizando URIs de pacote em marcação</span><span class="sxs-lookup"><span data-stu-id="2baa7-220">Using Pack URIs in Markup</span></span>

<span data-ttu-id="2baa7-221">Um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é especificado na marcação definindo o elemento de um atributo com o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2baa7-221">A pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is specified in markup by setting the element of an attribute with the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="2baa7-222">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2baa7-222">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="2baa7-223">A tabela 1 ilustra o vários pacotes [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] absolutos que você pode especificar na marcação.</span><span class="sxs-lookup"><span data-stu-id="2baa7-223">Table 1 illustrates the various absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>

<span data-ttu-id="2baa7-224">Tabela 1: URIs de pacote absolutos na marcação</span><span class="sxs-lookup"><span data-stu-id="2baa7-224">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="2baa7-225">Arquivo</span><span class="sxs-lookup"><span data-stu-id="2baa7-225">File</span></span>|<span data-ttu-id="2baa7-226">Pacote absoluto[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2baa7-226">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="2baa7-227">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="2baa7-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="2baa7-228">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="2baa7-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="2baa7-229">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2baa7-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="2baa7-230">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2baa7-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="2baa7-231">Arquivo de recurso em assembly referenciado com controle de versão</span><span class="sxs-lookup"><span data-stu-id="2baa7-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="2baa7-232">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="2baa7-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="2baa7-233">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="2baa7-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="2baa7-234">Arquivo de site de origem</span><span class="sxs-lookup"><span data-stu-id="2baa7-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="2baa7-235">Arquivo de site de origem em subpasta</span><span class="sxs-lookup"><span data-stu-id="2baa7-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="2baa7-236">A tabela 2 ilustra os vários pacotes [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] relativos que você pode especificar na marcação.</span><span class="sxs-lookup"><span data-stu-id="2baa7-236">Table 2 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>

<span data-ttu-id="2baa7-237">Tabela 2: URIs de pacote relativas na marcação</span><span class="sxs-lookup"><span data-stu-id="2baa7-237">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="2baa7-238">Arquivo</span><span class="sxs-lookup"><span data-stu-id="2baa7-238">File</span></span>|<span data-ttu-id="2baa7-239">Pacote relativo[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2baa7-239">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="2baa7-240">Arquivo de recurso em assembly local</span><span class="sxs-lookup"><span data-stu-id="2baa7-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="2baa7-241">Arquivo de recurso em subpasta de assembly local</span><span class="sxs-lookup"><span data-stu-id="2baa7-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="2baa7-242">Arquivo de recurso em assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2baa7-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="2baa7-243">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2baa7-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="2baa7-244">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="2baa7-244">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="2baa7-245">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="2baa7-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="2baa7-246">Utilizando URIs de pacote em código</span><span class="sxs-lookup"><span data-stu-id="2baa7-246">Using Pack URIs in Code</span></span>

<span data-ttu-id="2baa7-247">Você especifica um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] no código instanciando a <xref:System.Uri> classe e passando o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] como um parâmetro para o construtor.</span><span class="sxs-lookup"><span data-stu-id="2baa7-247">You specify a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] in code by instantiating the <xref:System.Uri> class and passing the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] as a parameter to the constructor.</span></span> <span data-ttu-id="2baa7-248">Isso é demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2baa7-248">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="2baa7-249">Por padrão, a <xref:System.Uri> classe considera o [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pacote como absoluto.</span><span class="sxs-lookup"><span data-stu-id="2baa7-249">By default, the <xref:System.Uri> class considers pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to be absolute.</span></span> <span data-ttu-id="2baa7-250">Consequentemente, uma exceção é gerada quando uma instância da <xref:System.Uri> classe é criada com um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]relativo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="2baa7-251">Felizmente, a <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> sobrecarga <xref:System.Uri> do construtor da classe aceita um parâmetro do tipo <xref:System.UriKind> para permitir que você especifique se um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="2baa7-252">Você deve especificar somente <xref:System.UriKind.Absolute> ou <xref:System.UriKind.Relative> quando tiver certeza de que o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] fornecido é um ou outro.</span><span class="sxs-lookup"><span data-stu-id="2baa7-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is one or the other.</span></span> <span data-ttu-id="2baa7-253">Se você não souber o tipo de pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] usado, como quando um usuário insere um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] em tempo de execução, use <xref:System.UriKind.RelativeOrAbsolute> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="2baa7-253">If you don't know the type of pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that is used, such as when a user enters a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="2baa7-254">A tabela 3 ilustra os vários pacotes [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] relativos que você pode especificar no código usando <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2baa7-254">Table 3 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="2baa7-255">Tabela 3: URIs de pacote absoluto no código</span><span class="sxs-lookup"><span data-stu-id="2baa7-255">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="2baa7-256">Arquivo</span><span class="sxs-lookup"><span data-stu-id="2baa7-256">File</span></span>|<span data-ttu-id="2baa7-257">Pacote absoluto[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2baa7-257">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="2baa7-258">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="2baa7-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="2baa7-259">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="2baa7-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="2baa7-260">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2baa7-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="2baa7-261">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2baa7-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="2baa7-262">Arquivo de recurso em assembly referenciado com controle de versão</span><span class="sxs-lookup"><span data-stu-id="2baa7-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="2baa7-263">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="2baa7-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="2baa7-264">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="2baa7-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="2baa7-265">Arquivo de site de origem</span><span class="sxs-lookup"><span data-stu-id="2baa7-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="2baa7-266">Arquivo de site de origem em subpasta</span><span class="sxs-lookup"><span data-stu-id="2baa7-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="2baa7-267">A tabela 4 ilustra os vários pacotes [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] relativos que você pode especificar no código <xref:System.Uri?displayProperty=nameWithType>usando.</span><span class="sxs-lookup"><span data-stu-id="2baa7-267">Table 4 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="2baa7-268">Tabela 4: URIs de pacote relativas no código</span><span class="sxs-lookup"><span data-stu-id="2baa7-268">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="2baa7-269">Arquivo</span><span class="sxs-lookup"><span data-stu-id="2baa7-269">File</span></span>|<span data-ttu-id="2baa7-270">Pacote relativo[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2baa7-270">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="2baa7-271">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="2baa7-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="2baa7-272">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="2baa7-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="2baa7-273">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2baa7-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="2baa7-274">Arquivo de recurso em subpasta - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2baa7-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="2baa7-275">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="2baa7-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="2baa7-276">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="2baa7-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="2baa7-277">Cenários comuns de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="2baa7-277">Common Pack URI Scenarios</span></span>

<span data-ttu-id="2baa7-278">As seções anteriores discutiram como construir o Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para identificar recursos, conteúdo e site de arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="2baa7-278">The preceding sections have discussed how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="2baa7-279">No [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], essas construções são usadas de várias maneiras, e as seções a seguir abrangem vários usos comuns.</span><span class="sxs-lookup"><span data-stu-id="2baa7-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="2baa7-280">Especificando a interface do usuário para mostrar quando um aplicativo foi iniciado</span><span class="sxs-lookup"><span data-stu-id="2baa7-280">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="2baa7-281"><xref:System.Windows.Application.StartupUri%2A>Especifica o primeiro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a ser mostrado quando [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] um aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="2baa7-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="2baa7-282">Para aplicativos autônomos, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] o pode ser uma janela, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2baa7-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="2baa7-283">Aplicativos autônomos [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] e também podem especificar uma página como a interface do usuário inicial, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2baa7-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="2baa7-284">Se o aplicativo for um aplicativo autônomo e uma página for especificada com <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] o abrirá um <xref:System.Windows.Navigation.NavigationWindow> para hospedar a página.</span><span class="sxs-lookup"><span data-stu-id="2baa7-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="2baa7-285">Para [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]o, a página é mostrada no navegador de host.</span><span class="sxs-lookup"><span data-stu-id="2baa7-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="2baa7-286">Navegando até uma página</span><span class="sxs-lookup"><span data-stu-id="2baa7-286">Navigating to a Page</span></span>

<span data-ttu-id="2baa7-287">O exemplo a seguir mostra como navegar até uma página.</span><span class="sxs-lookup"><span data-stu-id="2baa7-287">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="2baa7-288">Para obter mais informações sobre as várias maneiras de navegar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]no, consulte [visão geral de navegação](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2baa7-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="2baa7-289">Especificando um ícone de janela</span><span class="sxs-lookup"><span data-stu-id="2baa7-289">Specifying a Window Icon</span></span>

<span data-ttu-id="2baa7-290">O exemplo a seguir mostra como usar um URI para especificar um ícone de janela.</span><span class="sxs-lookup"><span data-stu-id="2baa7-290">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="2baa7-291">Para obter mais informações, consulte <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="2baa7-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="2baa7-292">Carregando arquivos de imagem, áudio e vídeo</span><span class="sxs-lookup"><span data-stu-id="2baa7-292">Loading Image, Audio, and Video Files</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="2baa7-293">permite que os aplicativos usem uma ampla variedade de tipos de mídia, todos os quais podem ser identificados e carregados [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]com o pacote, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="2baa7-293">allows applications to use a wide variety of media types, all of which can be identified and loaded with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="2baa7-294">Para obter mais informações sobre como trabalhar com conteúdo de mídia, consulte [gráficos e multimídia](../graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="2baa7-294">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="2baa7-295">Carregando um dicionário de recursos a partir do site de origem</span><span class="sxs-lookup"><span data-stu-id="2baa7-295">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="2baa7-296">Os dicionários<xref:System.Windows.ResourceDictionary>de recursos () podem ser usados para dar suporte a temas de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="2baa7-297">Uma maneira de criar e gerenciar temas é criando diferentes temas como dicionários de recursos localizados em um site de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="2baa7-298">Isso permite que temas sejam adicionados e atualizados sem recompilar e reimplantar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="2baa7-299">Esses dicionários de recursos podem ser identificados e carregados [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]usando o pacote, que é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2baa7-299">These resource dictionaries can be identified and loaded using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="2baa7-300">Para obter uma visão geral dos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]temas no, consulte [estilização e modelagem](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="2baa7-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../controls/styling-and-templating.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2baa7-301">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2baa7-301">See also</span></span>

- [<span data-ttu-id="2baa7-302">Arquivos de recursos, de conteúdo e de dados de aplicativos do WPF</span><span class="sxs-lookup"><span data-stu-id="2baa7-302">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
