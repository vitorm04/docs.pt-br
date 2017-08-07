---
title: "Opções do compilador de C# listadas por categoria"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bf0b4a4130fe69a15e6db438ac1d58b676c9ee8b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="c-compiler-options-listed-by-category"></a>Opções do compilador de C# listadas por categoria
As opções do compilador a seguir são classificadas por categoria. Para obter uma lista alfabética, consulte [Opções do compilador C# listadas em ordem alfabética](../../../csharp/language-reference/compiler-options/listed-alphabetically.md).  
  
### <a name="optimization"></a>Otimização  
  
|Opção|Finalidade|  
|------------|-------------|  
|[/filealign](../../../csharp/language-reference/compiler-options/filealign-compiler-option.md)|Especifica o tamanho das seções no arquivo de saída.|  
|[/optimize](../../../csharp/language-reference/compiler-options/optimize-compiler-option.md)|Habilita/desabilita otimizações.|  
  
### <a name="output-files"></a>Arquivos de saída  
  
|Opção|Finalidade|  
|------------|-------------|  
|[/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)|Especifica um arquivo XML em que os comentários da documentação processados devem ser gravados.|  
|[/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md)|Especifica o arquivo de saída.|  
|[/pdb](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)|Especifica o nome de arquivo e a localização do arquivo .pdb.|  
|[/platform](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)|Especifique a plataforma de saída.|  
|[/preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Especifique uma linguagem para a saída do compilador.|  
|[/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md)|Especifica o formato do arquivo de saída usando uma das cinco opções: [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md), [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md), [/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md), [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) ou [/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md).|  
|/modulename:\<string>|Especificar o nome do módulo de origem|  
  
### <a name="net-framework-assemblies"></a>Assemblies do .NET Framework  
  
|Opção|Finalidade|  
|------------|-------------|  
|[/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md)|Especifica um ou mais módulos para fazerem parte deste assembly.|  
|[/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)|Instrui o compilador a adicionar a chave pública, mas a deixar o assembly não assinado.|  
|[/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md)|Especifica o nome do contêiner da chave de criptografia.|  
|[/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)|Especifica o nome de arquivo que contém a chave de criptografia.|  
|[/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)|Especifica o local dos assemblies referenciados por meio de [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).|  
|[/nostdlib](../../../csharp/language-reference/compiler-options/nostdlib-compiler-option.md)|Instrui o compilador a não importar a biblioteca padrão (mscorlib.dll).|  
|[/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)|Importa metadados de um arquivo que contém um assembly.|  
|/analyzer|Executar os analisadores com basse nesse assembly (forma abreviada: /a)|  
|/additionalfile|Nomeia outros arquivos que não afetam diretamente a geração de código, mas podem ser usados por analisadores para produzir erros ou avisos.|  
  
### <a name="debuggingerror-checking"></a>Verificação de depuração/erros  
  
|Opção|Finalidade|  
|------------|-------------|  
|[/bugreport](../../../csharp/language-reference/compiler-options/bugreport-compiler-option.md)|Cria um arquivo que contém informações que tornam mais fácil relatar um bug.|  
|[/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md)|Especifica se o aritmético inteiro que estoura os limites do tipo de dados causará uma exceção em tempo de execução.|  
|[/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md)|Instrua o compilador a emitir informações de depuração.|  
|[/errorreport](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)|Define o comportamento de relatório de erros.|  
|[/fullpaths](../../../csharp/language-reference/compiler-options/fullpaths-compiler-option.md)|Especifica o caminho absoluto para o arquivo na saída do compilador.|  
|[/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md)|Suprime a geração de avisos especificados do compilador.|  
|[/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md)|Define o nível de aviso.|  
|[/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)|Promove avisos a erros.|  
|/ruleset:\<file>|Especifique um arquivo de conjunto de regras que desabilita o diagnóstico específico.|  
  
### <a name="preprocessor"></a>Pré-processador  
  
|Opção|Finalidade|  
|------------|-------------|  
|[/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md)|Define símbolos do pré-processador.|  
  
### <a name="resources"></a>Recursos  
  
|Opção|Finalidade|  
|------------|-------------|  
|[/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md)|Disponibiliza informações de tipo COM em assemblies especificados para o projeto.|  
|[/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)|Cria um link a um recurso gerenciado.|  
|[/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)|Insere um recurso do .NET Framework no arquivo de saída.|  
|[/win32icon](../../../csharp/language-reference/compiler-options/win32icon-compiler-option.md)|Especifica um arquivo .ico a ser inserido no arquivo de saída.|  
|[/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md)|Especifica um recurso Win32 a ser inserido no arquivo de saída.|  
  
### <a name="miscellaneous"></a>Diversos  
  
|Opção|Finalidade|  
|------------|-------------|  
|[@](../../../csharp/language-reference/compiler-options/response-file-compiler-option.md)|Especifica um arquivo de resposta.|  
|[/?](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Lista as opções de compilador para stdout.|  
|[/baseaddress](../../../csharp/language-reference/compiler-options/baseaddress-compiler-option.md)|Especifica o endereço básico preferencial no qual uma DLL será carregada.|  
|[/codepage](../../../csharp/language-reference/compiler-options/codepage-compiler-option.md)|Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.|  
|[/help](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Lista as opções de compilador para stdout.|  
|[/highentropyva](../../../csharp/language-reference/compiler-options/highentropyva-compiler-option.md)|Especifica que o arquivo executável dá suporte a uma ASLR (Address Space Layout Randomization).|  
|[/langversion](../../../csharp/language-reference/compiler-options/langversion-compiler-option.md)|Especifique o modo de versão da linguagem: Padrão, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1 ou Mais recente |  
|[/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md)|Especifica a localização do método **Principal**.|  
|[/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)|Instrui o compilador a não compilar com o csc.rsp.|  
|[/nologo](../../../csharp/language-reference/compiler-options/nologo-compiler-option.md)|Suprime as informações da faixa do compilador.|  
|[/recurse](../../../csharp/language-reference/compiler-options/recurse-compiler-option.md)|Pesquisa em subdiretórios arquivos de código-fonte a serem compilados.|  
|[/subsystemversion](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)|Especifica a versão mínima do subsistema que o arquivo executável pode usar.|  
|[/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)|Habilita a compilação de código que usa a palavra-chave [unsafe](../../../csharp/language-reference/keywords/unsafe.md).|  
|[/utf8output](../../../csharp/language-reference/compiler-options/utf8output-compiler-option.md)|Exibe a saída do compilador usando a codificação UTF-8.|  
|/parallel[+&#124;-]|Especifica se deve o build simultâneo deve ser usado (+).|  
|/checksumalgorithm:\<alg>|Especifique o algoritmo para calcular a soma de verificação do arquivo de origem armazenada no PDB.  Os valores com suporte são: SHA1 (padrão) ou SHA256.|  
  
## <a name="obsolete-options"></a>Opções obsoletas  
  
|Opção|Finalidade|  
|---|---|  
|/incremental|Habilita a compilação incremental.|  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Opções do compilador C# listadas em ordem alfabética](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)   
 [Como configurar variáveis de ambiente para a linha de comando do Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)

