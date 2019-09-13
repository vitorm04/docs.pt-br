---
title: Winmdexp.exe (Ferramenta de Exportação de Metadados do Windows Runtime )
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0664a68d258380fd9e4824b80f0d7a244cb61e85
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894782"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Ferramenta de Exportação de Metadados do Windows Runtime )
A Ferramenta de Exportação dos Metadados Windows Runtime (Winmdexp.exe) transforma um módulo do .NET Framework em um arquivo que contém metadados do Windows Runtime. Embora os assemblies do .NET Framework e os arquivos de metadados do Windows Runtime usem o mesmo formato físico, existem diferenças no conteúdo das tabelas de metadados, o que significa que os assemblies do .NET Framework não são automaticamente úteis como Componentes do Tempo de Execução do Windows. O processo de transformar um módulo do .NET Framework em um componente do Tempo de Execução do Windows é conhecido como *exportação*. No .NET Framework 4.5 e no .NET Framework 4.5.1, o arquivo de metadados do Windows (.winmd) resultante contém metadados e implementação.  
  
 Quando você usar o modelo **Componente do Tempo de Execução do Windows**, localizado na **Windows Store** para C# e Visual Basic no Visual Studio 2013 ou Visual Studio 2012, o alvo do compilador será um arquivo .winmdobj e uma etapa de compilação subsequente chamará Winmdexp.exe para exportar o arquivo .winmdobj para um arquivo .winmd. Essa é a maneira recomendada para compilar um componente do Tempo de Execução do Windows. Use Winmdexp.exe diretamente quando você quiser mais controle sobre o processo de compilação do que o dado pelo Visual Studio.  
  
 Essa ferramenta é instalada automaticamente com o Visual Studio. Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor para Visual Studio (ou o Prompt de Comando do Visual Studio no Windows 7). Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 No prompt de comando, digite o seguinte:  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>Parâmetros  
  
|Argumento ou opção|Descrição|  
|------------------------|-----------------|  
|`winmdmodule`|Especifica o módulo (.winmdobj) a ser exportado. Somente um módulo é permitido. Para criar esse módulo, use a opção do compilador `/target` com o destino `winmdobj`. Consulte [/target:winmdobj (Opções do compilador C#)](../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) ou [/target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`/docfile:` `docfile`<br /><br /> `/d:` `docfile`|Especifica o arquivo da documentação XML de saída que Winmdexp.exe produzirá. No .NET Framework 4.5, o arquivo de saída é basicamente igual ao arquivo de documentação XML da entrada.|  
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
 Winmdexp.exe não foi projetado para converter um assembly do .NET Framework arbitrário para um arquivo .winmd. Ele exige um módulo compilado com a opção `/target:winmdobj`, e as restrições adicionais se aplicam. A mais importante dessas limitações é que todos os tipos expostos na superfície da API do assembly precisam ser tipos do Windows Runtime. Para obter mais informações, consulte a seção “Declarando tipos em Componentes do Windows Runtime” do artigo [Criando Componentes do Windows Runtime no C# e no Visual Basic](https://go.microsoft.com/fwlink/p/?LinkID=238313) no Centro de Desenvolvimento do Windows.  
  
 Quando você grava um aplicativo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ou um componente do Tempo de Execução do Windows com C# ou Visual Basic, o .NET Framework dá suporte para deixar a programação com o Windows Runtime mais natural. Isso é abordado no artigo [Suporte do .NET Framework para Aplicativos da Windows Store e do Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md). No processo, alguns tipos do Windows Runtime mais usados são mapeados para tipos do .NET Framework. Winmdexp.exe reverte esse processo e produz uma superfície de API que usa os tipos do Windows Runtime correspondentes. Por exemplo, tipos construídos com base na interface <xref:System.Collections.Generic.IList%601> são mapeados para tipos construídos com base na interface [IVector\<T>](https://go.microsoft.com/fwlink/p/?LinkId=251132) do Windows Runtime.  
  
## <a name="see-also"></a>Consulte também

- [Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Criando componentes do Windows Runtime no C# e no Visual Basic](https://go.microsoft.com/fwlink/p/?LinkID=238313)
- [Mensagens de erro do winmdexp.exe](../../../docs/framework/tools/winmdexp-exe-error-messages.md)
- [Ferramentas de build, implantação e configuração (.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
