---
title: Como localizar um aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: f2e7e5e8879e89806cfd457a1af80f51b91871cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174206"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="b6722-102">Como localizar um aplicativo</span><span class="sxs-lookup"><span data-stu-id="b6722-102">How to: Localize an Application</span></span>
<span data-ttu-id="b6722-103">Esse tutorial explica como criar um aplicativo localizado usando a ferramenta LocBaml.</span><span class="sxs-lookup"><span data-stu-id="b6722-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6722-104">A ferramenta LocBaml não é um aplicativo pronto para produção.</span><span class="sxs-lookup"><span data-stu-id="b6722-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="b6722-105">Ela é apresentada como um exemplo que usa algumas das APIs de localização e ilustra como você pode escrever uma ferramenta de localização.</span><span class="sxs-lookup"><span data-stu-id="b6722-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>
## <a name="overview"></a><span data-ttu-id="b6722-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="b6722-106">Overview</span></span>  
 <span data-ttu-id="b6722-107">Esta discussão oferece uma abordagem passo a passo para a localização de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6722-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="b6722-108">Primeiro, você preparará o seu aplicativo para que o texto que será convertido possa ser extraído.</span><span class="sxs-lookup"><span data-stu-id="b6722-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="b6722-109">Depois que o texto for traduzido, você o mesclará em uma nova cópia do aplicativo original.</span><span class="sxs-lookup"><span data-stu-id="b6722-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>
