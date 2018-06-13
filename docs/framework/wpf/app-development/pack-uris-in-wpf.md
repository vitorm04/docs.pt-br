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
ms.openlocfilehash: ae96ec40cbbf0a29f780c059b9873c185b2975d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558142"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="f2aa7-102">URIs "pack://" no WPF</span><span class="sxs-lookup"><span data-stu-id="f2aa7-102">Pack URIs in WPF</span></span>
<span data-ttu-id="f2aa7-103">No Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] são usados para identificar e carregar arquivos de várias maneiras, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-103">In Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] are used to identify and load files in many ways, including the following:</span></span>  
  
-   <span data-ttu-id="f2aa7-104">Especificando o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] para mostrar quando um aplicativo iniciado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>  
  
-   <span data-ttu-id="f2aa7-105">Carregar imagens.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-105">Loading images.</span></span>  
  
-   <span data-ttu-id="f2aa7-106">Navegar até as páginas.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-106">Navigating to pages.</span></span>  
  
-   <span data-ttu-id="f2aa7-107">Carregar arquivos de dados não executáveis.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-107">Loading non-executable data files.</span></span>  
  
 <span data-ttu-id="f2aa7-108">Além disso, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pode ser usado para identificar e carregar arquivos de uma variedade de locais, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-108">Furthermore, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] can be used to identify and load files from a variety of locations, including the following:</span></span>  
  
-   <span data-ttu-id="f2aa7-109">O assembly atual.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-109">The current assembly.</span></span>  
  
-   <span data-ttu-id="f2aa7-110">Um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-110">A referenced assembly.</span></span>  
  
-   <span data-ttu-id="f2aa7-111">Um local relativo a um assembly.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-111">A location relative to an assembly.</span></span>  
  
