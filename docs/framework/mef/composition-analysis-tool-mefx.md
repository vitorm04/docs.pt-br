---
title: "Ferramenta de Análise de Composição (Mefx)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 740ba87fd247e05b1bc32e3732819514ba2806ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="33f4e-102">Ferramenta de Análise de Composição (Mefx)</span><span class="sxs-lookup"><span data-stu-id="33f4e-102">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="33f4e-103">A ferramenta de análise de composição (Mefx) é um aplicativo de linha de comando que analisa biblioteca (. dll) e arquivos de aplicativo (.exe) contendo partes Managed Extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="33f4e-103">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="33f4e-104">A principal finalidade de Mefx é fornecer aos desenvolvedores uma maneira de diagnosticar falhas de composição em seus aplicativos de MEF sem a necessidade de adicionar o código de rastreamento incômodo ao próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="33f4e-104">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="33f4e-105">Ele também pode ser útil para ajudar a entender as partes de uma biblioteca fornecidos por terceiros.</span><span class="sxs-lookup"><span data-stu-id="33f4e-105">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="33f4e-106">Este tópico descreve como usar Mefx e fornece uma referência para a sintaxe.</span><span class="sxs-lookup"><span data-stu-id="33f4e-106">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a><span data-ttu-id="33f4e-107">Obtendo Mefx</span><span class="sxs-lookup"><span data-stu-id="33f4e-107">Getting Mefx</span></span>  
 <span data-ttu-id="33f4e-108">Mefx está disponível no GitHub em [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span><span class="sxs-lookup"><span data-stu-id="33f4e-108">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="33f4e-109">Basta baixar e descompactar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="33f4e-109">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a><span data-ttu-id="33f4e-110">Sintaxe básica</span><span class="sxs-lookup"><span data-stu-id="33f4e-110">Basic Syntax</span></span>  
 <span data-ttu-id="33f4e-111">Mefx é invocado na linha de comando no seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="33f4e-111">Mefx is invoked from the command line in the following format:</span></span>  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="33f4e-112">O primeiro conjunto de argumentos de especificar os arquivos e diretórios do qual carregar partes para análise.</span><span class="sxs-lookup"><span data-stu-id="33f4e-112">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="33f4e-113">Especifique um arquivo com o `/file:` comutador e um diretório com o `/directory:` alternar.</span><span class="sxs-lookup"><span data-stu-id="33f4e-113">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="33f4e-114">Você pode especificar vários arquivos ou diretórios, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="33f4e-114">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  <span data-ttu-id="33f4e-115">Cada arquivo. dll ou .exe devem ser carregados somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="33f4e-115">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="33f4e-116">Se um arquivo for carregado várias vezes, a ferramenta pode retornar informações incorretas.</span><span class="sxs-lookup"><span data-stu-id="33f4e-116">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="33f4e-117">Após a lista de arquivos e diretórios, você deve especificar um comando e as opções para o comando.</span><span class="sxs-lookup"><span data-stu-id="33f4e-117">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a><span data-ttu-id="33f4e-118">Listando partes disponíveis</span><span class="sxs-lookup"><span data-stu-id="33f4e-118">Listing Available Parts</span></span>  
 <span data-ttu-id="33f4e-119">Use o `/parts` declarado de ação para listar todas as partes nos arquivos carregados.</span><span class="sxs-lookup"><span data-stu-id="33f4e-119">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="33f4e-120">O resultado é uma lista simple de nomes de parte.</span><span class="sxs-lookup"><span data-stu-id="33f4e-120">The result is a simple list of part names.</span></span>  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="33f4e-121">Para obter mais informações sobre as partes, use o `/verbose` opção.</span><span class="sxs-lookup"><span data-stu-id="33f4e-121">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="33f4e-122">Isso produzirá obter mais informações para todas as partes disponíveis.</span><span class="sxs-lookup"><span data-stu-id="33f4e-122">This will output more information for all available parts.</span></span> <span data-ttu-id="33f4e-123">Para obter mais informações sobre uma única parte, use o `/type` ação em vez de `/parts`.</span><span class="sxs-lookup"><span data-stu-id="33f4e-123">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a><span data-ttu-id="33f4e-124">Listando as importações e exportações</span><span class="sxs-lookup"><span data-stu-id="33f4e-124">Listing Imports and Exports</span></span>  
 <span data-ttu-id="33f4e-125">O `/imports` e `/exports` ações listará todas as partes importadas e todas as partes exportadas, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="33f4e-125">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="33f4e-126">Você também pode listar as partes que importar ou exportar um tipo específico usando o `/importers` ou `/exporters` ações.</span><span class="sxs-lookup"><span data-stu-id="33f4e-126">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="33f4e-127">Você também pode aplicar o `/verbose` opção para essas ações.</span><span class="sxs-lookup"><span data-stu-id="33f4e-127">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a><span data-ttu-id="33f4e-128">Localizando rejeitadas partes</span><span class="sxs-lookup"><span data-stu-id="33f4e-128">Finding Rejected Parts</span></span>  
 <span data-ttu-id="33f4e-129">Depois de ter carregado as partes disponíveis, Mefx usa o mecanismo de composição de MEF para compor-los.</span><span class="sxs-lookup"><span data-stu-id="33f4e-129">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="33f4e-130">Partes que não podem ser compostas com êxito são chamados de *rejeitadas*.</span><span class="sxs-lookup"><span data-stu-id="33f4e-130">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="33f4e-131">Para listar todas as partes rejeitadas, use o `/rejected` ação.</span><span class="sxs-lookup"><span data-stu-id="33f4e-131">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="33f4e-132">Você pode usar o `/verbose` opção com o `/rejected` ação Imprimir informações detalhadas sobre rejeitada partes.</span><span class="sxs-lookup"><span data-stu-id="33f4e-132">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="33f4e-133">No exemplo a seguir, o `ClassLibrary1` DLL contém o `AddIn` parte, que importa o `MemberPart` e `ChainOne` partes.</span><span class="sxs-lookup"><span data-stu-id="33f4e-133">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="33f4e-134">`ChainOne`importa `ChainTwo`, mas `ChainTwo` não existe.</span><span class="sxs-lookup"><span data-stu-id="33f4e-134">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="33f4e-135">Isso significa que `ChainOne` for rejeitada, que faz com que `AddIn` sejam rejeitadas.</span><span class="sxs-lookup"><span data-stu-id="33f4e-135">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="33f4e-136">O exemplo a seguir mostra a saída completa do comando anterior:</span><span class="sxs-lookup"><span data-stu-id="33f4e-136">The following shows the complete output of the previous command:</span></span>  
  
```  
[Part] ClassLibrary1.AddIn from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] ClassLibrary1.AddIn (ContractName="ClassLibrary1.AddIn")  
  [Import] ClassLibrary1.AddIn.memberPart (ContractName="ClassLibrary1.MemberPart")  
    [SatisfiedBy] ClassLibrary1.MemberPart (ContractName="ClassLibrary1.MemberPart") from: ClassLibrary1.MemberPart from: AssemblyCatalog (Assembly="ClassLibrar  
y1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Import] ClassLibrary1.AddIn.chain (ContractName="ClassLibrary1.ChainOne")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainOne") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainOne".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
    [Unsuitable] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
from: ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
      [Because] PartDefinitionIsRejected, The part providing the export is rejected because of other issues.  
  
[Part] ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Primary Rejection]  
  [Export] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
  [Import] ClassLibrary1.ChainOne.chain (ContractName="ClassLibrary1.ChainTwo")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainTwo") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainTwo".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
```  
  
 <span data-ttu-id="33f4e-137">As informações interessantes estão contidas no `[Exception]` e `[Unsuitable]` resultados.</span><span class="sxs-lookup"><span data-stu-id="33f4e-137">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="33f4e-138">O `[Exception]` resultado fornece informações sobre por que uma parte foi rejeitada.</span><span class="sxs-lookup"><span data-stu-id="33f4e-138">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="33f4e-139">O `[Unsuitable]` resultado indica por que uma parte de outra forma correspondente não pôde ser usada para preencher uma importação; nesse caso, porque essa parte se rejeitados para importações ausentes.</span><span class="sxs-lookup"><span data-stu-id="33f4e-139">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a><span data-ttu-id="33f4e-140">Analisando a principal causa</span><span class="sxs-lookup"><span data-stu-id="33f4e-140">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="33f4e-141">Se várias partes são vinculadas em uma cadeia de dependência de tempo, um problema que envolve uma parte na parte inferior pode causar a cadeia inteira deve ser rejeitada.</span><span class="sxs-lookup"><span data-stu-id="33f4e-141">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="33f4e-142">Diagnosticando desses problemas pode ser difícil, pois a causa da falha nem sempre é óbvia.</span><span class="sxs-lookup"><span data-stu-id="33f4e-142">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="33f4e-143">Para ajudar a resolver o problema, você pode usar o `/causes` ação, que tenta localizar a causa raiz de qualquer rejeição em cascata.</span><span class="sxs-lookup"><span data-stu-id="33f4e-143">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="33f4e-144">Usando o `/causes` ação no exemplo anterior seria lista apenas as informações para `ChainOne`, cuja preenchida importação é a causa raiz de rejeição de `AddIn`.</span><span class="sxs-lookup"><span data-stu-id="33f4e-144">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="33f4e-145">O `/causes` ação pode ser usada em ambos os normal e `/verbose` opções.</span><span class="sxs-lookup"><span data-stu-id="33f4e-145">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33f4e-146">Na maioria dos casos, Mefx poderá diagnosticar a causa de uma falha em cascata.</span><span class="sxs-lookup"><span data-stu-id="33f4e-146">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="33f4e-147">No entanto, em casos onde partes são adicionadas por meio de programação para um contêiner, casos que envolvem contêineres hierárquicos, ou que envolvem personalizado `ExportProvider` implementações, Mefx não será possível diagnosticar a causa.</span><span class="sxs-lookup"><span data-stu-id="33f4e-147">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="33f4e-148">Em geral, os casos descritos anteriormente devem ser evitados quando possível, como falhas são geralmente difíceis de diagnosticar.</span><span class="sxs-lookup"><span data-stu-id="33f4e-148">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a><span data-ttu-id="33f4e-149">Listas de branco</span><span class="sxs-lookup"><span data-stu-id="33f4e-149">White Lists</span></span>  
 <span data-ttu-id="33f4e-150">O `/whitelist` opção permite que você especifique um arquivo de texto que mostra as partes que devem ser rejeitados.</span><span class="sxs-lookup"><span data-stu-id="33f4e-150">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="33f4e-151">Em seguida, serão sinalizadas rejeições inesperadas.</span><span class="sxs-lookup"><span data-stu-id="33f4e-151">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="33f4e-152">Isso pode ser útil quando você analisa uma biblioteca incompleta ou em uma biblioteca sub que não tem algumas dependências.</span><span class="sxs-lookup"><span data-stu-id="33f4e-152">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="33f4e-153">O `/whitelist` opção pode ser aplicada para o `/rejected` ou `/causes` ações.</span><span class="sxs-lookup"><span data-stu-id="33f4e-153">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="33f4e-154">Considere a possibilidade de um arquivo chamado Test. txt que contém o texto "ClassLibrary1.ChainOne".</span><span class="sxs-lookup"><span data-stu-id="33f4e-154">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="33f4e-155">Se você executar o `/rejected` ação com o `/whitelist` opção no exemplo anterior, ele produzirá a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="33f4e-155">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