## <a name="requirements"></a><span data-ttu-id="b6722-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6722-110">Requirements</span></span>  
 <span data-ttu-id="b6722-111">Ao longo desta discussão, você usará o Microsoft build engine (MSBuild), que é um compilador que funciona a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b6722-111">Over the course of this discussion, you will use Microsoft build engine (MSBuild), which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="b6722-112">Além disso, você será instruído a usar um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="b6722-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="b6722-113">Para obter instruções sobre como usar arquivos msbuild e projeto, consulte [Build and Deploy](../app-development/building-and-deploying-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="b6722-113">For instructions on how to use MSBuild and project files, see [Build and Deploy](../app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="b6722-114">Todos os exemplos nesta discussão usam en-US (inglês-EUA) como a cultura.</span><span class="sxs-lookup"><span data-stu-id="b6722-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="b6722-115">Isso permite que você trabalhe nas etapas dos exemplos sem instalar um idioma diferente.</span><span class="sxs-lookup"><span data-stu-id="b6722-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>
## <a name="create-a-sample-application"></a><span data-ttu-id="b6722-116">Criar um aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="b6722-116">Create a Sample Application</span></span>  
 <span data-ttu-id="b6722-117">Nesta etapa, você preparará seu aplicativo para a localização.</span><span class="sxs-lookup"><span data-stu-id="b6722-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="b6722-118">Nas [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] amostras, é fornecida uma amostra de HelloApp que será usada para os exemplos de código nesta discussão.</span><span class="sxs-lookup"><span data-stu-id="b6722-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="b6722-119">Se você quiser usar esta amostra, baixe os [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivos da Amostra de Ferramenta [LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span><span class="sxs-lookup"><span data-stu-id="b6722-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
1. <span data-ttu-id="b6722-120">Desenvolva seu aplicativo até o ponto em que você deseja iniciar a localização.</span><span class="sxs-lookup"><span data-stu-id="b6722-120">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="b6722-121">Especifique a linguagem de desenvolvimento no arquivo do projeto para que o MSBuild gere uma montagem principal e um conjunto por satélite (um arquivo com a extensão .resources.dll) para conter os recursos de linguagem neutra.</span><span class="sxs-lookup"><span data-stu-id="b6722-121">Specify the development language in the project file so that MSBuild generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="b6722-122">O arquivo de projeto no exemplo HelloApp é o HelloApp.csproj.</span><span class="sxs-lookup"><span data-stu-id="b6722-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="b6722-123">Nesse arquivo, você encontrará a linguagem de desenvolvimento identificada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b6722-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="b6722-124">Adicione Uids [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aos seus arquivos.</span><span class="sxs-lookup"><span data-stu-id="b6722-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="b6722-125">Os Uids são usados para controlar as alterações nos arquivos e para identificar os itens que devem ser traduzidos.</span><span class="sxs-lookup"><span data-stu-id="b6722-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="b6722-126">Para adicionar Uids aos seus arquivos, execute **updateuid** no arquivo do projeto:</span><span class="sxs-lookup"><span data-stu-id="b6722-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="b6722-127">**msbuild -t:updateuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="b6722-127">**msbuild -t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="b6722-128">Para verificar se você não tem Uids faltando ou duplicado, execute **checkuid**:</span><span class="sxs-lookup"><span data-stu-id="b6722-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="b6722-129">**msbuild -t:checkuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="b6722-129">**msbuild -t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="b6722-130">Depois de executar **updateuid,** seus arquivos devem conter Uids.</span><span class="sxs-lookup"><span data-stu-id="b6722-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="b6722-131">Por exemplo, no arquivo Pane1.xaml do HelloApp, você deve encontrar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b6722-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="b6722-132">Criar o assembly satélite de recursos de idioma neutro</span><span class="sxs-lookup"><span data-stu-id="b6722-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="b6722-133">Depois que o aplicativo está configurado para gerar um assembly satélite de recursos de idioma neutro, você compila o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6722-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="b6722-134">Isso gera o assembly principal do aplicativo, bem como o assembly satélite de recursos de idioma neutro exigido pela LocBaml para a localização.</span><span class="sxs-lookup"><span data-stu-id="b6722-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="b6722-135">Para criar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="b6722-135">To build the application:</span></span>  
  
1. <span data-ttu-id="b6722-136">Compile o HelloApp para criar uma biblioteca de links dinâmicos (DLL):</span><span class="sxs-lookup"><span data-stu-id="b6722-136">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
     <span data-ttu-id="b6722-137">**msbuild helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="b6722-137">**msbuild helloapp.csproj**</span></span>  
  
2. <span data-ttu-id="b6722-138">O assembly principal recém-criado do aplicativo, HelloApp.exe, é criado na seguinte pasta:</span><span class="sxs-lookup"><span data-stu-id="b6722-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. <span data-ttu-id="b6722-139">O assembly satélite de recursos de idioma neutro recém-criado, HelloApp.resources.dll, é criado na seguinte pasta:</span><span class="sxs-lookup"><span data-stu-id="b6722-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="b6722-140">Compilar a ferramenta LocBaml</span><span class="sxs-lookup"><span data-stu-id="b6722-140">Build the LocBaml Tool</span></span>  
  
1. <span data-ttu-id="b6722-141">Todos os arquivos necessários para construir LocBaml estão localizados nas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="b6722-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="b6722-142">Baixe os arquivos C# da amostra de [ferramentas locBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span><span class="sxs-lookup"><span data-stu-id="b6722-142">Download the C# files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
2. <span data-ttu-id="b6722-143">Na linha de comando, execute o arquivo de projeto (locbaml.csproj) para compilar a ferramenta:</span><span class="sxs-lookup"><span data-stu-id="b6722-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="b6722-144">**msbuild locbaml.csproj**</span><span class="sxs-lookup"><span data-stu-id="b6722-144">**msbuild locbaml.csproj**</span></span>  
  
3. <span data-ttu-id="b6722-145">Acesse o diretório Bin\Release para encontrar o arquivo executável recém-criado (locbaml.exe).</span><span class="sxs-lookup"><span data-stu-id="b6722-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="b6722-146">Exemplo: C:\LocBaml\Bin\Release\locbaml.exe.</span><span class="sxs-lookup"><span data-stu-id="b6722-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4. <span data-ttu-id="b6722-147">As opções que você pode especificar ao executar a LocBaml são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="b6722-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    - <span data-ttu-id="b6722-148">**analisar** ou **-p:** Analisa arquivos Baml, resources ou DLL para gerar um arquivo .csv ou .txt.</span><span class="sxs-lookup"><span data-stu-id="b6722-148">**parse** or **-p:** Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span>  
  
    - <span data-ttu-id="b6722-149">**gerar** ou **-g:** Gera um arquivo binário localizado usando um arquivo traduzido.</span><span class="sxs-lookup"><span data-stu-id="b6722-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    - <span data-ttu-id="b6722-150">**fora** ou **-o** {*diretório de arquivos*] : **Nome** do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="b6722-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    - <span data-ttu-id="b6722-151">**cultura** ou **-cul** {*cultura*] **:** Locale de conjuntos de saída.</span><span class="sxs-lookup"><span data-stu-id="b6722-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    - <span data-ttu-id="b6722-152">**tradução** ou **-trans** {*translation.csv*] **:** Arquivo traduzido ou localizado.</span><span class="sxs-lookup"><span data-stu-id="b6722-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    - <span data-ttu-id="b6722-153">**asmpath** ou **-asmpath:** {*filedirectory*] **:** Se o seu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] código contiver controles personalizados, você deve fornecer o **asmpath** para o conjunto de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="b6722-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    - <span data-ttu-id="b6722-154">**nologo:** não exibe nenhuma informação de logotipo ou direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="b6722-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    - <span data-ttu-id="b6722-155">**verbose:** exibe informações de modo detalhado.</span><span class="sxs-lookup"><span data-stu-id="b6722-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b6722-156">Se você precisar de uma lista das opções quando estiver executando a ferramenta, **digite LocBaml.exe** e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="b6722-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="b6722-157">Usar LocBaml para analisar um arquivo</span><span class="sxs-lookup"><span data-stu-id="b6722-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="b6722-158">Agora que criou a ferramenta LocBaml, você está pronto para usá-la para analisar o HelloApp.resources.dll e extrair o conteúdo de texto que será localizado.</span><span class="sxs-lookup"><span data-stu-id="b6722-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="b6722-159">Copie o LocBaml.exe para a pasta bin\debug do aplicativo, em que o assembly principal do aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="b6722-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="b6722-160">Para analisar o arquivo do assembly satélite e armazenar o resultado como um arquivo .csv, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b6722-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="b6722-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span><span class="sxs-lookup"><span data-stu-id="b6722-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b6722-162">Se o arquivo de entrada, HelloApp.resources.dll, não estiver no mesmo diretório que o LocBaml.exe mova um dos arquivos para que ambos estejam no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="b6722-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="b6722-163">Ao executar a LocBaml para analisar arquivos, a saída consistirá em sete campos delimitados por vírgulas (arquivos .csv) ou tabulações (arquivos .txt).</span><span class="sxs-lookup"><span data-stu-id="b6722-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="b6722-164">A seguir está o arquivo .csv analisado do HelloApp.resources.dll:</span><span class="sxs-lookup"><span data-stu-id="b6722-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="b6722-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span><span class="sxs-lookup"><span data-stu-id="b6722-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="b6722-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span><span class="sxs-lookup"><span data-stu-id="b6722-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="b6722-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span><span class="sxs-lookup"><span data-stu-id="b6722-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="b6722-168">Os sete campos são:</span><span class="sxs-lookup"><span data-stu-id="b6722-168">The seven fields are:</span></span>  
  
   1. <span data-ttu-id="b6722-169">**Nome BAML**.</span><span class="sxs-lookup"><span data-stu-id="b6722-169">**BAML Name**.</span></span> <span data-ttu-id="b6722-170">O nome do recurso BAML em relação ao assembly satélite do idioma de origem.</span><span class="sxs-lookup"><span data-stu-id="b6722-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2. <span data-ttu-id="b6722-171">**Chave de recursos**.</span><span class="sxs-lookup"><span data-stu-id="b6722-171">**Resource Key**.</span></span> <span data-ttu-id="b6722-172">O identificador do recurso localizado.</span><span class="sxs-lookup"><span data-stu-id="b6722-172">The localized resource identifier.</span></span>  
  
   3. <span data-ttu-id="b6722-173">**Categoria**.</span><span class="sxs-lookup"><span data-stu-id="b6722-173">**Category**.</span></span> <span data-ttu-id="b6722-174">O tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="b6722-174">The value type.</span></span> <span data-ttu-id="b6722-175">Veja [Atributos e Comentários de Localização](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="b6722-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   4. <span data-ttu-id="b6722-176">**Legibilidade**.</span><span class="sxs-lookup"><span data-stu-id="b6722-176">**Readability**.</span></span> <span data-ttu-id="b6722-177">Se o valor pode ser lido por um localizador.</span><span class="sxs-lookup"><span data-stu-id="b6722-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="b6722-178">Veja [Atributos e Comentários de Localização](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="b6722-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   5. <span data-ttu-id="b6722-179">**Modificabilidade**.</span><span class="sxs-lookup"><span data-stu-id="b6722-179">**Modifiability**.</span></span> <span data-ttu-id="b6722-180">Se o valor pode ser modificado por um localizador.</span><span class="sxs-lookup"><span data-stu-id="b6722-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="b6722-181">Veja [Atributos e Comentários de Localização](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="b6722-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   6. <span data-ttu-id="b6722-182">**Comentários**.</span><span class="sxs-lookup"><span data-stu-id="b6722-182">**Comments**.</span></span> <span data-ttu-id="b6722-183">Descrição adicional do valor para ajudar a determinar como um valor é localizado.</span><span class="sxs-lookup"><span data-stu-id="b6722-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="b6722-184">Veja [Atributos e Comentários de Localização](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="b6722-184">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   7. <span data-ttu-id="b6722-185">**Valor**.</span><span class="sxs-lookup"><span data-stu-id="b6722-185">**Value**.</span></span> <span data-ttu-id="b6722-186">O valor de texto a traduzir para a cultura desejada.</span><span class="sxs-lookup"><span data-stu-id="b6722-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="b6722-187">A tabela a seguir mostra como esses campos são mapeados para os valores delimitados do arquivo .csv:</span><span class="sxs-lookup"><span data-stu-id="b6722-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="b6722-188">Nome BAML</span><span class="sxs-lookup"><span data-stu-id="b6722-188">BAML name</span></span>|<span data-ttu-id="b6722-189">Chave de recurso</span><span class="sxs-lookup"><span data-stu-id="b6722-189">Resource key</span></span>|<span data-ttu-id="b6722-190">Categoria</span><span class="sxs-lookup"><span data-stu-id="b6722-190">Category</span></span>|<span data-ttu-id="b6722-191">Legibilidade</span><span class="sxs-lookup"><span data-stu-id="b6722-191">Readability</span></span>|<span data-ttu-id="b6722-192">Modificabilidade</span><span class="sxs-lookup"><span data-stu-id="b6722-192">Modifiability</span></span>|<span data-ttu-id="b6722-193">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6722-193">Comments</span></span>|<span data-ttu-id="b6722-194">Valor</span><span class="sxs-lookup"><span data-stu-id="b6722-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="b6722-195">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="b6722-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="b6722-196">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="b6722-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="b6722-197">Ignorar</span><span class="sxs-lookup"><span data-stu-id="b6722-197">Ignore</span></span>|<span data-ttu-id="b6722-198">FALSE</span><span class="sxs-lookup"><span data-stu-id="b6722-198">FALSE</span></span>|<span data-ttu-id="b6722-199">FALSE</span><span class="sxs-lookup"><span data-stu-id="b6722-199">FALSE</span></span>||<span data-ttu-id="b6722-200">#Text1;#Text2</span><span class="sxs-lookup"><span data-stu-id="b6722-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="b6722-201">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="b6722-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="b6722-202">Text1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="b6722-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="b6722-203">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b6722-203">None</span></span>|<span data-ttu-id="b6722-204">TRUE</span><span class="sxs-lookup"><span data-stu-id="b6722-204">TRUE</span></span>|<span data-ttu-id="b6722-205">TRUE</span><span class="sxs-lookup"><span data-stu-id="b6722-205">TRUE</span></span>||<span data-ttu-id="b6722-206">Olá, Mundo</span><span class="sxs-lookup"><span data-stu-id="b6722-206">Hello World</span></span>|
   |<span data-ttu-id="b6722-207">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="b6722-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="b6722-208">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="b6722-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="b6722-209">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b6722-209">None</span></span>|<span data-ttu-id="b6722-210">TRUE</span><span class="sxs-lookup"><span data-stu-id="b6722-210">TRUE</span></span>|<span data-ttu-id="b6722-211">TRUE</span><span class="sxs-lookup"><span data-stu-id="b6722-211">TRUE</span></span>||<span data-ttu-id="b6722-212">Goodbye World</span><span class="sxs-lookup"><span data-stu-id="b6722-212">Goodbye World</span></span>|
  
   <span data-ttu-id="b6722-213">Observe que todos os valores para o campo **Comentários** não contêm valores; se um campo não tem um valor, ele está vazio.</span><span class="sxs-lookup"><span data-stu-id="b6722-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="b6722-214">Observe também que o item na primeira linha não é legível nem modificável, e tem "Ignorar" como seu valor de **categoria,** tudo indica que o valor não é localizado.</span><span class="sxs-lookup"><span data-stu-id="b6722-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="b6722-215">Para facilitar a descoberta de itens localizados em arquivos analisados, particularmente em arquivos grandes, você pode classificar ou filtrar os itens por **categoria,** **leitura**e **modificabilidade.**</span><span class="sxs-lookup"><span data-stu-id="b6722-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="b6722-216">Por exemplo, você pode filtrar valores e ilegíveis e não modificáveis.</span><span class="sxs-lookup"><span data-stu-id="b6722-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>
## <a name="translate-the-localizable-content"></a><span data-ttu-id="b6722-217">Traduzir o conteúdo localizável</span><span class="sxs-lookup"><span data-stu-id="b6722-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="b6722-218">Use qualquer ferramenta que você tiver disponível para traduzir o conteúdo extraído.</span><span class="sxs-lookup"><span data-stu-id="b6722-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="b6722-219">Uma boa maneira de fazer isso é escrever os recursos em um arquivo .csv e visualizá-los no Microsoft Excel, fazendo alterações de tradução na última coluna (valor).</span><span class="sxs-lookup"><span data-stu-id="b6722-219">A good way to do this is to write the resources to a .csv file and view them in Microsoft Excel, making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="b6722-220">Usar a LocBaml para gerar um novo arquivo .resources.dll</span><span class="sxs-lookup"><span data-stu-id="b6722-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="b6722-221">O conteúdo que foi identificado ao analisar o HelloApp.resources.dll com a LocBaml foi traduzido e deve ser mesclado de volta no aplicativo original.</span><span class="sxs-lookup"><span data-stu-id="b6722-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="b6722-222">Use a opção **gerar** ou **-g** para gerar um novo arquivo .resources.dll.</span><span class="sxs-lookup"><span data-stu-id="b6722-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="b6722-223">Use a seguinte sintaxe para gerar um novo arquivo HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="b6722-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="b6722-224">Marque a cultura como en-US (/cul:en-US).</span><span class="sxs-lookup"><span data-stu-id="b6722-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="b6722-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span><span class="sxs-lookup"><span data-stu-id="b6722-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b6722-226">Se o arquivo de entrada, Hello.csv, não estiver no mesmo diretório que o executável, LocBaml.exe, mova um dos arquivos para que ambos estejam no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="b6722-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="b6722-227">Substitua o arquivo HelloApp.resources.dll no diretório C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll antigo pelo arquivo HelloApp.resources.dll recém-criado.</span><span class="sxs-lookup"><span data-stu-id="b6722-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3. <span data-ttu-id="b6722-228">"Hello World" e "Goodbye World" agora devem estar traduzidos em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6722-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="b6722-229">Para traduzir para uma cultura diferente, use a cultura do idioma para o qual você está traduzindo.</span><span class="sxs-lookup"><span data-stu-id="b6722-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="b6722-230">O exemplo a seguir mostra como traduzir para francês canadense:</span><span class="sxs-lookup"><span data-stu-id="b6722-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="b6722-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span><span class="sxs-lookup"><span data-stu-id="b6722-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5. <span data-ttu-id="b6722-232">No mesmo assembly que o assembly principal do aplicativo, crie uma nova pasta específica de cultura para abrigar o novo assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="b6722-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="b6722-233">Para francês canadense, a pasta seria fr-CA.</span><span class="sxs-lookup"><span data-stu-id="b6722-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="b6722-234">Copie o assembly satélite gerado para a nova pasta.</span><span class="sxs-lookup"><span data-stu-id="b6722-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="b6722-235">Para testar o novo assembly satélite, você precisa alterar a cultura na qual o aplicativo será executado.</span><span class="sxs-lookup"><span data-stu-id="b6722-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="b6722-236">É possível fazer isso de duas formas:</span><span class="sxs-lookup"><span data-stu-id="b6722-236">You can do this in one of two ways:</span></span>  
  
    - <span data-ttu-id="b6722-237">Altere as configurações regionais do sistema operacional **(Inicie** &#124; **Painel de Controle** &#124; **Opções Regionais e de Idiomas**).</span><span class="sxs-lookup"><span data-stu-id="b6722-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    - <span data-ttu-id="b6722-238">Em seu aplicativo, adicione o seguinte código em App.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="b6722-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="b6722-239">Algumas dicas para usar a LocBaml</span><span class="sxs-lookup"><span data-stu-id="b6722-239">Some Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="b6722-240">Todos os assemblies dependentes que definem controles personalizados devem ser copiados para o diretório local da LocBaml ou instalados no GAC.</span><span class="sxs-lookup"><span data-stu-id="b6722-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="b6722-241">Isso é necessário porque a API de localização deve ter acesso aos conjuntos dependentes quando lê o Binário XAML (BAML).</span><span class="sxs-lookup"><span data-stu-id="b6722-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="b6722-242">Se o assembly principal é assinado, a DLL de recurso gerado também deve ser assinada para que seja carregada.</span><span class="sxs-lookup"><span data-stu-id="b6722-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="b6722-243">A versão da DLL de recurso localizado precisa ser sincronizada com o assembly principal.</span><span class="sxs-lookup"><span data-stu-id="b6722-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>
## <a name="whats-next"></a><span data-ttu-id="b6722-244">E agora?</span><span class="sxs-lookup"><span data-stu-id="b6722-244">What's Next</span></span>  
 <span data-ttu-id="b6722-245">Agora você deve ter um entendimento básico de como usar a ferramenta LocBaml.</span><span class="sxs-lookup"><span data-stu-id="b6722-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="b6722-246">Você deve ser capaz de criar um arquivo que contém Uids.</span><span class="sxs-lookup"><span data-stu-id="b6722-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="b6722-247">Ao usar a ferramenta LocBaml, você deverá ser capaz de analisar um arquivo para extrair o conteúdo localizável e, depois que o conteúdo for traduzido, você deverá ser capaz de gerar um arquivo .resources.dll que mescla o conteúdo traduzido.</span><span class="sxs-lookup"><span data-stu-id="b6722-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="b6722-248">Este tópico não inclui todos os detalhes possíveis, mas agora você tem o conhecimento necessário para usar a LocBaml na localização de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b6722-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6722-249">Confira também</span><span class="sxs-lookup"><span data-stu-id="b6722-249">See also</span></span>

- [<span data-ttu-id="b6722-250">Globalização para WPF</span><span class="sxs-lookup"><span data-stu-id="b6722-250">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="b6722-251">Visão geral do uso de layout automático</span><span class="sxs-lookup"><span data-stu-id="b6722-251">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