-   <span data-ttu-id="f2aa7-112">O site de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-112">The application's site of origin.</span></span>  
  
 <span data-ttu-id="f2aa7-113">Para fornecer um mecanismo consistente para identificar e carregar esses tipos de arquivos a partir desses locais, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utiliza a extensibilidade do *esquema de URI de pacote*.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="f2aa7-114">Este tópico fornece uma visão geral do esquema, aborda como criar pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para uma variedade de cenários, discute absolute e relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] e [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolução, antes de mostrar como usar o pacote de [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] de ambos os marcação e o código.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-114">This topic provides an overview of the scheme, covers how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for a variety of scenarios, discusses absolute and relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] and [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution, before showing how to use pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] from both markup and code.</span></span>  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a><span data-ttu-id="f2aa7-115">O esquema de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="f2aa7-115">The Pack URI Scheme</span></span>  
 <span data-ttu-id="f2aa7-116">O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquema é usada pelo [Open Packaging Conventions](http://go.microsoft.com/fwlink/?LinkID=71255) especificação (OPC), que descreve um modelo para organizar e identificar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-116">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme is used by the [Open Packaging Conventions](http://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="f2aa7-117">Os principais elementos desse modelo são pacotes e partes, onde um *pacote* é um contêiner lógico para uma ou mais lógica *partes*.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="f2aa7-118">A imagem a seguir ilustra esse conceito.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-118">The following figure illustrates this concept.</span></span>  
  
 <span data-ttu-id="f2aa7-119">![Diagrama de pacote e peças](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")</span><span class="sxs-lookup"><span data-stu-id="f2aa7-119">![Package and Parts diagram](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")</span></span>  
  
 <span data-ttu-id="f2aa7-120">Para identificar partes, a especificação OPC utiliza a extensibilidade do RFC 2396 (identificadores de recurso uniforme (URI): sintaxe genérica) para definir o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquema.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme.</span></span>  
  
 <span data-ttu-id="f2aa7-121">O esquema especificado por um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é definido por seu prefixo; http, ftp e file são exemplos bem conhecidos.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-121">The scheme that is specified by a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="f2aa7-122">O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquema utiliza "pack" como seu esquema e contém dois componentes: autoridade e caminho.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-122">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="f2aa7-123">Este é o formato para um pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-123">The following is the format for a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 <span data-ttu-id="f2aa7-124">pacote: / /*autoridade*/*caminho*</span><span class="sxs-lookup"><span data-stu-id="f2aa7-124">pack://*authority*/*path*</span></span>
  
 <span data-ttu-id="f2aa7-125">O *autoridade* Especifica o tipo de pacote que contém a parte, enquanto o *caminho* Especifica o local de uma parte dentro de um pacote.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>  
  
 <span data-ttu-id="f2aa7-126">Esse conceito é ilustrado pela figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-126">This concept is illustrated by the following figure:</span></span>  
  
 <span data-ttu-id="f2aa7-127">![Relação entre pacote, autoridade e caminho](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")</span><span class="sxs-lookup"><span data-stu-id="f2aa7-127">![Relationship among package, authority, and path](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")</span></span>  
  
 <span data-ttu-id="f2aa7-128">Os pacotes e peças são análogos a aplicativos e arquivos, pois um aplicativo (pacote) pode incluir um ou mais arquivos (peças), incluindo:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>  
  
-   <span data-ttu-id="f2aa7-129">Arquivos de recursos que são compilados no assembly local.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-129">Resource files that are compiled into the local assembly.</span></span>  
  
-   <span data-ttu-id="f2aa7-130">Arquivos de recursos que são compilados em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-130">Resource files that are compiled into a referenced assembly.</span></span>  
  
-   <span data-ttu-id="f2aa7-131">Arquivos de recursos que são compilados em um assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-131">Resource files that are compiled into a referencing assembly.</span></span>  
  
-   <span data-ttu-id="f2aa7-132">Arquivos de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-132">Content files.</span></span>  
  
-   <span data-ttu-id="f2aa7-133">Arquivos de site de origem.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-133">Site of origin files.</span></span>  
  
 <span data-ttu-id="f2aa7-134">Para acessar esses tipos de arquivos, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] suporta duas autoridades: application: / / / e siteoforigin: / / /.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="f2aa7-135">A autoridade application:/// identifica arquivos de dados de aplicativo que são conhecidos no tempo de compilação, incluindo arquivos de recurso e conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="f2aa7-136">A autoridade siteoforigin:/// identifica arquivos de site de origem.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="f2aa7-137">O escopo de cada autoridade é mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-137">The scope of each authority is shown in the following figure.</span></span>  
  
 <span data-ttu-id="f2aa7-138">![Diagrama de URI de pacote](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")</span><span class="sxs-lookup"><span data-stu-id="f2aa7-138">![Pack URI diagram](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2aa7-139">O componente de autoridade de um pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é inserida [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que aponta para um pacote de acordo com RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-139">The authority component of a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is an embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="f2aa7-140">Além disso, o caractere “/” deve ser substituído pelo caractere “,”; caracteres reservados como “%” e “?” devem ser ignorados.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="f2aa7-141">Para ver os detalhes, consulte o OPC.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-141">See the OPC for details.</span></span>  
  
 <span data-ttu-id="f2aa7-142">As seções a seguir explicam como criar pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] usando estas duas autoridades em conjunto com os caminhos apropriados para a identificação de recurso, o conteúdo e o local dos arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-142">The following sections explain how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a><span data-ttu-id="f2aa7-143">URIs de pacote de arquivo de recurso</span><span class="sxs-lookup"><span data-stu-id="f2aa7-143">Resource File Pack URIs</span></span>  
 <span data-ttu-id="f2aa7-144">Arquivos de recurso são configurados como [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` itens e são compilados em assemblies.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-144">Resource files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource` items and are compiled into assemblies.</span></span> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="f2aa7-145"> oferece suporte a construção de pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que pode ser usado para identificar arquivos de recursos que são compilados no assembly local ou compilados em um assembly que é referenciado no assembly local.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-145"> supports the construction of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a><span data-ttu-id="f2aa7-146">Arquivo de recurso de assembly local</span><span class="sxs-lookup"><span data-stu-id="f2aa7-146">Local Assembly Resource File</span></span>  
 <span data-ttu-id="f2aa7-147">O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um recurso de arquivo que é compilado no assembly local usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-147">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="f2aa7-148">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-148">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="f2aa7-149">**Caminho**: o nome do arquivo de recurso, incluindo seu caminho, em relação à raiz da pasta de projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>  
  
 <span data-ttu-id="f2aa7-150">O exemplo a seguir mostra o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado na raiz da pasta de projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-150">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 <span data-ttu-id="f2aa7-151">O exemplo a seguir mostra o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado em uma subpasta da pasta de projeto do assembly local.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-151">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="f2aa7-152">Arquivo de recurso de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f2aa7-152">Referenced Assembly Resource File</span></span>  
 <span data-ttu-id="f2aa7-153">O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um recurso de arquivo que é compilado em um assembly referenciado utiliza a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-153">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="f2aa7-154">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-154">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="f2aa7-155">**Caminho**: o nome de um arquivo de recurso compilado em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="f2aa7-156">O caminho deve estar de acordo com o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-156">The path must conform to the following format:</span></span>  
  
     <span data-ttu-id="f2aa7-157">*AssemblyShortName*{*; Versão*] {*; PublicKey*]; component /*caminho*</span><span class="sxs-lookup"><span data-stu-id="f2aa7-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>  
  
    -   <span data-ttu-id="f2aa7-158">**AssemblyShortName**: o nome curto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>  
  
    -   <span data-ttu-id="f2aa7-159">**;Version** [opcional]: a versão do assembly referenciado que contém o arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="f2aa7-160">É usada quando são carregados dois ou mais assemblies referenciados com o mesmo nome curto.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>  
  
    -   <span data-ttu-id="f2aa7-161">**;PublicKey** [opcional]: a chave pública que foi usada para assinar o assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="f2aa7-162">É usada quando são carregados dois ou mais assemblies referenciados com o mesmo nome curto.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>  
  
    -   <span data-ttu-id="f2aa7-163">**;component**: especifica que o assembly referenciado é referenciado a partir do assembly local.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>  
  
    -   <span data-ttu-id="f2aa7-164">**/Path**: o nome do arquivo de recurso, incluindo o caminho, em relação à raiz da pasta de projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>  
  
 <span data-ttu-id="f2aa7-165">O exemplo a seguir mostra o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado na raiz da pasta de projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-165">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 <span data-ttu-id="f2aa7-166">O exemplo a seguir mostra o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado em uma subpasta da pasta de projeto do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-166">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 <span data-ttu-id="f2aa7-167">O exemplo a seguir mostra o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado na pasta raiz da pasta de projeto de uma versão específica de assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-167">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 <span data-ttu-id="f2aa7-168">Observe que o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] sintaxe para arquivos de recurso de assembly referenciado pode ser usada apenas com o aplicativo: / / / autoridade.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-168">Note that the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="f2aa7-169">Por exemplo, o seguinte não é suportado em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a><span data-ttu-id="f2aa7-170">URIs de pacote de arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2aa7-170">Content File Pack URIs</span></span>  
 <span data-ttu-id="f2aa7-171">O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um arquivo de conteúdo utiliza os seguintes autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-171">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a content file uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="f2aa7-172">**Autoridade**: application:///.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-172">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="f2aa7-173">**Caminho**: o nome do arquivo de conteúdo, incluindo o caminho em relação ao local do sistema de arquivos do principal assembly executável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>  
  
 <span data-ttu-id="f2aa7-174">O exemplo a seguir mostra o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de conteúdo, localizado na mesma pasta do assembly executável.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-174">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 <span data-ttu-id="f2aa7-175">O exemplo a seguir mostra o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de conteúdo, localizado em uma subpasta que é relativo ao assembly executável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-175">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  <span data-ttu-id="f2aa7-176">Não é possível acessar os arquivos de conteúdo do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-176">[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] content files cannot be navigated to.</span></span> <span data-ttu-id="f2aa7-177">O [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquema só oferece suporte à navegação para [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] arquivos que estão localizados no site de origem.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-177">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme only supports navigation to [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] files that are located at the site of origin.</span></span>  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="f2aa7-178">URIs de pacote de site de origem</span><span class="sxs-lookup"><span data-stu-id="f2aa7-178">Site of Origin Pack URIs</span></span>  
 <span data-ttu-id="f2aa7-179">O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um site de origem arquivo usa a seguinte autoridade e caminho:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-179">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a site of origin file uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="f2aa7-180">**Autoridade**: siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-180">**Authority**: siteoforigin:///.</span></span>  
  
-   <span data-ttu-id="f2aa7-181">**Caminho**: o nome do arquivo de site de origem, incluindo o caminho em relação ao local a partir do qual o assembly executável foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>  
  
 <span data-ttu-id="f2aa7-182">O exemplo a seguir mostra o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] local do arquivo de origem, armazenado no local de onde o assembly executável foi lançado.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-182">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 <span data-ttu-id="f2aa7-183">O exemplo a seguir mostra o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] local do arquivo de origem, armazenado na subpasta é relativo ao local de onde o assembly executável do aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-183">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a><span data-ttu-id="f2aa7-184">Arquivos de paginação</span><span class="sxs-lookup"><span data-stu-id="f2aa7-184">Page Files</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="f2aa7-185"> arquivos que são configurados como [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` itens são compilados em assemblies da mesma forma como arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-185"> files that are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="f2aa7-186">Consequentemente, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` itens podem ser identificados usando o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-186">Consequently, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items can be identified using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files.</span></span>  
  
 <span data-ttu-id="f2aa7-187">Os tipos de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos normalmente são configurados como [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` itens têm um dos seguintes como seu elemento raiz:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items have one of the following as their root element:</span></span>  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="f2aa7-188">Vs absolutos. URIs de pacote relativa</span><span class="sxs-lookup"><span data-stu-id="f2aa7-188">Absolute vs. Relative Pack URIs</span></span>  
 <span data-ttu-id="f2aa7-189">Um pacote completo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] inclui o esquema, a autoridade e o caminho, e é considerado um pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-189">A fully qualified pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] includes the scheme, the authority, and the path, and it is considered an absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="f2aa7-190">Como simplificação para desenvolvedores, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementos normalmente permitem que você defina os atributos apropriados com um pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], que inclui apenas o caminho.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], which includes only the path.</span></span>  
  
 <span data-ttu-id="f2aa7-191">Por exemplo, considere o seguinte pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um arquivo de recurso no assembly local.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-191">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file in the local assembly.</span></span>  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 <span data-ttu-id="f2aa7-192">O pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que se refere a esse recurso arquivo seria o seguinte.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-192">The relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that refers to this resource file would be the following.</span></span>  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  <span data-ttu-id="f2aa7-193">Porque o site de arquivos de origem não estão associados a assemblies, eles só podem ser referenciados em absoluto pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span></span>  
  
 <span data-ttu-id="f2aa7-194">Por padrão, um pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é considerado relativo ao local da marcação ou código que contém a referência.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-194">By default, a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="f2aa7-195">Se uma barra invertida inicial for usada, no entanto, o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] referência é considerada em relação à raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-195">If a leading backslash is used, however, the relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="f2aa7-196">Considere, por exemplo, a estrutura de projeto a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-196">For example, consider the following project structure.</span></span>  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 <span data-ttu-id="f2aa7-197">Se Page1 contém um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que referencia *raiz*\SubFolder\Page2.xaml, a referência pode usar o seguinte pacote relativa [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-197">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `Page2.xaml`  
  
 <span data-ttu-id="f2aa7-198">Se Page1 contém um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que referencia *raiz*\Page2.xaml, a referência pode usar o seguinte pacote relativa [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-198">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a><span data-ttu-id="f2aa7-199">Resolução de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="f2aa7-199">Pack URI Resolution</span></span>  
 <span data-ttu-id="f2aa7-200">O formato de pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] tornam possível para o pacote de [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para diferentes tipos de arquivos para a mesma aparência.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-200">The format of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] makes it is possible for pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for different types of files to look the same.</span></span> <span data-ttu-id="f2aa7-201">Por exemplo, considere o seguinte pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-201">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 <span data-ttu-id="f2aa7-202">Este pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pode se referir a um arquivo de recurso no assembly local ou um arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-202">This absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="f2aa7-203">O mesmo é verdadeiro para seguir relativa [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-203">The same is true for the following relative [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `/ResourceOrContentFile.xaml`  
  
 <span data-ttu-id="f2aa7-204">Para determinar o tipo de arquivo que um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] se refere, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolve [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para arquivos de recurso em assemblies locais e arquivos de conteúdo usando a heurística do seguinte:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-204">In order to determine the type of file that a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files in local assemblies and content files by using the following heuristics:</span></span>  
  
1.  <span data-ttu-id="f2aa7-205">Teste os metadados de assembly para um <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo que coincide com o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
2.  <span data-ttu-id="f2aa7-206">Se o <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo for encontrado, o caminho do pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] se refere a um arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a content file.</span></span>  
  
3.  <span data-ttu-id="f2aa7-207">Se o <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo não for encontrado, verificar o conjunto de arquivos de recursos que é compilados no assembly local.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>  
  
4.  <span data-ttu-id="f2aa7-208">Se um arquivo de recurso que corresponde ao caminho do pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for encontrado, o caminho do pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] se refere a um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-208">If a resource file that matches the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a resource file.</span></span>  
  
5.  <span data-ttu-id="f2aa7-209">Se o recurso não for encontrado, criado internamente <xref:System.Uri> é inválido.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]<span data-ttu-id="f2aa7-210"> resolução não se aplica a [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que se referem ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-210"> resolution does not apply for [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that refer to the following:</span></span>  
  
-   <span data-ttu-id="f2aa7-211">Arquivos de conteúdo em assemblies referenciados: não há suporte para esses tipos de arquivo por [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>  
  
-   <span data-ttu-id="f2aa7-212">Arquivos incorporados em assemblies referenciados: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que possa identificá-los são exclusivos, pois eles incluem o nome do assembly referenciado e o `;component` sufixo.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-212">Embedded files in referenced assemblies: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>  
  
-   <span data-ttu-id="f2aa7-213">Site de arquivos de origem: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que possa identificá-los são exclusivas porque são apenas os arquivos que podem ser identificados pelo pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que contêm o siteoforigin: / / / autoridade.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-213">Site of origin files: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they are the only files that can be identified by pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that contain the siteoforigin:/// authority.</span></span>  
  
 <span data-ttu-id="f2aa7-214">Simplificação de um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolução permite é para código ser independente dos locais de arquivos de conteúdo e recursos.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-214">One simplification that pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="f2aa7-215">Por exemplo, se você tiver um arquivo de recurso no assembly local reconfigurado como um arquivo de conteúdo, o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para o recurso permanece o mesmo, assim como o código que usa o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the resource remains the same, as does the code that uses the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a><span data-ttu-id="f2aa7-216">Programando com URIs de pacote</span><span class="sxs-lookup"><span data-stu-id="f2aa7-216">Programming with Pack URIs</span></span>  
 <span data-ttu-id="f2aa7-217">Muitos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implementam propriedades que podem ser definidas com o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], incluindo:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including:</span></span>  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="f2aa7-218">Essas propriedades podem ser definidas a partir de marcação e código.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="f2aa7-219">Esta seção demonstra as construções básicas para ambos e, depois, mostra exemplos de cenários comuns.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="f2aa7-220">Utilizando URIs de pacote em marcação</span><span class="sxs-lookup"><span data-stu-id="f2aa7-220">Using Pack URIs in Markup</span></span>  
 <span data-ttu-id="f2aa7-221">Um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é especificada em marcação definindo o elemento de um atributo com o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-221">A pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is specified in markup by setting the element of an attribute with the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="f2aa7-222">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f2aa7-222">For example:</span></span>  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 <span data-ttu-id="f2aa7-223">Tabela 1 ilustra o pacote absoluto vários [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que você pode especificar na marcação.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-223">Table 1 illustrates the various absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>  
  
 <span data-ttu-id="f2aa7-224">Tabela 1: URIs de pacote absolutos em marcação</span><span class="sxs-lookup"><span data-stu-id="f2aa7-224">Table 1: Absolute Pack URIs in Markup</span></span>  
  
|<span data-ttu-id="f2aa7-225">Arquivo</span><span class="sxs-lookup"><span data-stu-id="f2aa7-225">File</span></span>|<span data-ttu-id="f2aa7-226">Pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2aa7-226">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="f2aa7-227">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="f2aa7-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|  
|<span data-ttu-id="f2aa7-228">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="f2aa7-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="f2aa7-229">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f2aa7-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|<span data-ttu-id="f2aa7-230">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f2aa7-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="f2aa7-231">Arquivo de recurso em assembly referenciado com controle de versão</span><span class="sxs-lookup"><span data-stu-id="f2aa7-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|<span data-ttu-id="f2aa7-232">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2aa7-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|  
|<span data-ttu-id="f2aa7-233">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="f2aa7-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|<span data-ttu-id="f2aa7-234">Arquivo de site de origem</span><span class="sxs-lookup"><span data-stu-id="f2aa7-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|<span data-ttu-id="f2aa7-235">Arquivo de site de origem em subpasta</span><span class="sxs-lookup"><span data-stu-id="f2aa7-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 <span data-ttu-id="f2aa7-236">Tabela 2 ilustra o pacote relativo vários [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que você pode especificar na marcação.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-236">Table 2 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>  
  
 <span data-ttu-id="f2aa7-237">Tabela 2: URIs de pacote relativos em marcação</span><span class="sxs-lookup"><span data-stu-id="f2aa7-237">Table 2: Relative Pack URIs in Markup</span></span>  
  
|<span data-ttu-id="f2aa7-238">Arquivo</span><span class="sxs-lookup"><span data-stu-id="f2aa7-238">File</span></span>|<span data-ttu-id="f2aa7-239">Pacote relativa [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2aa7-239">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="f2aa7-240">Arquivo de recurso em assembly local</span><span class="sxs-lookup"><span data-stu-id="f2aa7-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|  
|<span data-ttu-id="f2aa7-241">Arquivo de recurso em subpasta de assembly local</span><span class="sxs-lookup"><span data-stu-id="f2aa7-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="f2aa7-242">Arquivo de recurso em assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f2aa7-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|<span data-ttu-id="f2aa7-243">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f2aa7-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="f2aa7-244">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2aa7-244">Content file</span></span>|`"/ContentFile.xaml"`|  
|<span data-ttu-id="f2aa7-245">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="f2aa7-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a><span data-ttu-id="f2aa7-246">Utilizando URIs de pacote em código</span><span class="sxs-lookup"><span data-stu-id="f2aa7-246">Using Pack URIs in Code</span></span>  
 <span data-ttu-id="f2aa7-247">Especifique um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] em código instanciando a <xref:System.Uri> classe e passar o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] como um parâmetro para o construtor.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-247">You specify a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] in code by instantiating the <xref:System.Uri> class and passing the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] as a parameter to the constructor.</span></span> <span data-ttu-id="f2aa7-248">Isso é demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-248">This is demonstrated in the following example.</span></span>  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 <span data-ttu-id="f2aa7-249">Por padrão, o <xref:System.Uri> classe considera pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] ser absoluto.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-249">By default, the <xref:System.Uri> class considers pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to be absolute.</span></span> <span data-ttu-id="f2aa7-250">Consequentemente, uma exceção é gerada quando uma instância do <xref:System.Uri> classe é criada com um pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2aa7-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 <span data-ttu-id="f2aa7-251">Felizmente, o <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> de sobrecarga do <xref:System.Uri> construtor de classe aceita um parâmetro de tipo <xref:System.UriKind> para permitir que você especifique se um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é absoluta ou relativa.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is either absolute or relative.</span></span>  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 <span data-ttu-id="f2aa7-252">Você deve especificar somente <xref:System.UriKind.Absolute> ou <xref:System.UriKind.Relative> quando você tiver certeza de que o pacote fornecido [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é um ou outro.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is one or the other.</span></span> <span data-ttu-id="f2aa7-253">Se você não souber o tipo de pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que é usada, como quando um usuário entra em um pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] em tempo de execução, use <xref:System.UriKind.RelativeOrAbsolute> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-253">If you don't know the type of pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that is used, such as when a user enters a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 <span data-ttu-id="f2aa7-254">Tabela 3 ilustra o pacote relativo vários [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que você pode especificar no código usando <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-254">Table 3 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f2aa7-255">Tabela 3: URIs de pacote absolutos em código</span><span class="sxs-lookup"><span data-stu-id="f2aa7-255">Table 3: Absolute Pack URIs in Code</span></span>  
  
|<span data-ttu-id="f2aa7-256">Arquivo</span><span class="sxs-lookup"><span data-stu-id="f2aa7-256">File</span></span>|<span data-ttu-id="f2aa7-257">Pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2aa7-257">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="f2aa7-258">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="f2aa7-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="f2aa7-259">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="f2aa7-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="f2aa7-260">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f2aa7-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="f2aa7-261">Arquivo de recurso em subpasta de assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f2aa7-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="f2aa7-262">Arquivo de recurso em assembly referenciado com controle de versão</span><span class="sxs-lookup"><span data-stu-id="f2aa7-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="f2aa7-263">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2aa7-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="f2aa7-264">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="f2aa7-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="f2aa7-265">Arquivo de site de origem</span><span class="sxs-lookup"><span data-stu-id="f2aa7-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="f2aa7-266">Arquivo de site de origem em subpasta</span><span class="sxs-lookup"><span data-stu-id="f2aa7-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 <span data-ttu-id="f2aa7-267">Tabela 4 ilustra o pacote relativo vários [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que você pode especificar no código usando <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-267">Table 4 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f2aa7-268">Tabela 4: URIs de pacote relativos em código</span><span class="sxs-lookup"><span data-stu-id="f2aa7-268">Table 4: Relative Pack URIs in Code</span></span>  
  
|<span data-ttu-id="f2aa7-269">Arquivo</span><span class="sxs-lookup"><span data-stu-id="f2aa7-269">File</span></span>|<span data-ttu-id="f2aa7-270">Pacote relativa [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2aa7-270">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="f2aa7-271">Arquivo de recurso - assembly local</span><span class="sxs-lookup"><span data-stu-id="f2aa7-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="f2aa7-272">Arquivo de recurso em subpasta - assembly local</span><span class="sxs-lookup"><span data-stu-id="f2aa7-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="f2aa7-273">Arquivo de recurso - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f2aa7-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="f2aa7-274">Arquivo de recurso em subpasta - assembly referenciado</span><span class="sxs-lookup"><span data-stu-id="f2aa7-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="f2aa7-275">Arquivo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2aa7-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="f2aa7-276">Arquivo de conteúdo em subpasta</span><span class="sxs-lookup"><span data-stu-id="f2aa7-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="f2aa7-277">Cenários comuns de URI de pacote</span><span class="sxs-lookup"><span data-stu-id="f2aa7-277">Common Pack URI Scenarios</span></span>  
 <span data-ttu-id="f2aa7-278">As seções anteriores discutimos como construir pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para identificar recursos, o conteúdo e o local dos arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-278">The preceding sections have discussed how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="f2aa7-279">Em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], essas construções são usadas em uma variedade de formas e as seções a seguir abrangem vários usos comuns.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="f2aa7-280">Especificando a interface do usuário para mostrar quando um aplicativo foi iniciado</span><span class="sxs-lookup"><span data-stu-id="f2aa7-280">Specifying the UI to Show When an Application Starts</span></span>  
 <span data-ttu-id="f2aa7-281"><xref:System.Windows.Application.StartupUri%2A> Especifica o primeiro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para mostrar quando um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="f2aa7-282">Para aplicativos autônomos, o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pode ser uma janela, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 <span data-ttu-id="f2aa7-283">Aplicativos autônomos e [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] também pode especificar uma página como a interface do usuário inicial, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 <span data-ttu-id="f2aa7-284">Se o aplicativo é um aplicativo autônomo e uma página é especificada com <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] abre um <xref:System.Windows.Navigation.NavigationWindow> para hospedar a página.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="f2aa7-285">Para [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], a página é exibida no navegador host.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a><span data-ttu-id="f2aa7-286">Navegando até uma página</span><span class="sxs-lookup"><span data-stu-id="f2aa7-286">Navigating to a Page</span></span>  
 <span data-ttu-id="f2aa7-287">O exemplo a seguir mostra como navegar até uma página.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-287">The following example shows how to navigate to a page.</span></span>  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 <span data-ttu-id="f2aa7-288">Para obter mais informações sobre as várias maneiras de navegar no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consulte [visão geral de navegação](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f2aa7-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span>  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a><span data-ttu-id="f2aa7-289">Especificando um ícone de janela</span><span class="sxs-lookup"><span data-stu-id="f2aa7-289">Specifying a Window Icon</span></span>  
 <span data-ttu-id="f2aa7-290">O exemplo a seguir mostra como usar um URI para especificar um ícone de janela.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-290">The following example shows how to use a URI to specify a window's icon.</span></span>  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 <span data-ttu-id="f2aa7-291">Para obter mais informações, consulte <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="f2aa7-292">Carregando arquivos de imagem, áudio e vídeo</span><span class="sxs-lookup"><span data-stu-id="f2aa7-292">Loading Image, Audio, and Video Files</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="f2aa7-293"> permite que os aplicativos usar uma ampla variedade de tipos de mídia, que podem ser identificados e carregados com o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-293"> allows applications to use a wide variety of media types, all of which can be identified and loaded with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], as shown in the following examples.</span></span>  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 <span data-ttu-id="f2aa7-294">Para obter mais informações sobre como trabalhar com conteúdo de mídia, consulte [elementos gráficos e multimídia](../../../../docs/framework/wpf/graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2aa7-294">For more information on working with media content, see [Graphics and Multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md).</span></span>  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="f2aa7-295">Carregando um dicionário de recursos a partir do site de origem</span><span class="sxs-lookup"><span data-stu-id="f2aa7-295">Loading a Resource Dictionary from the Site of Origin</span></span>  
 <span data-ttu-id="f2aa7-296">Dicionários de recurso (<xref:System.Windows.ResourceDictionary>) pode ser usado para dar suporte a temas de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="f2aa7-297">Uma maneira de criar e gerenciar temas é criando diferentes temas como dicionários de recursos localizados em um site de origem do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="f2aa7-298">Isso permite que temas sejam adicionados e atualizados sem recompilar e reimplantar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="f2aa7-299">Estes dicionários de recurso podem ser identificados e carregados usando [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], que é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-299">These resource dictionaries can be identified and loaded using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], which is shown in the following example.</span></span>  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 <span data-ttu-id="f2aa7-300">Para obter uma visão geral de temas [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consulte [estilos e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="f2aa7-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2aa7-301">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2aa7-301">See Also</span></span>  
 [<span data-ttu-id="f2aa7-302">Arquivos de recurso, conteúdo e dados de aplicativo do WPF</span><span class="sxs-lookup"><span data-stu-id="f2aa7-302">WPF Application Resource, Content, and Data Files</span></span>](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
