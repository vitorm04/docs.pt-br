---
title: Localizar um aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: dc7d8f4f56b26fffbd883e1e1d6e420026e1f94f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209676"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="07534-102">Como localizar um aplicativo</span><span class="sxs-lookup"><span data-stu-id="07534-102">How to: Localize an application</span></span>

<span data-ttu-id="07534-103">Esse tutorial explica como criar um aplicativo localizado usando a ferramenta LocBaml.</span><span class="sxs-lookup"><span data-stu-id="07534-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07534-104">A ferramenta LocBaml não é um aplicativo pronto para produção.</span><span class="sxs-lookup"><span data-stu-id="07534-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="07534-105">Ela é apresentada como um exemplo que usa algumas das APIs de localização e ilustra como você pode escrever uma ferramenta de localização.</span><span class="sxs-lookup"><span data-stu-id="07534-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="07534-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="07534-106">Overview</span></span>

<span data-ttu-id="07534-107">Este artigo fornece uma abordagem passo a passo para a localização de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07534-107">This article gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="07534-108">Primeiro, você prepara seu aplicativo para que o texto que será traduzido possa ser extraído.</span><span class="sxs-lookup"><span data-stu-id="07534-108">First, you prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="07534-109">Depois que o texto é traduzido, você mescla o texto traduzido em uma nova cópia do aplicativo original.</span><span class="sxs-lookup"><span data-stu-id="07534-109">After the text is translated, you merge the translated text into a new copy of the original application.</span></span>
  
## <a name="create-a-sample-application"></a><span data-ttu-id="07534-110">Criar um aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="07534-110">Create a sample application</span></span>

