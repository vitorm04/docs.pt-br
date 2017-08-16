---
title: "Winmdexp.exe (Ferramenta de Exportação de Metadados do Windows Runtime) | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 48b7839ebb5ff46d6ede017349f9345c0184abcf
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Ferramenta de Exportação de Metadados do Windows Runtime )
A Ferramenta de Exportação dos Metadados [!INCLUDE[wrt](../../../includes/wrt-md.md)] (Winmdexp.exe) transforma um módulo do .NET Framework em um arquivo que contém metadados [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Embora os assemblies do .NET Framework e os arquivos de metadados [!INCLUDE[wrt](../../../includes/wrt-md.md)] usem o mesmo formato físico, existem diferenças no conteúdo das tabelas de metadados, o que significa que os assemblies do .NET Framework não são automaticamente úteis como Componentes [!INCLUDE[wrt](../../../includes/wrt-md.md)]. O processo de transformar um módulo do .NET Framework em um componente [!INCLUDE[wrt](../../../includes/wrt-md.md)] é conhecido como *exportação*. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e no [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], o arquivo de metadados do Windows (.winmd) resultante contém metadados e implementação.  
  
 Quando você usar o modelo **[!INCLUDE[wrt](../../../includes/wrt-md.md)] Componente**, localizado na **Windows Store** para C# e Visual Basic no [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] ou no [!INCLUDE[vs_dev11_ext](../../../includes/vs-dev11-ext-md.md)], o alvo do compilador será um arquivo .winmdobj e uma etapa de build subsequente chama Winmdexp.exe de uma etapa de compilação para exportar o arquivo .winmdobj para um arquivo .winmd. Essa é a maneira recomendada para compilar um componente [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Use Winmdexp.exe diretamente quando você quiser mais controle sobre o processo de compilação do que o dado pelo Visual Studio.  
  
 Essa ferramenta é instalada automaticamente com o Visual Studio. Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor (ou o Prompt de Comando do Visual Studio no Windows 7). Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 No prompt de comando, digite o seguinte:  
  
## <a name="syntax"></a>Sintaxe  
  
```  
winmdexp [options] winmdmodule  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Argumento ou opção|Descrição|  
|------------------------|-----------------|  
|`winmdmodule`|Especifica o módulo (.winmdobj) a ser exportado. Somente um módulo é permitido. Para criar esse módulo, use a opção do compilador `/target` com o destino `winmdobj`. Consulte See [/target:winmdobj (Opções do compilador de C#)](~/docs/csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) ou [/target (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/target.md) na Biblioteca MSDN.|  
|`/docfile:` `docfile`<br /><br /> `/d:` `docfile`|Especifica o arquivo da documentação XML de saída que Winmdexp.exe produzirá. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], o arquivo de saída é basicamente igual ao arquivo de documentação XML da entrada.|  
|`/moduledoc:` `docfile`<br /><br /> `/md:` `docfile`|Especifica o nome do arquivo de documentação XML que o compilador produziu com `winmdmodule`.|  
|`/modulepdb:` `symbolfile`<br /><br /> `/mp:` `symbolfile`|Especifica o nome do arquivo PDB (banco de dados do programa) que contém símbolos para `winmdmodule`.|  
|`/nowarn:` `warning`|Suprime o número de aviso especificado. Para *aviso*, forneça apenas a parte numérica do código de erro, sem zeros à esquerda.|  
|`/out:` `file`<br /><br /> `/o:` `file`|Especifica o nome do arquivo de metadados do Windows (.winmd) de saída.|  
|`/pdb:` `symbolfile`<br /><br /> `/p:` `symbolfile`|Especifica o nome do arquivo PDB de saída que conterá os símbolos do arquivo de metadados do Windows (.winmd) exportado.|  
|`/reference:` `winmd`<br /><br /> `/r:` `winmd`|Especifica um arquivo de metadados (.winmd ou assembly) para fazer referencia durante a exportação. Se você usar os assemblies de referência em “\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5" ("\Program Files\\...” em computadores 32 bits), inclua referências para System.Runtime.dll e mscorlib.dll.|  
|`/utf8output`|Especifica que as mensagens de saída devem estar na codificação UTF-8.|  
|`/warnaserror+`|Especifica que todos os avisos devem ser tratado como erros.|  
|**@** `responsefile`|Especifica um arquivo de resposta (.rsp) que contém opções (ou `winmdmodule`). Cada linha em `responsefile` deve conter um único argumento ou opção.|  
  
## <a name="remarks"></a>Comentários  
 Winmdexp.exe não foi projetado para converter um assembly do .NET Framework arbitrário para um arquivo .winmd. Ele exige um módulo compilado com a opção `/target:winmdobj`, e as restrições adicionais se aplicam. A mais importante dessas limitações é que todos os tipos expostos na superfície da API do assembly devem ser tipos [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Para obter mais informações, consulte a seção “Declarando tipos em Componentes do Windows Runtime” do artigo [Criando Componentes do Windows Runtime no C# e no Visual Basic](http://go.microsoft.com/fwlink/p/?LinkID=238313) no Centro de Desenvolvimento do Windows.  
  
 Ao gravar um aplicativo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ou um componente [!INCLUDE[wrt](../../../includes/wrt-md.md)] com C# ou Visual Basic, o .NET Framework dá suporte para deixar a programação com o [!INCLUDE[wrt](../../../includes/wrt-md.md)] mais natural. Isso é abordado no artigo [Suporte do .NET Framework para Aplicativos da Windows Store e do Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). No processo, alguns tipos [!INCLUDE[wrt](../../../includes/wrt-md.md)] mais usados são mapeados para tipos do .NET Framework. Winmdexp.exe reverte esse processo e produz uma superfície de API que usa os tipos [!INCLUDE[wrt](../../../includes/wrt-md.md)] correspondentes. Por exemplo, tipos construídos com base na interface <xref:System.Collections.Generic.IList%601> são mapeados para tipos construídos com base na interface [!INCLUDE[wrt](../../../includes/wrt-md.md)][IVector\<T>](http://go.microsoft.com/fwlink/p/?LinkId=251132).  
  
## <a name="see-also"></a>Consulte também  
 [Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)   
 [Criando Componentes do Windows Runtime no C# e no Visual Basic](http://go.microsoft.com/fwlink/p/?LinkID=238313)   
 [Mensagens de erro Winmdexp.exe](../../../docs/framework/tools/winmdexp-exe-error-messages.md)   
 [Ferramentas de build, implantação e configuração (.NET Framework)](http://msdn.microsoft.com/en-us/b8c921be-6012-4181-b8d4-ab15813fc9a7)

