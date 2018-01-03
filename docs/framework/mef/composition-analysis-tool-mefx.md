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
ms.workload: dotnet
ms.openlocfilehash: d6e5ab22ff2fe382fa2a266e3180cb34f970cc48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="composition-analysis-tool-mefx"></a>Ferramenta de Análise de Composição (Mefx)
A ferramenta de análise de composição (Mefx) é um aplicativo de linha de comando que analisa biblioteca (. dll) e arquivos de aplicativo (.exe) contendo partes Managed Extensibility Framework (MEF). A principal finalidade de Mefx é fornecer aos desenvolvedores uma maneira de diagnosticar falhas de composição em seus aplicativos de MEF sem a necessidade de adicionar o código de rastreamento incômodo ao próprio aplicativo. Ele também pode ser útil para ajudar a entender as partes de uma biblioteca fornecidos por terceiros. Este tópico descreve como usar Mefx e fornece uma referência para a sintaxe.  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a>Obtendo Mefx  
 Mefx está disponível no GitHub em [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0). Basta baixar e descompactar a ferramenta.  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a>Sintaxe básica  
 Mefx é invocado na linha de comando no seguinte formato:  
  
```  
mefx [files and directories] [action] [options]  
```  
  
 O primeiro conjunto de argumentos de especificar os arquivos e diretórios do qual carregar partes para análise. Especifique um arquivo com o `/file:` comutador e um diretório com o `/directory:` alternar. Você pode especificar vários arquivos ou diretórios, conforme mostrado no exemplo a seguir:  
  
```  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
>  Cada arquivo. dll ou .exe devem ser carregados somente uma vez. Se um arquivo for carregado várias vezes, a ferramenta pode retornar informações incorretas.  
  
 Após a lista de arquivos e diretórios, você deve especificar um comando e as opções para o comando.  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a>Listando partes disponíveis  
 Use o `/parts` declarado de ação para listar todas as partes nos arquivos carregados. O resultado é uma lista simple de nomes de parte.  
  
```  
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 Para obter mais informações sobre as partes, use o `/verbose` opção. Isso produzirá obter mais informações para todas as partes disponíveis. Para obter mais informações sobre uma única parte, use o `/type` ação em vez de `/parts`.  
  
```  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a>Listando as importações e exportações  
 O `/imports` e `/exports` ações listará todas as partes importadas e todas as partes exportadas, respectivamente. Você também pode listar as partes que importar ou exportar um tipo específico usando o `/importers` ou `/exporters` ações.  
  
```  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 Você também pode aplicar o `/verbose` opção para essas ações.  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a>Localizando rejeitadas partes  
 Depois de ter carregado as partes disponíveis, Mefx usa o mecanismo de composição de MEF para compor-los. Partes que não podem ser compostas com êxito são chamados de *rejeitadas*. Para listar todas as partes rejeitadas, use o `/rejected` ação.  
  
 Você pode usar o `/verbose` opção com o `/rejected` ação Imprimir informações detalhadas sobre rejeitada partes. No exemplo a seguir, o `ClassLibrary1` DLL contém o `AddIn` parte, que importa o `MemberPart` e `ChainOne` partes. `ChainOne`importa `ChainTwo`, mas `ChainTwo` não existe. Isso significa que `ChainOne` for rejeitada, que faz com que `AddIn` sejam rejeitadas.  
  
```  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 O exemplo a seguir mostra a saída completa do comando anterior:  
  
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
  
 As informações interessantes estão contidas no `[Exception]` e `[Unsuitable]` resultados. O `[Exception]` resultado fornece informações sobre por que uma parte foi rejeitada. O `[Unsuitable]` resultado indica por que uma parte de outra forma correspondente não pôde ser usada para preencher uma importação; nesse caso, porque essa parte se rejeitados para importações ausentes.  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a>Analisando a principal causa  
 Se várias partes são vinculadas em uma cadeia de dependência de tempo, um problema que envolve uma parte na parte inferior pode causar a cadeia inteira deve ser rejeitada. Diagnosticando desses problemas pode ser difícil, pois a causa da falha nem sempre é óbvia. Para ajudar a resolver o problema, você pode usar o `/causes` ação, que tenta localizar a causa raiz de qualquer rejeição em cascata.  
  
 Usando o `/causes` ação no exemplo anterior seria lista apenas as informações para `ChainOne`, cuja preenchida importação é a causa raiz de rejeição de `AddIn`. O `/causes` ação pode ser usada em ambos os normal e `/verbose` opções.  
  
> [!NOTE]
>  Na maioria dos casos, Mefx poderá diagnosticar a causa de uma falha em cascata. No entanto, em casos onde partes são adicionadas por meio de programação para um contêiner, casos que envolvem contêineres hierárquicos, ou que envolvem personalizado `ExportProvider` implementações, Mefx não será possível diagnosticar a causa. Em geral, os casos descritos anteriormente devem ser evitados quando possível, como falhas são geralmente difíceis de diagnosticar.  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a>Listas de branco  
 O `/whitelist` opção permite que você especifique um arquivo de texto que mostra as partes que devem ser rejeitados. Em seguida, serão sinalizadas rejeições inesperadas. Isso pode ser útil quando você analisa uma biblioteca incompleta ou em uma biblioteca sub que não tem algumas dependências. O `/whitelist` opção pode ser aplicada para o `/rejected` ou `/causes` ações.  
  
 Considere a possibilidade de um arquivo chamado Test. txt que contém o texto "ClassLibrary1.ChainOne". Se você executar o `/rejected` ação com o `/whitelist` opção no exemplo anterior, ele produzirá a saída a seguir:  
  
```  
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
