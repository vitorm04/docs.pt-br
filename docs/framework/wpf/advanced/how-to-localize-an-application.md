---
title: 'Como: Localizar um aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: 68bb3b8cd080e5b454776433e65027b7d18e7c3b
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331559"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="3e52e-102">Como: Localizar um aplicativo</span><span class="sxs-lookup"><span data-stu-id="3e52e-102">How to: Localize an Application</span></span>
<span data-ttu-id="3e52e-103">Esse tutorial explica como criar um aplicativo localizado usando a ferramenta LocBaml.</span><span class="sxs-lookup"><span data-stu-id="3e52e-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e52e-104">A ferramenta LocBaml não é um aplicativo pronto para produção.</span><span class="sxs-lookup"><span data-stu-id="3e52e-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="3e52e-105">Ela é apresentada como um exemplo que usa algumas das APIs de localização e ilustra como você pode escrever uma ferramenta de localização.</span><span class="sxs-lookup"><span data-stu-id="3e52e-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>   
## <a name="overview"></a><span data-ttu-id="3e52e-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="3e52e-106">Overview</span></span>  
 <span data-ttu-id="3e52e-107">Esta discussão oferece uma abordagem passo a passo para a localização de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3e52e-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="3e52e-108">Primeiro, você preparará o seu aplicativo para que o texto que será convertido possa ser extraído.</span><span class="sxs-lookup"><span data-stu-id="3e52e-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="3e52e-109">Depois que o texto for traduzido, você o mesclará em uma nova cópia do aplicativo original.</span><span class="sxs-lookup"><span data-stu-id="3e52e-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>   
