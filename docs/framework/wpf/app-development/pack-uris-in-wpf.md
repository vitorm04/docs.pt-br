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
ms.openlocfilehash: 4e005ea96df45da8326386f8b43aa5640ce810b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344345"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="2d6ee-102">URIs "pack://" no WPF</span><span class="sxs-lookup"><span data-stu-id="2d6ee-102">Pack URIs in WPF</span></span>
<span data-ttu-id="2d6ee-103">No Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] são usados para identificar e carregar arquivos de várias maneiras, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-103">In Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] are used to identify and load files in many ways, including the following:</span></span>  
  
-   <span data-ttu-id="2d6ee-104">Especificando o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] para mostrar quando um aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>  
  
-   <span data-ttu-id="2d6ee-105">Carregar imagens.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-105">Loading images.</span></span>  
  
-   <span data-ttu-id="2d6ee-106">Navegar até as páginas.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-106">Navigating to pages.</span></span>  
  
-   <span data-ttu-id="2d6ee-107">Carregar arquivos de dados não executáveis.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-107">Loading non-executable data files.</span></span>  
  
 <span data-ttu-id="2d6ee-108">Além disso, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pode ser usado para identificar e carregar arquivos de uma variedade de locais, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-108">Furthermore, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] can be used to identify and load files from a variety of locations, including the following:</span></span>  
  
-   <span data-ttu-id="2d6ee-109">O assembly atual.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-109">The current assembly.</span></span>  
  
-   <span data-ttu-id="2d6ee-110">Um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-110">A referenced assembly.</span></span>  
  
-   <span data-ttu-id="2d6ee-111">Um local relativo a um assembly.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-111">A location relative to an assembly.</span></span>  
  