<span data-ttu-id="07534-111">Nesta etapa, você prepara seu aplicativo para localização.</span><span class="sxs-lookup"><span data-stu-id="07534-111">In this step, you prepare your app for localization.</span></span> <span data-ttu-id="07534-112">Nos exemplos de Windows Presentation Foundation (WPF), é fornecido um exemplo de HelloApp que será usado para os exemplos de código nesta discussão.</span><span class="sxs-lookup"><span data-stu-id="07534-112">In the Windows Presentation Foundation (WPF) samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="07534-113">Se você quiser usar este exemplo, baixe os arquivos de Extensible Application Markup Language (XAML) do exemplo da [ferramenta LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span><span class="sxs-lookup"><span data-stu-id="07534-113">If you would like to use this sample, download the Extensible Application Markup Language (XAML) files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
1. <span data-ttu-id="07534-114">Desenvolva seu aplicativo até o ponto em que você deseja iniciar a localização.</span><span class="sxs-lookup"><span data-stu-id="07534-114">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="07534-115">Especifique a linguagem de desenvolvimento no arquivo de projeto para que o MSBuild gere um assembly principal e um assembly satélite (um arquivo com a extensão. Resources. dll) para conter os recursos de idioma neutro.</span><span class="sxs-lookup"><span data-stu-id="07534-115">Specify the development language in the project file so that MSBuild generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="07534-116">O arquivo de projeto no exemplo HelloApp é o HelloApp.csproj.</span><span class="sxs-lookup"><span data-stu-id="07534-116">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="07534-117">Nesse arquivo, você encontrará a linguagem de desenvolvimento identificada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="07534-117">In that file, you will find the development language identified as follows:</span></span>  
  
   `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="07534-118">Adicione UIDs aos seus arquivos XAML.</span><span class="sxs-lookup"><span data-stu-id="07534-118">Add Uids to your XAML files.</span></span> <span data-ttu-id="07534-119">Os Uids são usados para controlar as alterações nos arquivos e para identificar os itens que devem ser traduzidos.</span><span class="sxs-lookup"><span data-stu-id="07534-119">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="07534-120">Para adicionar UIDs aos seus arquivos, execute `updateuid` em seu arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="07534-120">To add Uids to your files, run `updateuid` on your project file:</span></span>  

   `msbuild -t:updateuid helloapp.csproj`

   <span data-ttu-id="07534-121">Para verificar se você não tem UIDs ausentes ou duplicados, execute `checkuid` :</span><span class="sxs-lookup"><span data-stu-id="07534-121">To verify that you have no missing or duplicate Uids, run `checkuid`:</span></span>  

   `msbuild -t:checkuid helloapp.csproj`

   <span data-ttu-id="07534-122">Após `updateuid` a execução, os arquivos devem conter UIDs.</span><span class="sxs-lookup"><span data-stu-id="07534-122">After running `updateuid`, your files should contain Uids.</span></span> <span data-ttu-id="07534-123">Por exemplo, no arquivo *Pane1. XAML* de HelloApp, você deve encontrar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="07534-123">For example, in the *Pane1.xaml* file of HelloApp, you should find the following:</span></span>  

   ```xaml
   <StackPanel x:Uid="StackPanel_1">
     <TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>
     <TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>
   </StackPanel>
   ```

## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="07534-124">Criar o assembly satélite de recursos de idioma neutro</span><span class="sxs-lookup"><span data-stu-id="07534-124">Create the neutral-language resources satellite assembly</span></span>

<span data-ttu-id="07534-125">Depois que o aplicativo é configurado para gerar um assembly satélite de recursos de idioma neutro, você cria o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07534-125">After the application is configured to generate a neutral-language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="07534-126">Isso gera o assembly do aplicativo principal, bem como o assembly satélite de recursos de idioma neutro que é exigido por LocBaml para localização.</span><span class="sxs-lookup"><span data-stu-id="07534-126">This generates the main application assembly as well as the neutral-language resources satellite assembly that's required by LocBaml for localization.</span></span>

<span data-ttu-id="07534-127">Para criar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="07534-127">To build the application:</span></span>  
  
1. <span data-ttu-id="07534-128">Compile HelloApp para criar uma DLL (biblioteca de vínculo dinâmico):</span><span class="sxs-lookup"><span data-stu-id="07534-128">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
   `msbuild helloapp.csproj`
  
2. <span data-ttu-id="07534-129">O assembly de aplicativo principal recém-criado, HelloApp. exe, é criado na seguinte pasta: *C:\HelloApp\Bin\Debug*</span><span class="sxs-lookup"><span data-stu-id="07534-129">The newly created main application assembly, HelloApp.exe, is created in the following folder: *C:\HelloApp\Bin\Debug*</span></span>
  
3. <span data-ttu-id="07534-130">O assembly satélite de recursos de idioma neutro recentemente criado, HelloApp. Resources. dll, é criado na seguinte pasta: *C:\HelloApp\Bin\Debug\en-US*</span><span class="sxs-lookup"><span data-stu-id="07534-130">The newly created neutral-language resources satellite assembly, HelloApp.resources.dll, is created in the following folder: *C:\HelloApp\Bin\Debug\en-US*</span></span>
  
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="07534-131">Criar a ferramenta LocBaml</span><span class="sxs-lookup"><span data-stu-id="07534-131">Build the LocBaml tool</span></span>  
  
1. <span data-ttu-id="07534-132">Todos os arquivos necessários para compilar LocBaml estão localizados nos exemplos do WPF.</span><span class="sxs-lookup"><span data-stu-id="07534-132">All the files necessary to build LocBaml are located in the WPF samples.</span></span> <span data-ttu-id="07534-133">Baixe os arquivos C# do [exemplo da ferramenta LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span><span class="sxs-lookup"><span data-stu-id="07534-133">Download the C# files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
2. <span data-ttu-id="07534-134">Na linha de comando, execute o arquivo de projeto (locbaml.csproj) para compilar a ferramenta:</span><span class="sxs-lookup"><span data-stu-id="07534-134">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  

   `msbuild locbaml.csproj`
  
3. <span data-ttu-id="07534-135">Vá para o diretório *bin\Release* para localizar o arquivo executável recém-criado (LocBaml. exe).</span><span class="sxs-lookup"><span data-stu-id="07534-135">Go to the *Bin\Release* directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="07534-136">Exemplo: *C:\LocBaml\Bin\Release\locbaml.exe*</span><span class="sxs-lookup"><span data-stu-id="07534-136">Example: *C:\LocBaml\Bin\Release\locbaml.exe*</span></span>
  
4. <span data-ttu-id="07534-137">As opções que você pode especificar ao executar LocBaml são as seguintes.</span><span class="sxs-lookup"><span data-stu-id="07534-137">The options that you can specify when you run LocBaml are as follows.</span></span>

   | <span data-ttu-id="07534-138">Opção</span><span class="sxs-lookup"><span data-stu-id="07534-138">Option</span></span> | <span data-ttu-id="07534-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="07534-139">Description</span></span>|
   | - | - |
   | <span data-ttu-id="07534-140">`parse` ou `-p`</span><span class="sxs-lookup"><span data-stu-id="07534-140">`parse` or `-p`</span></span> | <span data-ttu-id="07534-141">Analisa arquivos BAML, recursos ou DLL para gerar um arquivo. csv ou. txt.</span><span class="sxs-lookup"><span data-stu-id="07534-141">Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span> |
   | <span data-ttu-id="07534-142">`generate` ou `-g`</span><span class="sxs-lookup"><span data-stu-id="07534-142">`generate` or `-g`</span></span> | <span data-ttu-id="07534-143">Gera um arquivo binário localizado usando um arquivo traduzido.</span><span class="sxs-lookup"><span data-stu-id="07534-143">Generates a localized binary file by using a translated file.</span></span> |
   | <span data-ttu-id="07534-144">`out`ou `-o` {*fileDirectory*]</span><span class="sxs-lookup"><span data-stu-id="07534-144">`out` or `-o` {*filedirectory*]</span></span> | <span data-ttu-id="07534-145">Nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="07534-145">Output file name.</span></span> |
   | <span data-ttu-id="07534-146">`culture`ou `-cul` {*Culture*]</span><span class="sxs-lookup"><span data-stu-id="07534-146">`culture` or `-cul` {*culture*]</span></span> | <span data-ttu-id="07534-147">Localidade dos assemblies de saída.</span><span class="sxs-lookup"><span data-stu-id="07534-147">Locale of output assemblies.</span></span> |
   | <span data-ttu-id="07534-148">`translation`ou `-trans` {*translation. csv*]</span><span class="sxs-lookup"><span data-stu-id="07534-148">`translation` or `-trans` {*translation.csv*]</span></span> | <span data-ttu-id="07534-149">Arquivo traduzido ou localizado.</span><span class="sxs-lookup"><span data-stu-id="07534-149">Translated or localized file.</span></span> |
   | <span data-ttu-id="07534-150">`asmpath`ou `-asmpath` {*fileDirectory*]</span><span class="sxs-lookup"><span data-stu-id="07534-150">`asmpath` or `-asmpath` {*filedirectory*]</span></span> | <span data-ttu-id="07534-151">Se o código XAML contiver controles personalizados, você deverá fornecer o `asmpath` ao assembly de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="07534-151">If your XAML code contains custom controls, you must supply the `asmpath` to the custom control assembly.</span></span> |
   | `nologo` | <span data-ttu-id="07534-152">Não exibe nenhum logotipo ou informações de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="07534-152">Displays no logo or copyright information.</span></span> |
   | `verbose` | <span data-ttu-id="07534-153">Exibe informações de modo detalhado.</span><span class="sxs-lookup"><span data-stu-id="07534-153">Displays verbose mode information.</span></span> |
  
   > [!NOTE]
   > <span data-ttu-id="07534-154">Se você precisar de uma lista das opções ao executar a ferramenta, digite `LocBaml.exe` e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="07534-154">If you need a list of the options when you are running the tool, enter `LocBaml.exe` and then press **Enter**.</span></span>
  
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="07534-155">Usar LocBaml para analisar um arquivo</span><span class="sxs-lookup"><span data-stu-id="07534-155">Use LocBaml to parse a file</span></span>

<span data-ttu-id="07534-156">Agora que criou a ferramenta LocBaml, você está pronto para usá-la para analisar o HelloApp.resources.dll e extrair o conteúdo de texto que será localizado.</span><span class="sxs-lookup"><span data-stu-id="07534-156">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="07534-157">Copie o LocBaml.exe para a pasta bin\debug do aplicativo, em que o assembly principal do aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="07534-157">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="07534-158">Para analisar o arquivo do assembly satélite e armazenar o resultado como um arquivo .csv, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="07534-158">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
   `LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv`
  
   > [!NOTE]
   > <span data-ttu-id="07534-159">Se o arquivo de entrada, HelloApp.resources.dll, não estiver no mesmo diretório que o LocBaml.exe mova um dos arquivos para que ambos estejam no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="07534-159">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="07534-160">Ao executar a LocBaml para analisar arquivos, a saída consistirá em sete campos delimitados por vírgulas (arquivos .csv) ou tabulações (arquivos .txt).</span><span class="sxs-lookup"><span data-stu-id="07534-160">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="07534-161">A seguir está o arquivo .csv analisado do HelloApp.resources.dll:</span><span class="sxs-lookup"><span data-stu-id="07534-161">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="07534-162">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span><span class="sxs-lookup"><span data-stu-id="07534-162">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="07534-163">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span><span class="sxs-lookup"><span data-stu-id="07534-163">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="07534-164">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span><span class="sxs-lookup"><span data-stu-id="07534-164">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="07534-165">Os sete campos são:</span><span class="sxs-lookup"><span data-stu-id="07534-165">The seven fields are:</span></span>  
  
   - <span data-ttu-id="07534-166">**Nome de BAML**.</span><span class="sxs-lookup"><span data-stu-id="07534-166">**BAML Name**.</span></span> <span data-ttu-id="07534-167">O nome do recurso BAML em relação ao assembly satélite do idioma de origem.</span><span class="sxs-lookup"><span data-stu-id="07534-167">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   - <span data-ttu-id="07534-168">**Chave de recurso**.</span><span class="sxs-lookup"><span data-stu-id="07534-168">**Resource Key**.</span></span> <span data-ttu-id="07534-169">O identificador do recurso localizado.</span><span class="sxs-lookup"><span data-stu-id="07534-169">The localized resource identifier.</span></span>  
  
   - <span data-ttu-id="07534-170">**Categoria**.</span><span class="sxs-lookup"><span data-stu-id="07534-170">**Category**.</span></span> <span data-ttu-id="07534-171">O tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="07534-171">The value type.</span></span> <span data-ttu-id="07534-172">Consulte [atributos e comentários de localização](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="07534-172">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="07534-173">**Legibilidade**.</span><span class="sxs-lookup"><span data-stu-id="07534-173">**Readability**.</span></span> <span data-ttu-id="07534-174">Se o valor pode ser lido por um localizador.</span><span class="sxs-lookup"><span data-stu-id="07534-174">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="07534-175">Consulte [atributos e comentários de localização](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="07534-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="07534-176">**Modificabilidade**.</span><span class="sxs-lookup"><span data-stu-id="07534-176">**Modifiability**.</span></span> <span data-ttu-id="07534-177">Se o valor pode ser modificado por um localizador.</span><span class="sxs-lookup"><span data-stu-id="07534-177">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="07534-178">Consulte [atributos e comentários de localização](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="07534-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="07534-179">**Comentários**.</span><span class="sxs-lookup"><span data-stu-id="07534-179">**Comments**.</span></span> <span data-ttu-id="07534-180">Descrição adicional do valor para ajudar a determinar como um valor é localizado.</span><span class="sxs-lookup"><span data-stu-id="07534-180">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="07534-181">Consulte [atributos e comentários de localização](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="07534-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="07534-182">**Valor**.</span><span class="sxs-lookup"><span data-stu-id="07534-182">**Value**.</span></span> <span data-ttu-id="07534-183">O valor de texto a traduzir para a cultura desejada.</span><span class="sxs-lookup"><span data-stu-id="07534-183">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="07534-184">A tabela a seguir mostra como esses campos são mapeados para os valores delimitados do arquivo .csv:</span><span class="sxs-lookup"><span data-stu-id="07534-184">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="07534-185">Nome BAML</span><span class="sxs-lookup"><span data-stu-id="07534-185">BAML name</span></span>|<span data-ttu-id="07534-186">Chave de recurso</span><span class="sxs-lookup"><span data-stu-id="07534-186">Resource key</span></span>|<span data-ttu-id="07534-187">Categoria</span><span class="sxs-lookup"><span data-stu-id="07534-187">Category</span></span>|<span data-ttu-id="07534-188">Legibilidade</span><span class="sxs-lookup"><span data-stu-id="07534-188">Readability</span></span>|<span data-ttu-id="07534-189">Modificabilidade</span><span class="sxs-lookup"><span data-stu-id="07534-189">Modifiability</span></span>|<span data-ttu-id="07534-190">Comentários</span><span class="sxs-lookup"><span data-stu-id="07534-190">Comments</span></span>|<span data-ttu-id="07534-191">Valor</span><span class="sxs-lookup"><span data-stu-id="07534-191">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="07534-192">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="07534-192">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="07534-193">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="07534-193">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="07534-194">Ignorar</span><span class="sxs-lookup"><span data-stu-id="07534-194">Ignore</span></span>|<span data-ttu-id="07534-195">FALSE</span><span class="sxs-lookup"><span data-stu-id="07534-195">FALSE</span></span>|<span data-ttu-id="07534-196">FALSE</span><span class="sxs-lookup"><span data-stu-id="07534-196">FALSE</span></span>||<span data-ttu-id="07534-197">#Text1; #Text2</span><span class="sxs-lookup"><span data-stu-id="07534-197">#Text1;#Text2</span></span>|
   |<span data-ttu-id="07534-198">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="07534-198">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="07534-199">Text1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="07534-199">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="07534-200">Nenhum</span><span class="sxs-lookup"><span data-stu-id="07534-200">None</span></span>|<span data-ttu-id="07534-201">TRUE</span><span class="sxs-lookup"><span data-stu-id="07534-201">TRUE</span></span>|<span data-ttu-id="07534-202">TRUE</span><span class="sxs-lookup"><span data-stu-id="07534-202">TRUE</span></span>||<span data-ttu-id="07534-203">Olá, Mundo</span><span class="sxs-lookup"><span data-stu-id="07534-203">Hello World</span></span>|
   |<span data-ttu-id="07534-204">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="07534-204">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="07534-205">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="07534-205">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="07534-206">Nenhum</span><span class="sxs-lookup"><span data-stu-id="07534-206">None</span></span>|<span data-ttu-id="07534-207">TRUE</span><span class="sxs-lookup"><span data-stu-id="07534-207">TRUE</span></span>|<span data-ttu-id="07534-208">TRUE</span><span class="sxs-lookup"><span data-stu-id="07534-208">TRUE</span></span>||<span data-ttu-id="07534-209">Goodbye World</span><span class="sxs-lookup"><span data-stu-id="07534-209">Goodbye World</span></span>|
  
   <span data-ttu-id="07534-210">Observe que todos os valores do campo **comentários** não contêm valores; se um campo não tiver um valor, ele estará vazio.</span><span class="sxs-lookup"><span data-stu-id="07534-210">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="07534-211">Observe também que o item na primeira linha não é legível nem modificável e tem "ignorar" como seu valor de **categoria** , que indica que o valor não é localizável.</span><span class="sxs-lookup"><span data-stu-id="07534-211">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="07534-212">Para facilitar a descoberta de itens localizáveis em arquivos analisados, especialmente em arquivos grandes, você pode classificar ou filtrar os itens por **categoria**, **legibilidade**e **modificação**.</span><span class="sxs-lookup"><span data-stu-id="07534-212">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="07534-213">Por exemplo, você pode filtrar valores e ilegíveis e não modificáveis.</span><span class="sxs-lookup"><span data-stu-id="07534-213">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
## <a name="translate-the-localizable-content"></a><span data-ttu-id="07534-214">Traduza o conteúdo localizável</span><span class="sxs-lookup"><span data-stu-id="07534-214">Translate the localizable content</span></span>

<span data-ttu-id="07534-215">Use qualquer ferramenta que você tiver disponível para traduzir o conteúdo extraído.</span><span class="sxs-lookup"><span data-stu-id="07534-215">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="07534-216">Uma boa maneira de fazer isso é gravar os recursos em um arquivo. csv e exibi-los no Microsoft Excel, fazendo alterações de tradução na última coluna (valor).</span><span class="sxs-lookup"><span data-stu-id="07534-216">A good way to do this is to write the resources to a .csv file and view them in Microsoft Excel, making translation changes to the last column (value).</span></span>  
  
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="07534-217">Use LocBaml para gerar um novo arquivo. Resources. dll</span><span class="sxs-lookup"><span data-stu-id="07534-217">Use LocBaml to generate a new .resources.dll file</span></span>

<span data-ttu-id="07534-218">O conteúdo que foi identificado ao analisar o HelloApp.resources.dll com a LocBaml foi traduzido e deve ser mesclado de volta no aplicativo original.</span><span class="sxs-lookup"><span data-stu-id="07534-218">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="07534-219">Use a `generate` `-g` opção ou para gerar um novo arquivo. Resources. dll.</span><span class="sxs-lookup"><span data-stu-id="07534-219">Use the `generate` or `-g` option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="07534-220">Use a seguinte sintaxe para gerar um novo arquivo HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="07534-220">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="07534-221">Marque a cultura como en-US (/cul:en-US).</span><span class="sxs-lookup"><span data-stu-id="07534-221">Mark the culture as en-US (/cul:en-US).</span></span>  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US`  

   > [!NOTE]
   > <span data-ttu-id="07534-222">Se o arquivo de entrada, Hello.csv, não estiver no mesmo diretório que o executável, LocBaml.exe, mova um dos arquivos para que ambos estejam no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="07534-222">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="07534-223">Substitua o antigo arquivo *HelloApp. Resources. dll* no diretório *C:\HelloApp\Bin\Debug\en-US\HelloApp.Resources.dll* pelo arquivo *HelloApp. Resources. dll* recém-criado.</span><span class="sxs-lookup"><span data-stu-id="07534-223">Replace the old *HelloApp.resources.dll* file in the *C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll* directory with your newly created *HelloApp.resources.dll* file.</span></span>  
  
3. <span data-ttu-id="07534-224">"Hello World" e "Goodbye World" agora devem estar traduzidos em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07534-224">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="07534-225">Para traduzir para uma cultura diferente, use a cultura do idioma para o qual você está traduzindo.</span><span class="sxs-lookup"><span data-stu-id="07534-225">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="07534-226">O exemplo a seguir mostra como traduzir para francês canadense:</span><span class="sxs-lookup"><span data-stu-id="07534-226">The following example shows how to translate to French-Canadian:</span></span>  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA`  
  
5. <span data-ttu-id="07534-227">No mesmo assembly que o assembly principal do aplicativo, crie uma nova pasta específica de cultura para abrigar o novo assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="07534-227">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="07534-228">Para francês canadense, a pasta seria fr-CA.</span><span class="sxs-lookup"><span data-stu-id="07534-228">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="07534-229">Copie o assembly satélite gerado para a nova pasta.</span><span class="sxs-lookup"><span data-stu-id="07534-229">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="07534-230">Para testar o novo assembly satélite, você precisa alterar a cultura na qual o aplicativo será executado.</span><span class="sxs-lookup"><span data-stu-id="07534-230">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="07534-231">É possível fazer isso de duas formas:</span><span class="sxs-lookup"><span data-stu-id="07534-231">You can do this in one of two ways:</span></span>  
  
   - <span data-ttu-id="07534-232">Altere as configurações regionais do seu sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="07534-232">Change your operating system's regional settings.</span></span>
  
   - <span data-ttu-id="07534-233">Em seu aplicativo, adicione o seguinte código em App.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="07534-233">In your application, add the following code to App.xaml.cs:</span></span>  
  
     [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
     [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
     [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
## <a name="tips-for-using-locbaml"></a><span data-ttu-id="07534-234">Dicas para usar LocBaml</span><span class="sxs-lookup"><span data-stu-id="07534-234">Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="07534-235">Todos os assemblies dependentes que definem controles personalizados devem ser copiados para o diretório local da LocBaml ou instalados no GAC.</span><span class="sxs-lookup"><span data-stu-id="07534-235">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="07534-236">Isso é necessário porque a API de localização deve ter acesso aos assemblies dependentes quando ele lê o XAML binário (BAML).</span><span class="sxs-lookup"><span data-stu-id="07534-236">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="07534-237">Se o assembly principal é assinado, a DLL de recurso gerado também deve ser assinada para que seja carregada.</span><span class="sxs-lookup"><span data-stu-id="07534-237">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="07534-238">A versão da DLL de recurso localizado precisa ser sincronizada com o assembly principal.</span><span class="sxs-lookup"><span data-stu-id="07534-238">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="07534-239">Confira também</span><span class="sxs-lookup"><span data-stu-id="07534-239">See also</span></span>

- [<span data-ttu-id="07534-240">Globalização do WPF</span><span class="sxs-lookup"><span data-stu-id="07534-240">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="07534-241">Visão geral do uso de layout automático</span><span class="sxs-lookup"><span data-stu-id="07534-241">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