## <a name="requirements"></a><span data-ttu-id="3e52e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e52e-110">Requirements</span></span>  
 <span data-ttu-id="3e52e-111">Ao longo desta discussão, você usará [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], que é um compilador que é executado na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="3e52e-111">Over the course of this discussion, you will use [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="3e52e-112">Além disso, você será instruído a usar um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="3e52e-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="3e52e-113">Para obter instruções sobre como usar [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] os arquivos do e do Project, consulte [Compilar e implantar](../app-development/building-and-deploying-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="3e52e-113">For instructions on how to use [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] and project files, see [Build and Deploy](../app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="3e52e-114">Todos os exemplos nesta discussão usam en-US (inglês-EUA) como a cultura.</span><span class="sxs-lookup"><span data-stu-id="3e52e-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="3e52e-115">Isso permite que você trabalhe nas etapas dos exemplos sem instalar um idioma diferente.</span><span class="sxs-lookup"><span data-stu-id="3e52e-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a><span data-ttu-id="3e52e-116">Criar um aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="3e52e-116">Create a Sample Application</span></span>  
 <span data-ttu-id="3e52e-117">Nesta etapa, você preparará seu aplicativo para a localização.</span><span class="sxs-lookup"><span data-stu-id="3e52e-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="3e52e-118">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Nos exemplos, é fornecido um exemplo de HelloApp que será usado para os exemplos de código nesta discussão.</span><span class="sxs-lookup"><span data-stu-id="3e52e-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="3e52e-119">Se você quiser usar este exemplo, baixe os [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivos do exemplo da [ferramenta LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="3e52e-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
1. <span data-ttu-id="3e52e-120">Desenvolva seu aplicativo até o ponto em que você deseja iniciar a localização.</span><span class="sxs-lookup"><span data-stu-id="3e52e-120">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="3e52e-121">Especifique a linguagem de desenvolvimento no arquivo de projeto para [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] que gere um assembly principal e um assembly satélite (um arquivo com a extensão. Resources. dll) para conter os recursos de idioma neutro.</span><span class="sxs-lookup"><span data-stu-id="3e52e-121">Specify the development language in the project file so that [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="3e52e-122">O arquivo de projeto no exemplo HelloApp é o HelloApp.csproj.</span><span class="sxs-lookup"><span data-stu-id="3e52e-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="3e52e-123">Nesse arquivo, você encontrará a linguagem de desenvolvimento identificada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3e52e-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="3e52e-124">Adicione UIDs aos seus [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos.</span><span class="sxs-lookup"><span data-stu-id="3e52e-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="3e52e-125">Os Uids são usados para controlar as alterações nos arquivos e para identificar os itens que devem ser traduzidos.</span><span class="sxs-lookup"><span data-stu-id="3e52e-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="3e52e-126">Para adicionar UIDs aos seus arquivos, execute **updateuid** em seu arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="3e52e-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="3e52e-127">**msbuild -t:updateuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="3e52e-127">**msbuild -t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="3e52e-128">Para verificar se você não tem UIDs ausentes ou duplicados, execute **checkuid**:</span><span class="sxs-lookup"><span data-stu-id="3e52e-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="3e52e-129">**MSBuild-t:checkuid HelloApp. csproj**</span><span class="sxs-lookup"><span data-stu-id="3e52e-129">**msbuild -t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="3e52e-130">Depois de executar o **updateuid**, os arquivos devem conter UIDs.</span><span class="sxs-lookup"><span data-stu-id="3e52e-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="3e52e-131">Por exemplo, no arquivo Pane1.xaml do HelloApp, você deve encontrar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3e52e-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="3e52e-132">Criar o assembly satélite de recursos de idioma neutro</span><span class="sxs-lookup"><span data-stu-id="3e52e-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="3e52e-133">Depois que o aplicativo está configurado para gerar um assembly satélite de recursos de idioma neutro, você compila o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3e52e-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="3e52e-134">Isso gera o assembly principal do aplicativo, bem como o assembly satélite de recursos de idioma neutro exigido pela LocBaml para a localização.</span><span class="sxs-lookup"><span data-stu-id="3e52e-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="3e52e-135">Para compilar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="3e52e-135">To build the application:</span></span>  
  
1. <span data-ttu-id="3e52e-136">Compile HelloApp para criar um [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3e52e-136">Compile HelloApp to create a [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:</span></span>  
  
     <span data-ttu-id="3e52e-137">**msbuild helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="3e52e-137">**msbuild helloapp.csproj**</span></span>  
  
2. <span data-ttu-id="3e52e-138">O assembly principal recém-criado do aplicativo, HelloApp.exe, é criado na seguinte pasta:</span><span class="sxs-lookup"><span data-stu-id="3e52e-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. <span data-ttu-id="3e52e-139">O assembly satélite de recursos de idioma neutro recém-criado, HelloApp.resources.dll, é criado na seguinte pasta:</span><span class="sxs-lookup"><span data-stu-id="3e52e-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="3e52e-140">Compilar a ferramenta LocBaml</span><span class="sxs-lookup"><span data-stu-id="3e52e-140">Build the LocBaml Tool</span></span>  
  
1. <span data-ttu-id="3e52e-141">Todos os arquivos necessários para compilar LocBaml estão localizados nos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="3e52e-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="3e52e-142">Baixe os C# arquivos do [exemplo da ferramenta LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="3e52e-142">Download the C# files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
2. <span data-ttu-id="3e52e-143">Na linha de comando, execute o arquivo de projeto (locbaml.csproj) para compilar a ferramenta:</span><span class="sxs-lookup"><span data-stu-id="3e52e-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="3e52e-144">**msbuild locbaml.csproj**</span><span class="sxs-lookup"><span data-stu-id="3e52e-144">**msbuild locbaml.csproj**</span></span>  
  
3. <span data-ttu-id="3e52e-145">Acesse o diretório Bin\Release para encontrar o arquivo executável recém-criado (locbaml.exe).</span><span class="sxs-lookup"><span data-stu-id="3e52e-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="3e52e-146">Exemplo: C:\LocBaml\Bin\Release\locbaml.exe.</span><span class="sxs-lookup"><span data-stu-id="3e52e-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4. <span data-ttu-id="3e52e-147">As opções que você pode especificar ao executar a LocBaml são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="3e52e-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    - <span data-ttu-id="3e52e-148">**Parse** ou **-p:** Analisa BAML, recursos ou [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] arquivos para gerar um arquivo. csv ou. txt.</span><span class="sxs-lookup"><span data-stu-id="3e52e-148">**parse** or **-p:** Parses Baml, resources, or [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] files to generate a .csv or .txt file.</span></span>  
  
    - <span data-ttu-id="3e52e-149">**gerar** ou **-g:** Gera um arquivo binário localizado usando um arquivo traduzido.</span><span class="sxs-lookup"><span data-stu-id="3e52e-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    - <span data-ttu-id="3e52e-150">**out** ou **-o** {fileDirectory] **:** Nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="3e52e-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    - <span data-ttu-id="3e52e-151">**Culture** ou **-cul** {*Culture*] **:** Localidade dos assemblies de saída.</span><span class="sxs-lookup"><span data-stu-id="3e52e-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    - <span data-ttu-id="3e52e-152">**translation** ou **-Trans** {*translation. csv*] **:** Arquivo traduzido ou localizado.</span><span class="sxs-lookup"><span data-stu-id="3e52e-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    - <span data-ttu-id="3e52e-153">**asmpath** ou **-asmpath:** {fileDirectory] **:** Se o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] código contiver controles personalizados, você deverá fornecer o **asmpath** para o assembly de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="3e52e-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    - <span data-ttu-id="3e52e-154">**nologo** Não exibe nenhum logotipo ou informações de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="3e52e-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    - <span data-ttu-id="3e52e-155">**extensa** Exibe informações de modo detalhado.</span><span class="sxs-lookup"><span data-stu-id="3e52e-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e52e-156">Se você precisar de uma lista das opções ao executar a ferramenta, digite **LocBaml. exe** e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="3e52e-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="3e52e-157">Usar LocBaml para analisar um arquivo</span><span class="sxs-lookup"><span data-stu-id="3e52e-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="3e52e-158">Agora que criou a ferramenta LocBaml, você está pronto para usá-la para analisar o HelloApp.resources.dll e extrair o conteúdo de texto que será localizado.</span><span class="sxs-lookup"><span data-stu-id="3e52e-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="3e52e-159">Copie o LocBaml.exe para a pasta bin\debug do aplicativo, em que o assembly principal do aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="3e52e-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="3e52e-160">Para analisar o arquivo do assembly satélite e armazenar o resultado como um arquivo .csv, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3e52e-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="3e52e-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span><span class="sxs-lookup"><span data-stu-id="3e52e-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e52e-162">Se o arquivo de entrada, HelloApp.resources.dll, não estiver no mesmo diretório que o LocBaml.exe mova um dos arquivos para que ambos estejam no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="3e52e-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="3e52e-163">Ao executar a LocBaml para analisar arquivos, a saída consistirá em sete campos delimitados por vírgulas (arquivos .csv) ou tabulações (arquivos .txt).</span><span class="sxs-lookup"><span data-stu-id="3e52e-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="3e52e-164">A seguir está o arquivo .csv analisado do HelloApp.resources.dll:</span><span class="sxs-lookup"><span data-stu-id="3e52e-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="3e52e-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span><span class="sxs-lookup"><span data-stu-id="3e52e-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="3e52e-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span><span class="sxs-lookup"><span data-stu-id="3e52e-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="3e52e-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span><span class="sxs-lookup"><span data-stu-id="3e52e-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="3e52e-168">Os sete campos são:</span><span class="sxs-lookup"><span data-stu-id="3e52e-168">The seven fields are:</span></span>  
  
   1. <span data-ttu-id="3e52e-169">**Nome BAML**.</span><span class="sxs-lookup"><span data-stu-id="3e52e-169">**BAML Name**.</span></span> <span data-ttu-id="3e52e-170">O nome do recurso BAML em relação ao assembly satélite do idioma de origem.</span><span class="sxs-lookup"><span data-stu-id="3e52e-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2. <span data-ttu-id="3e52e-171">**Chave de recurso**.</span><span class="sxs-lookup"><span data-stu-id="3e52e-171">**Resource Key**.</span></span> <span data-ttu-id="3e52e-172">O identificador do recurso localizado.</span><span class="sxs-lookup"><span data-stu-id="3e52e-172">The localized resource identifier.</span></span>  
  
   3. <span data-ttu-id="3e52e-173">**Categoria**.</span><span class="sxs-lookup"><span data-stu-id="3e52e-173">**Category**.</span></span> <span data-ttu-id="3e52e-174">O tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="3e52e-174">The value type.</span></span> <span data-ttu-id="3e52e-175">Consulte [atributos e comentários de localização](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="3e52e-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   4. <span data-ttu-id="3e52e-176">**Legibilidade**.</span><span class="sxs-lookup"><span data-stu-id="3e52e-176">**Readability**.</span></span> <span data-ttu-id="3e52e-177">Se o valor pode ser lido por um localizador.</span><span class="sxs-lookup"><span data-stu-id="3e52e-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="3e52e-178">Consulte [atributos e comentários de localização](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="3e52e-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   5. <span data-ttu-id="3e52e-179">**Modificabilidade**.</span><span class="sxs-lookup"><span data-stu-id="3e52e-179">**Modifiability**.</span></span> <span data-ttu-id="3e52e-180">Se o valor pode ser modificado por um localizador.</span><span class="sxs-lookup"><span data-stu-id="3e52e-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="3e52e-181">Consulte [atributos e comentários de localização](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="3e52e-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   6. <span data-ttu-id="3e52e-182">**Comentários**.</span><span class="sxs-lookup"><span data-stu-id="3e52e-182">**Comments**.</span></span> <span data-ttu-id="3e52e-183">Descrição adicional do valor para ajudar a determinar como um valor é localizado.</span><span class="sxs-lookup"><span data-stu-id="3e52e-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="3e52e-184">Consulte [atributos e comentários de localização](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="3e52e-184">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   7. <span data-ttu-id="3e52e-185">**Valor**.</span><span class="sxs-lookup"><span data-stu-id="3e52e-185">**Value**.</span></span> <span data-ttu-id="3e52e-186">O valor de texto a traduzir para a cultura desejada.</span><span class="sxs-lookup"><span data-stu-id="3e52e-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="3e52e-187">A tabela a seguir mostra como esses campos são mapeados para os valores delimitados do arquivo .csv:</span><span class="sxs-lookup"><span data-stu-id="3e52e-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="3e52e-188">Nome BAML</span><span class="sxs-lookup"><span data-stu-id="3e52e-188">BAML name</span></span>|<span data-ttu-id="3e52e-189">Chave de recurso</span><span class="sxs-lookup"><span data-stu-id="3e52e-189">Resource key</span></span>|<span data-ttu-id="3e52e-190">Categoria</span><span class="sxs-lookup"><span data-stu-id="3e52e-190">Category</span></span>|<span data-ttu-id="3e52e-191">Legibilidade</span><span class="sxs-lookup"><span data-stu-id="3e52e-191">Readability</span></span>|<span data-ttu-id="3e52e-192">Modificabilidade</span><span class="sxs-lookup"><span data-stu-id="3e52e-192">Modifiability</span></span>|<span data-ttu-id="3e52e-193">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e52e-193">Comments</span></span>|<span data-ttu-id="3e52e-194">Valor</span><span class="sxs-lookup"><span data-stu-id="3e52e-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="3e52e-195">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="3e52e-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="3e52e-196">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="3e52e-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="3e52e-197">Ignorar</span><span class="sxs-lookup"><span data-stu-id="3e52e-197">Ignore</span></span>|<span data-ttu-id="3e52e-198">FALSE</span><span class="sxs-lookup"><span data-stu-id="3e52e-198">FALSE</span></span>|<span data-ttu-id="3e52e-199">FALSE</span><span class="sxs-lookup"><span data-stu-id="3e52e-199">FALSE</span></span>||<span data-ttu-id="3e52e-200">#Text1;#Text2</span><span class="sxs-lookup"><span data-stu-id="3e52e-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="3e52e-201">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="3e52e-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="3e52e-202">Text1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="3e52e-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="3e52e-203">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3e52e-203">None</span></span>|<span data-ttu-id="3e52e-204">TRUE</span><span class="sxs-lookup"><span data-stu-id="3e52e-204">TRUE</span></span>|<span data-ttu-id="3e52e-205">TRUE</span><span class="sxs-lookup"><span data-stu-id="3e52e-205">TRUE</span></span>||<span data-ttu-id="3e52e-206">Hello World</span><span class="sxs-lookup"><span data-stu-id="3e52e-206">Hello World</span></span>|
   |<span data-ttu-id="3e52e-207">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="3e52e-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="3e52e-208">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="3e52e-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="3e52e-209">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3e52e-209">None</span></span>|<span data-ttu-id="3e52e-210">TRUE</span><span class="sxs-lookup"><span data-stu-id="3e52e-210">TRUE</span></span>|<span data-ttu-id="3e52e-211">TRUE</span><span class="sxs-lookup"><span data-stu-id="3e52e-211">TRUE</span></span>||<span data-ttu-id="3e52e-212">Goodbye World</span><span class="sxs-lookup"><span data-stu-id="3e52e-212">Goodbye World</span></span>|
  
   <span data-ttu-id="3e52e-213">Observe que todos os valores do campo **comentários** não contêm valores; se um campo não tiver um valor, ele estará vazio.</span><span class="sxs-lookup"><span data-stu-id="3e52e-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="3e52e-214">Observe também que o item na primeira linha não é legível nem modificável e tem "ignorar" como seu valor de **categoria** , que indica que o valor não é localizável.</span><span class="sxs-lookup"><span data-stu-id="3e52e-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="3e52e-215">Para facilitar a descoberta de itens localizáveis em arquivos analisados, especialmente em arquivos grandes, você pode classificar ou filtrar os itens por **categoria**, **legibilidade**e **modificação**.</span><span class="sxs-lookup"><span data-stu-id="3e52e-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="3e52e-216">Por exemplo, você pode filtrar valores e ilegíveis e não modificáveis.</span><span class="sxs-lookup"><span data-stu-id="3e52e-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a><span data-ttu-id="3e52e-217">Traduzir o conteúdo localizável</span><span class="sxs-lookup"><span data-stu-id="3e52e-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="3e52e-218">Use qualquer ferramenta que você tiver disponível para traduzir o conteúdo extraído.</span><span class="sxs-lookup"><span data-stu-id="3e52e-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="3e52e-219">Uma boa maneira de fazer isso é gravar os recursos em um arquivo. csv e exibi-los no [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], fazendo alterações de tradução na última coluna (valor).</span><span class="sxs-lookup"><span data-stu-id="3e52e-219">A good way to do this is to write the resources to a .csv file and view them in [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="3e52e-220">Usar a LocBaml para gerar um novo arquivo .resources.dll</span><span class="sxs-lookup"><span data-stu-id="3e52e-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="3e52e-221">O conteúdo que foi identificado ao analisar o HelloApp.resources.dll com a LocBaml foi traduzido e deve ser mesclado de volta no aplicativo original.</span><span class="sxs-lookup"><span data-stu-id="3e52e-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="3e52e-222">Use a opção **Generate** ou **-g** para gerar um novo arquivo. Resources. dll.</span><span class="sxs-lookup"><span data-stu-id="3e52e-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="3e52e-223">Use a seguinte sintaxe para gerar um novo arquivo HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="3e52e-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="3e52e-224">Marque a cultura como en-US (/cul:en-US).</span><span class="sxs-lookup"><span data-stu-id="3e52e-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="3e52e-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span><span class="sxs-lookup"><span data-stu-id="3e52e-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e52e-226">Se o arquivo de entrada, Hello.csv, não estiver no mesmo diretório que o executável, LocBaml.exe, mova um dos arquivos para que ambos estejam no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="3e52e-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="3e52e-227">Substitua o arquivo HelloApp.resources.dll no diretório C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll antigo pelo arquivo HelloApp.resources.dll recém-criado.</span><span class="sxs-lookup"><span data-stu-id="3e52e-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3. <span data-ttu-id="3e52e-228">"Hello World" e "Goodbye World" agora devem estar traduzidos em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3e52e-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="3e52e-229">Para traduzir para uma cultura diferente, use a cultura do idioma para o qual você está traduzindo.</span><span class="sxs-lookup"><span data-stu-id="3e52e-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="3e52e-230">O exemplo a seguir mostra como traduzir para francês canadense:</span><span class="sxs-lookup"><span data-stu-id="3e52e-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="3e52e-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span><span class="sxs-lookup"><span data-stu-id="3e52e-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5. <span data-ttu-id="3e52e-232">No mesmo assembly que o assembly principal do aplicativo, crie uma nova pasta específica de cultura para abrigar o novo assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="3e52e-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="3e52e-233">Para francês canadense, a pasta seria fr-CA.</span><span class="sxs-lookup"><span data-stu-id="3e52e-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="3e52e-234">Copie o assembly satélite gerado para a nova pasta.</span><span class="sxs-lookup"><span data-stu-id="3e52e-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="3e52e-235">Para testar o novo assembly satélite, você precisa alterar a cultura na qual o aplicativo será executado.</span><span class="sxs-lookup"><span data-stu-id="3e52e-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="3e52e-236">Você pode fazer isso de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="3e52e-236">You can do this in one of two ways:</span></span>  
  
    - <span data-ttu-id="3e52e-237">Altere as configurações regionais do seu sistema operacional (**inicie** &#124; **as opções regionais e de idioma**do painel &#124; de **controle** ).</span><span class="sxs-lookup"><span data-stu-id="3e52e-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    - <span data-ttu-id="3e52e-238">Em seu aplicativo, adicione o seguinte código em App.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="3e52e-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="3e52e-239">Algumas dicas para usar a LocBaml</span><span class="sxs-lookup"><span data-stu-id="3e52e-239">Some Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="3e52e-240">Todos os assemblies dependentes que definem controles personalizados devem ser copiados para o diretório local da LocBaml ou instalados no GAC.</span><span class="sxs-lookup"><span data-stu-id="3e52e-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="3e52e-241">Isso é necessário porque a API de localização deve ter acesso aos assemblies dependentes quando ele lê o XAML binário (BAML).</span><span class="sxs-lookup"><span data-stu-id="3e52e-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="3e52e-242">Se o assembly principal é assinado, a DLL de recurso gerado também deve ser assinada para que seja carregada.</span><span class="sxs-lookup"><span data-stu-id="3e52e-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="3e52e-243">A versão da DLL de recurso localizado precisa ser sincronizada com o assembly principal.</span><span class="sxs-lookup"><span data-stu-id="3e52e-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a><span data-ttu-id="3e52e-244">Novidades</span><span class="sxs-lookup"><span data-stu-id="3e52e-244">What's Next</span></span>  
 <span data-ttu-id="3e52e-245">Agora você deve ter um entendimento básico de como usar a ferramenta LocBaml.</span><span class="sxs-lookup"><span data-stu-id="3e52e-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="3e52e-246">Você deve ser capaz de criar um arquivo que contém Uids.</span><span class="sxs-lookup"><span data-stu-id="3e52e-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="3e52e-247">Ao usar a ferramenta LocBaml, você deverá ser capaz de analisar um arquivo para extrair o conteúdo localizável e, depois que o conteúdo for traduzido, você deverá ser capaz de gerar um arquivo .resources.dll que mescla o conteúdo traduzido.</span><span class="sxs-lookup"><span data-stu-id="3e52e-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="3e52e-248">Este tópico não inclui todos os detalhes possíveis, mas agora você tem o conhecimento necessário para usar a LocBaml na localização de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3e52e-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e52e-249">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e52e-249">See also</span></span>

- [<span data-ttu-id="3e52e-250">Globalização para WPF</span><span class="sxs-lookup"><span data-stu-id="3e52e-250">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="3e52e-251">Visão geral do uso de layout automático</span><span class="sxs-lookup"><span data-stu-id="3e52e-251">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