-   <span data-ttu-id="2d6ee-112">O site de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-112">The application's site of origin.</span></span>  
  
 <span data-ttu-id="2d6ee-113">Para fornecer um mecanismo consistente para identificar e carregar esses tipos de arquivos a partir desses locais, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utiliza a extensibilidade a *esquema de URI de pacote*.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="2d6ee-114">Este tópico fornece uma visão geral do esquema, aborda como construir um pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para uma variedade de cenários, aborda absolute e relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] e [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolução, antes de mostrar como usar o pacote de [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] de ambos os marcação e o código.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-114">This topic provides an overview of the scheme, covers how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for a variety of scenarios, discusses absolute and relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] and [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution, before showing how to use pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] from both markup and code.</span></span>  

<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a><span data-ttu-id="2d6ee-115">O esquema de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="2d6ee-115">The Pack URI Scheme</span></span>  
 <span data-ttu-id="2d6ee-116">O pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquema é usado pelas [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) especificação (OPC), que descreve um modelo para organizar e identificar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-116">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme is used by the [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="2d6ee-117">Os principais elementos desse modelo são pacotes e partes, onde um *pacote* é um contêiner lógico para uma ou mais lógica *partes*.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="2d6ee-118">A imagem a seguir ilustra esse conceito.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-118">The following figure illustrates this concept.</span></span>  
  
 ![Diagrama de pacote e partes](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)  
  
 <span data-ttu-id="2d6ee-120">Para identificar partes, a especificação OPC utiliza a extensibilidade RFC 2396 (identificadores de recurso uniforme (URI): Sintaxe genérica) para definir o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquema.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme.</span></span>  
  
 <span data-ttu-id="2d6ee-121">O esquema especificado por um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é definido por seu prefixo; http, ftp e file são exemplos bem conhecidos.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-121">The scheme that is specified by a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="2d6ee-122">O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquema usa "pack" como seu esquema e contém dois componentes: autoridade e caminho.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-122">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="2d6ee-123">Este é o formato para um pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-123">The following is the format for a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 <span data-ttu-id="2d6ee-124">pack://*authority*/*path*</span><span class="sxs-lookup"><span data-stu-id="2d6ee-124">pack://*authority*/*path*</span></span>
  
 <span data-ttu-id="2d6ee-125">O *autoridade* Especifica o tipo de pacote que contém a parte, enquanto o *caminho* Especifica o local de uma parte dentro de um pacote.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>  
  
 <span data-ttu-id="2d6ee-126">Esse conceito é ilustrado pela figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-126">This concept is illustrated by the following figure:</span></span>  
  
 ![Relação entre pacote, autoridade e caminho](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)  
  
 <span data-ttu-id="2d6ee-128">Os pacotes e peças são análogos a aplicativos e arquivos, pois um aplicativo (pacote) pode incluir um ou mais arquivos (peças), incluindo:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>  
  
-   <span data-ttu-id="2d6ee-129">Arquivos de recursos que são compilados no assembly local.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-129">Resource files that are compiled into the local assembly.</span></span>  
  
-   <span data-ttu-id="2d6ee-130">Arquivos de recursos que são compilados em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-130">Resource files that are compiled into a referenced assembly.</span></span>  
  
-   <span data-ttu-id="2d6ee-131">Arquivos de recursos que são compilados em um assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-131">Resource files that are compiled into a referencing assembly.</span></span>  
  
-   <span data-ttu-id="2d6ee-132">Arquivos de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-132">Content files.</span></span>  
  
-   <span data-ttu-id="2d6ee-133">Arquivos de site de origem.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-133">Site of origin files.</span></span>  
  
 <span data-ttu-id="2d6ee-134">Para acessar esses tipos de arquivos, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dá suporte a duas autoridades: application: Application:/// e siteoforigin:///: / / /.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="2d6ee-135">A autoridade application:/// identifica arquivos de dados de aplicativo que são conhecidos no tempo de compilação, incluindo arquivos de recurso e conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="2d6ee-136">A autoridade siteoforigin:/// identifica arquivos de site de origem.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="2d6ee-137">O escopo de cada autoridade é mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-137">The scope of each authority is shown in the following figure.</span></span>  
  
 ![Diagrama URI de pacote](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)  
  
> [!NOTE]
>  <span data-ttu-id="2d6ee-139">O componente de autoridade de um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é inserida [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que aponta para um pacote e deve estar em conformidade com RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-139">The authority component of a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is an embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="2d6ee-140">Além disso, o caractere “/” deve ser substituído pelo caractere “,”; caracteres reservados como “%” e “?” devem ser ignorados.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="2d6ee-141">Para ver os detalhes, consulte o OPC.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-141">See the OPC for details.</span></span>  
  
 <span data-ttu-id="2d6ee-142">As seções a seguir explicam como construir um pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] usando essas duas autoridades em conjunto com os caminhos adequados para a identificação de recurso, conteúdo e site de arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-142">The following sections explain how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a><span data-ttu-id="2d6ee-143">URIs de pacote de arquivo de recurso</span><span class="sxs-lookup"><span data-stu-id="2d6ee-143">Resource File Pack URIs</span></span>  
 <span data-ttu-id="2d6ee-144">Arquivos de recurso são configurados como [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` itens e são compilados em assemblies.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-144">Resource files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource` items and are compiled into assemblies.</span></span> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="2d6ee-145">dá suporte à construção de pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que pode ser usado para identificar arquivos de recursos que são compilados no assembly local ou compilados em um assembly que é referenciado no assembly local.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-145">supports the construction of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a><span data-ttu-id="2d6ee-146">Arquivo de recurso de assembly local</span><span class="sxs-lookup"><span data-stu-id="2d6ee-146">Local Assembly Resource File</span></span>  
 <span data-ttu-id="2d6ee-147">O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um recurso de arquivo é compilado no assembly local utiliza a autoridade e caminho a seguir:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-147">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="2d6ee-148">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-148">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="2d6ee-149">**Caminho**: O nome do arquivo de recurso, incluindo seu caminho, relativo à pasta raiz do projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>  
  
 <span data-ttu-id="2d6ee-150">O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado na raiz da pasta do projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-150">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 <span data-ttu-id="2d6ee-151">O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado em uma subpasta da pasta de projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-151">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="2d6ee-152">Arquivo de recurso de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2d6ee-152">Referenced Assembly Resource File</span></span>  
 <span data-ttu-id="2d6ee-153">O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um recurso de arquivo é compilado em um assembly referenciado utiliza a autoridade e caminho a seguir:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-153">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="2d6ee-154">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-154">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="2d6ee-155">**Caminho**: O nome de um arquivo de recurso que é compilado em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="2d6ee-156">O caminho deve estar de acordo com o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-156">The path must conform to the following format:</span></span>  
  
     <span data-ttu-id="2d6ee-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span><span class="sxs-lookup"><span data-stu-id="2d6ee-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>  
  
    -   <span data-ttu-id="2d6ee-158">**AssemblyShortName**: o nome curto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>  
  
    -   <span data-ttu-id="2d6ee-159">**;Version** [opcional]: a versão do assembly referenciado que contém o arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="2d6ee-160">É usada quando são carregados dois ou mais assemblies referenciados com o mesmo nome curto.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>  
  
    -   <span data-ttu-id="2d6ee-161">**;PublicKey** [opcional]: a chave pública que foi usada para assinar o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="2d6ee-162">É usada quando são carregados dois ou mais assemblies referenciados com o mesmo nome curto.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>  
  
    -   <span data-ttu-id="2d6ee-163">**;component**: especifica que o assembly referenciado é referenciado a partir do assembly local.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>  
  
    -   <span data-ttu-id="2d6ee-164">**/Path**: o nome do arquivo de recurso, incluindo o caminho, em relação à raiz da pasta de projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>  
  
 <span data-ttu-id="2d6ee-165">O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado na raiz da pasta do projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-165">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 <span data-ttu-id="2d6ee-166">O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado em uma subpasta da pasta de projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-166">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 <span data-ttu-id="2d6ee-167">O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado na pasta raiz da pasta de projeto de uma versão específica do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-167">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 <span data-ttu-id="2d6ee-168">Observe que o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] sintaxe para arquivos de recurso de assembly referenciado pode ser usada apenas com o aplicativo: autoridade.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-168">Note that the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="2d6ee-169">Por exemplo, o seguinte não é suportado em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a><span data-ttu-id="2d6ee-170">URIs de pacote de arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="2d6ee-170">Content File Pack URIs</span></span>  
 <span data-ttu-id="2d6ee-171">O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um arquivo de conteúdo usa a autoridade e caminho a seguir:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-171">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a content file uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="2d6ee-172">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-172">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="2d6ee-173">**Caminho**: O nome do arquivo de conteúdo, incluindo seu caminho relativo ao local de sistema do arquivo do assembly executável principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>  
  
 <span data-ttu-id="2d6ee-174">O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de conteúdo, localizado na mesma pasta do assembly executável.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-174">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 <span data-ttu-id="2d6ee-175">O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de conteúdo, localizado em uma subpasta que é relativo ao assembly executável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-175">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  <span data-ttu-id="2d6ee-176">Não é possível acessar os arquivos de conteúdo do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-176">[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] content files cannot be navigated to.</span></span> <span data-ttu-id="2d6ee-177">O [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquema dá suporte apenas a navegação para [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] arquivos que estão localizados no site de origem.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-177">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme only supports navigation to [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] files that are located at the site of origin.</span></span>  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="2d6ee-178">URIs de pacote de site de origem</span><span class="sxs-lookup"><span data-stu-id="2d6ee-178">Site of Origin Pack URIs</span></span>  
 <span data-ttu-id="2d6ee-179">O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um site de origem arquivo utiliza a autoridade e caminho a seguir:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-179">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a site of origin file uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="2d6ee-180">**Autoridade**: siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-180">**Authority**: siteoforigin:///.</span></span>  
  
-   <span data-ttu-id="2d6ee-181">**Caminho**: O nome do site do arquivo de origem, incluindo seu caminho relativo ao local do qual o assembly executável foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>  
  
 <span data-ttu-id="2d6ee-182">O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site de origem, armazenado no local do qual o assembly executável é iniciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-182">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 <span data-ttu-id="2d6ee-183">O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site de origem, armazenado na subpasta é relativo ao local do qual o assembly executável do aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-183">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a><span data-ttu-id="2d6ee-184">Arquivos de paginação</span><span class="sxs-lookup"><span data-stu-id="2d6ee-184">Page Files</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="2d6ee-185">arquivos que são configurados como [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` itens são compilados em assemblies da mesma forma como arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-185">files that are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="2d6ee-186">Consequentemente, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` itens podem ser identificados usando o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-186">Consequently, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items can be identified using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files.</span></span>  
  
 <span data-ttu-id="2d6ee-187">Os tipos de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos que normalmente são configurados como [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` itens têm um dos seguintes como seu elemento raiz:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items have one of the following as their root element:</span></span>  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="2d6ee-188">Absolutos vs. URIs de pacote relativo</span><span class="sxs-lookup"><span data-stu-id="2d6ee-188">Absolute vs. Relative Pack URIs</span></span>  
 <span data-ttu-id="2d6ee-189">Um pacote totalmente qualificado [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] inclui o esquema, a autoridade e o caminho, e ele é considerado um pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-189">A fully qualified pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] includes the scheme, the authority, and the path, and it is considered an absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="2d6ee-190">Como simplificação para os desenvolvedores, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementos normalmente permitem que você defina atributos adequados com um pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], que inclui apenas o caminho.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], which includes only the path.</span></span>  
  
 <span data-ttu-id="2d6ee-191">Por exemplo, considere a possibilidade de pacote absoluto a seguir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um arquivo de recurso no assembly local.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-191">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file in the local assembly.</span></span>  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 <span data-ttu-id="2d6ee-192">O pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que se refere a esse recurso de arquivo seria o seguinte.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-192">The relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that refers to this resource file would be the following.</span></span>  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  <span data-ttu-id="2d6ee-193">Porque o site de arquivos de origem não estão associados a assemblies, eles só podem ser referenciados para com o pacote absoluto [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span></span>  
  
 <span data-ttu-id="2d6ee-194">Por padrão, um pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é considerado relativo ao local da marcação ou código que contém a referência.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-194">By default, a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="2d6ee-195">Se uma barra invertida inicial for usada, no entanto, o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] referência, em seguida, é considerada relativa à raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-195">If a leading backslash is used, however, the relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="2d6ee-196">Considere, por exemplo, a estrutura de projeto a seguir.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-196">For example, consider the following project structure.</span></span>  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 <span data-ttu-id="2d6ee-197">Se o Page1.xaml contém um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que referencia *raiz*\SubFolder\Page2.xaml, a referência pode usar o pacote relativo a seguir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-197">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `Page2.xaml`  
  
 <span data-ttu-id="2d6ee-198">Se o Page1.xaml contém um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que referencia *raiz*\Page2.xaml, a referência pode usar o pacote relativo a seguir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-198">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a><span data-ttu-id="2d6ee-199">Resolução de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="2d6ee-199">Pack URI Resolution</span></span>  
 <span data-ttu-id="2d6ee-200">O formato de pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] torna possível para o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para diferentes tipos de arquivos tenham a mesma aparência.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-200">The format of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] makes it possible for pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for different types of files to look the same.</span></span> <span data-ttu-id="2d6ee-201">Por exemplo, considere a possibilidade de pacote absoluto a seguir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-201">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 <span data-ttu-id="2d6ee-202">Este pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pode se referir a um arquivo de recurso no assembly local ou um arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-202">This absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="2d6ee-203">O mesmo é verdadeiro para relativo a seguir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-203">The same is true for the following relative [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `/ResourceOrContentFile.xaml`  
  
 <span data-ttu-id="2d6ee-204">Para determinar o tipo de arquivo que um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] se refere, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolve [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para arquivos de recursos em assemblies locais e arquivos de conteúdo usando a heurística a seguir:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-204">In order to determine the type of file that a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files in local assemblies and content files by using the following heuristics:</span></span>  
  
1. <span data-ttu-id="2d6ee-205">Teste os metadados de assembly para um <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo que corresponde ao pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
2. <span data-ttu-id="2d6ee-206">Se o <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo for encontrado, o caminho do pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refere-se a um arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a content file.</span></span>  
  
3. <span data-ttu-id="2d6ee-207">Se o <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo não for encontrado, verificar o conjunto de arquivos de recursos que é compilados no assembly local.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>  
  
4. <span data-ttu-id="2d6ee-208">Se um arquivo de recurso que corresponde ao caminho do pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for encontrado, o caminho do pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refere-se a um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-208">If a resource file that matches the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a resource file.</span></span>  
  
5. <span data-ttu-id="2d6ee-209">Se o recurso não for encontrado, criado internamente <xref:System.Uri> é inválido.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] <span data-ttu-id="2d6ee-210">resolução não se aplica a [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que se referem ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-210">resolution does not apply for [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that refer to the following:</span></span>  
  
-   <span data-ttu-id="2d6ee-211">Arquivos de conteúdo em assemblies referenciados: não há suporte para esses tipos de arquivo por [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>  
  
-   <span data-ttu-id="2d6ee-212">Arquivos inseridos em assemblies referenciados: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que os identificam são exclusivos, porque eles incluem o nome do assembly referenciado e o `;component` sufixo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-212">Embedded files in referenced assemblies: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>  
  
-   <span data-ttu-id="2d6ee-213">Site de arquivos de origem: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que os identificam são exclusivos, porque eles são os únicos arquivos que podem ser identificados pelo pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que contêm o siteoforigin:///: autoridade.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-213">Site of origin files: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they are the only files that can be identified by pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that contain the siteoforigin:/// authority.</span></span>  
  
 <span data-ttu-id="2d6ee-214">Uma simplificação que pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] permite a resolução é para código um pouco independente dos locais dos arquivos de recurso e conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-214">One simplification that pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="2d6ee-215">Por exemplo, se você tiver um arquivo de recurso no assembly local que foi reconfigurado para ser um arquivo de conteúdo, o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para o recurso permanece o mesmo, assim como o código que usa o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the resource remains the same, as does the code that uses the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a><span data-ttu-id="2d6ee-216">Programando com URIs de pacote</span><span class="sxs-lookup"><span data-stu-id="2d6ee-216">Programming with Pack URIs</span></span>  
 <span data-ttu-id="2d6ee-217">Muitas [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implementam propriedades que podem ser definidas com o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], incluindo:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including:</span></span>  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="2d6ee-218">Essas propriedades podem ser definidas a partir de marcação e código.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="2d6ee-219">Esta seção demonstra as construções básicas para ambos e, depois, mostra exemplos de cenários comuns.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="2d6ee-220">Utilizando URIs de pacote em marcação</span><span class="sxs-lookup"><span data-stu-id="2d6ee-220">Using Pack URIs in Markup</span></span>  
 <span data-ttu-id="2d6ee-221">Um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é especificado na marcação, definindo o elemento de um atributo com o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-221">A pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is specified in markup by setting the element of an attribute with the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="2d6ee-222">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2d6ee-222">For example:</span></span>  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 <span data-ttu-id="2d6ee-223">Tabela 1 mostra o pacote absoluto a vários [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que você pode especificar na marcação.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-223">Table 1 illustrates the various absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>  
  
 <span data-ttu-id="2d6ee-224">Tabela 1: URIs de pacote absolutos em marcação</span><span class="sxs-lookup"><span data-stu-id="2d6ee-224">Table 1: Absolute Pack URIs in Markup</span></span>  
  
|<span data-ttu-id="2d6ee-225">Arquivo</span><span class="sxs-lookup"><span data-stu-id="2d6ee-225">File</span></span>|<span data-ttu-id="2d6ee-226">Pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d6ee-226">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="2d6ee-227">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="2d6ee-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|  
|<span data-ttu-id="2d6ee-228">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="2d6ee-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="2d6ee-229">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2d6ee-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|<span data-ttu-id="2d6ee-230">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2d6ee-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="2d6ee-231">Arquivo de recurso em assembly referenciado com controle de versão</span><span class="sxs-lookup"><span data-stu-id="2d6ee-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|<span data-ttu-id="2d6ee-232">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="2d6ee-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|  
|<span data-ttu-id="2d6ee-233">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="2d6ee-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|<span data-ttu-id="2d6ee-234">Arquivo de site de origem</span><span class="sxs-lookup"><span data-stu-id="2d6ee-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|<span data-ttu-id="2d6ee-235">Arquivo de site de origem em subpasta</span><span class="sxs-lookup"><span data-stu-id="2d6ee-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 <span data-ttu-id="2d6ee-236">Tabela 2 mostra o pacote relativo a vários [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que você pode especificar na marcação.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-236">Table 2 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>  
  
 <span data-ttu-id="2d6ee-237">Tabela 2: URIs de pacote relativos em marcação</span><span class="sxs-lookup"><span data-stu-id="2d6ee-237">Table 2: Relative Pack URIs in Markup</span></span>  
  
|<span data-ttu-id="2d6ee-238">Arquivo</span><span class="sxs-lookup"><span data-stu-id="2d6ee-238">File</span></span>|<span data-ttu-id="2d6ee-239">Pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d6ee-239">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="2d6ee-240">Arquivo de recurso em assembly local</span><span class="sxs-lookup"><span data-stu-id="2d6ee-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|  
|<span data-ttu-id="2d6ee-241">Arquivo de recurso em subpasta de assembly local</span><span class="sxs-lookup"><span data-stu-id="2d6ee-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="2d6ee-242">Arquivo de recurso em assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2d6ee-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|<span data-ttu-id="2d6ee-243">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2d6ee-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="2d6ee-244">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="2d6ee-244">Content file</span></span>|`"/ContentFile.xaml"`|  
|<span data-ttu-id="2d6ee-245">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="2d6ee-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a><span data-ttu-id="2d6ee-246">Utilizando URIs de pacote em código</span><span class="sxs-lookup"><span data-stu-id="2d6ee-246">Using Pack URIs in Code</span></span>  
 <span data-ttu-id="2d6ee-247">Especifique um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] no código pela instanciação do <xref:System.Uri> classe e passando o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] como um parâmetro para o construtor.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-247">You specify a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] in code by instantiating the <xref:System.Uri> class and passing the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] as a parameter to the constructor.</span></span> <span data-ttu-id="2d6ee-248">Isso é demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-248">This is demonstrated in the following example.</span></span>  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 <span data-ttu-id="2d6ee-249">Por padrão, o <xref:System.Uri> classe considera pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para serem absolutos.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-249">By default, the <xref:System.Uri> class considers pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to be absolute.</span></span> <span data-ttu-id="2d6ee-250">Consequentemente, uma exceção é gerada quando uma instância das <xref:System.Uri> classe é criada com um pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d6ee-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 <span data-ttu-id="2d6ee-251">Felizmente, o <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> sobrecarga da <xref:System.Uri> construtor de classe aceita um parâmetro do tipo <xref:System.UriKind> para permitir que você especifique se um pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é relativo ou absoluto.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is either absolute or relative.</span></span>  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 <span data-ttu-id="2d6ee-252">Você deve especificar apenas <xref:System.UriKind.Absolute> ou <xref:System.UriKind.Relative> quando você tiver certeza de que o pacote fornecido [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é um ou outro.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is one or the other.</span></span> <span data-ttu-id="2d6ee-253">Se você não souber o tipo de pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que é usada, como quando um usuário insere um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] em tempo de execução, use <xref:System.UriKind.RelativeOrAbsolute> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-253">If you don't know the type of pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that is used, such as when a user enters a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 <span data-ttu-id="2d6ee-254">Tabela 3 ilustra um pacote relativo a vários [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que você pode especificar no código usando <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-254">Table 3 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="2d6ee-255">Tabela 3: URIs de pacote absolutos em código</span><span class="sxs-lookup"><span data-stu-id="2d6ee-255">Table 3: Absolute Pack URIs in Code</span></span>  
  
|<span data-ttu-id="2d6ee-256">Arquivo</span><span class="sxs-lookup"><span data-stu-id="2d6ee-256">File</span></span>|<span data-ttu-id="2d6ee-257">Pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d6ee-257">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="2d6ee-258">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="2d6ee-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="2d6ee-259">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="2d6ee-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="2d6ee-260">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2d6ee-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="2d6ee-261">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2d6ee-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="2d6ee-262">Arquivo de recurso em assembly referenciado com controle de versão</span><span class="sxs-lookup"><span data-stu-id="2d6ee-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="2d6ee-263">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="2d6ee-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="2d6ee-264">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="2d6ee-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="2d6ee-265">Arquivo de site de origem</span><span class="sxs-lookup"><span data-stu-id="2d6ee-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="2d6ee-266">Arquivo de site de origem em subpasta</span><span class="sxs-lookup"><span data-stu-id="2d6ee-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 <span data-ttu-id="2d6ee-267">Tabela 4 mostra um pacote relativo a vários [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que você pode especificar no código usando <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-267">Table 4 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="2d6ee-268">Tabela 4: URIs de pacote relativos em código</span><span class="sxs-lookup"><span data-stu-id="2d6ee-268">Table 4: Relative Pack URIs in Code</span></span>  
  
|<span data-ttu-id="2d6ee-269">Arquivo</span><span class="sxs-lookup"><span data-stu-id="2d6ee-269">File</span></span>|<span data-ttu-id="2d6ee-270">Pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d6ee-270">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="2d6ee-271">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="2d6ee-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="2d6ee-272">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="2d6ee-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="2d6ee-273">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2d6ee-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="2d6ee-274">Arquivo de recurso em subpasta - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="2d6ee-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="2d6ee-275">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="2d6ee-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="2d6ee-276">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="2d6ee-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="2d6ee-277">Cenários comuns de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="2d6ee-277">Common Pack URI Scenarios</span></span>  
 <span data-ttu-id="2d6ee-278">As seções anteriores discutiram como construir um pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para identificar o recurso, conteúdo e site de arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-278">The preceding sections have discussed how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="2d6ee-279">No [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], essas construções são usadas em uma variedade de formas e as seções a seguir abrangem vários usos comuns.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="2d6ee-280">Especificando a interface do usuário para mostrar quando um aplicativo foi iniciado</span><span class="sxs-lookup"><span data-stu-id="2d6ee-280">Specifying the UI to Show When an Application Starts</span></span>  
 <span data-ttu-id="2d6ee-281"><xref:System.Windows.Application.StartupUri%2A> Especifica o primeiro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para mostrar quando um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="2d6ee-282">Para aplicativos autônomos, o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pode ser uma janela, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 <span data-ttu-id="2d6ee-283">Aplicativos autônomos e [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] também pode especificar uma página como a interface do usuário inicial, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 <span data-ttu-id="2d6ee-284">Se o aplicativo é um aplicativo autônomo e uma página é especificada com <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] abre uma <xref:System.Windows.Navigation.NavigationWindow> para hospedar a página.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="2d6ee-285">Para [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], a página é exibida no navegador host.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a><span data-ttu-id="2d6ee-286">Navegando até uma página</span><span class="sxs-lookup"><span data-stu-id="2d6ee-286">Navigating to a Page</span></span>  
 <span data-ttu-id="2d6ee-287">O exemplo a seguir mostra como navegar até uma página.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-287">The following example shows how to navigate to a page.</span></span>  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 <span data-ttu-id="2d6ee-288">Para obter mais informações sobre as várias maneiras de navegar no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consulte [visão geral da navegação](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2d6ee-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](navigation-overview.md).</span></span>  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a><span data-ttu-id="2d6ee-289">Especificando um ícone de janela</span><span class="sxs-lookup"><span data-stu-id="2d6ee-289">Specifying a Window Icon</span></span>  
 <span data-ttu-id="2d6ee-290">O exemplo a seguir mostra como usar um URI para especificar um ícone de janela.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-290">The following example shows how to use a URI to specify a window's icon.</span></span>  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 <span data-ttu-id="2d6ee-291">Para obter mais informações, consulte <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="2d6ee-292">Carregando arquivos de imagem, áudio e vídeo</span><span class="sxs-lookup"><span data-stu-id="2d6ee-292">Loading Image, Audio, and Video Files</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="2d6ee-293">permite que aplicativos usem uma grande variedade de tipos de mídia, que podem ser identificados e carregados com o pacote de [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-293">allows applications to use a wide variety of media types, all of which can be identified and loaded with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], as shown in the following examples.</span></span>  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 <span data-ttu-id="2d6ee-294">Para obter mais informações sobre como trabalhar com conteúdo de mídia, consulte [gráficos e multimídia](../graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="2d6ee-294">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="2d6ee-295">Carregando um dicionário de recursos a partir do site de origem</span><span class="sxs-lookup"><span data-stu-id="2d6ee-295">Loading a Resource Dictionary from the Site of Origin</span></span>  
 <span data-ttu-id="2d6ee-296">Dicionários de recursos (<xref:System.Windows.ResourceDictionary>) pode ser usado para dar suporte a temas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="2d6ee-297">Uma maneira de criar e gerenciar temas é criando diferentes temas como dicionários de recursos localizados em um site de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="2d6ee-298">Isso permite que temas sejam adicionados e atualizados sem recompilar e reimplantar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="2d6ee-299">Esses dicionários de recursos podem ser identificados e carregados usando [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], que é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2d6ee-299">These resource dictionaries can be identified and loaded using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], which is shown in the following example.</span></span>  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 <span data-ttu-id="2d6ee-300">Para uma visão geral de temas [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consulte [Styling and Templating](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="2d6ee-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../controls/styling-and-templating.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d6ee-301">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d6ee-301">See also</span></span>

- [<span data-ttu-id="2d6ee-302">Arquivos de recursos, de conteúdo e de dados de aplicativos do WPF</span><span class="sxs-lookup"><span data-stu-id="2d6ee-302">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
