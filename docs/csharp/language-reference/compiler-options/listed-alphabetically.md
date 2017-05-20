---
title: "Opções do Compilador de C# Listadas em Ordem Alfabética | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- compiler options [C#], listed alpabetically
- C# language, compiler options listed alphabitically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
caps.latest.revision: 25
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 91582d214c2f8a72d383a0ac17e409167fda5065
ms.contentlocale: pt-br
ms.lasthandoff: 05/10/2017

---
# <a name="c-compiler-options-listed-alphabetically"></a>Opções do compilador de C# listadas em ordem alfabética
As opções do compilador a seguir estão em ordem alfabética. Para obter uma lista categórica, consulte [Opções de Compilador de C# Listadas por Categoria](../../../csharp/language-reference/compiler-options/listed-by-category.md).  
  
|Opção|Finalidade|  
|------------|-------------|  
|[@](../../../csharp/language-reference/compiler-options/response-file-compiler-option.md)|Lê um arquivo de resposta para obter mais opções.|  
|[/?](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Exibe uma mensagem de uso para stdout.|  
|`/additionalfile`|Nomeia outros arquivos que não afetam diretamente a geração de código, mas podem ser usados por analisadores para produzir erros ou avisos.|  
|[/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md)|Vincula os módulos especificados nesse assembly|  
|`/analyzer`|Executar os analisadores com basse nesse assembly (forma abreviada: /a)|  
|[/appconfig](../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)|Especifica o local do app.config em tempo de associação do assembly.|  
|[/baseaddress](../../../csharp/language-reference/compiler-options/baseaddress-compiler-option.md)|Especifica o endereço básico para a biblioteca a ser criada.|  
|[/bugreport](../../../csharp/language-reference/compiler-options/bugreport-compiler-option.md)|Cria um arquivo 'Bug Report'. Esse arquivo será enviado junto com informações de falha se for usado com **/errorreport:prompt** ou **/errorreport:send**.|  
|[/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md)|Faz com que o compilador gere verificações de estouro.|  
|`/checksumalgorithm:<alg>`|Especifique o algoritmo para calcular a soma de verificação do arquivo de origem armazenada no PDB.  Os valores com suporte são: SHA1 (padrão) ou SHA256.|  
|[/codepage](../../../csharp/language-reference/compiler-options/codepage-compiler-option.md)|Especifica a página de código a ser usada ao abrir arquivos de origem.|  
|[/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md)|Emite informações de depuração.|  
|[/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md)|Define símbolos de compilação condicional.|  
|[/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)|Atrasa a assinatura do assembly usando somente a parte pública da chave de nome forte.|  
|[/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)|Especifica um arquivo de documentação XML a ser gerado.|  
|[/errorreport](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)|Especifica como tratar erros internos do compilador: prompt, send ou none. O padrão é none.|  
|[/filealign](../../../csharp/language-reference/compiler-options/filealign-compiler-option.md)|Especifica o alinhamento usado em seções de arquivo de saída.|  
|[/fullpaths](../../../csharp/language-reference/compiler-options/fullpaths-compiler-option.md)|Faz com que o compilador gere caminhos totalmente qualificados.|  
|[/help](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Exibe uma mensagem de uso para stdout.|  
|[/highentropyva](../../../csharp/language-reference/compiler-options/highentropyva-compiler-option.md)|Especifica que há suporte para ASLR de alta entropia.|  
|**/incremental**|Habilita a compilação incremental [obsoleta].|  
|[/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md)|Especifica um contêiner de chave de nome forte.|  
|[/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)|Especifica um arquivo de chave de nome forte.|  
|[/langversion:\<string>](../../../csharp/language-reference/compiler-options/langversion-compiler-option.md)|Especifique o modo de versão da linguagem: ISO-1, ISO-2, 3, 4, 5, 6 ou padrão|  
|[/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)|Especifica diretórios adicionais para pesquisar referências.|  
|[/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md)|Disponibiliza informações de tipo COM em assemblies especificados para o projeto.|  
|[/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)|Vincula o recurso especificado a esse assembly.|  
|[/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md)|Especifica o tipo que contém o ponto de entrada (ignorar todos os outros pontos de entrada possíveis).|  
|[/moduleassemblyname](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)|Especifica um assembly cujos tipos não públicos podem ser acessados por um .netmodule.|  
|`/modulename:<string>`|Especificar o nome do módulo de origem|  
|[/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)|Instrui o compilador a não incluir automaticamente o arquivo CSC.RSP.|  
|[/nologo](../../../csharp/language-reference/compiler-options/nologo-compiler-option.md)|Suprime a mensagem de direitos autorais do compilador.|  
|[/nostdlib](../../../csharp/language-reference/compiler-options/nostdlib-compiler-option.md)|Instrui o compilador a não referenciar a biblioteca padrão (mscorlib.dll).|  
|[/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md)|Desabilita mensagens de aviso específicas|  
|[/nowin32manifest](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)|Instrui o compilador não inserir um manifesto de aplicativo no arquivo executável.|  
|[/optimize](../../../csharp/language-reference/compiler-options/optimize-compiler-option.md)|Habilita/desabilita otimizações.|  
|[/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md)|Especifica o nome do arquivo de saída (padrão: nome base do arquivo com classe main ou primeiro arquivo).|  
|`/parallel[+&#124;-]`|Especifica se deve o build simultâneo deve ser usado (+).|  
|[/pdb](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)|Especifica o nome de arquivo e a localização do arquivo .pdb.|  
|[/platform](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)|Limita as plataformas em que este código pode ser executado: x86, Itanium, x64, anycpu ou anycpu32bitpreferred. O padrão é anycpu.|  
|[/preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Especifica o idioma a ser usado para a saída do compilador.|  
|[/recurse](../../../csharp/language-reference/compiler-options/recurse-compiler-option.md)|Inclui todos os arquivos no diretório e subdiretórios atuais de acordo com as especificações curinga.|  
|[/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)|Referencia metadados dos arquivos do assembly especificado.|  
|[/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)|Insere o recurso especificado.|  
|`/ruleset:<file>`|Especifique um arquivo de conjunto de regras que desabilita o diagnóstico específico.|  
|[/subsystemversion](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)|Especifica a versão mínima do subsistema que o arquivo executável pode usar.|  
|[/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md)|Especifica o formato do arquivo de saída usando uma das quatro opções: [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md), [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md), [/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md), [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md), [/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md).|  
|[/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)|Permite o código [não seguro](../../../csharp/language-reference/keywords/unsafe.md).|  
|[/utf8output](../../../csharp/language-reference/compiler-options/utf8output-compiler-option.md)|Produz mensagens do compilador em codificação UTF-8.|  
|[/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md)|Define o nível de aviso (0-4).|  
|[/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)|Relata avisos específicos como erros.|  
|[/win32icon](../../../csharp/language-reference/compiler-options/win32icon-compiler-option.md)|Usa este ícone para saída.|  
|[/win32manifest](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)|Especifica um arquivo de manifesto win32 personalizado.|  
|[/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md)|Especifica um arquivo de recurso win32 (.res).|  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Opções do Compilador do C# Listadas por Categoria](../../../csharp/language-reference/compiler-options/listed-by-category.md)   
 [Como Configurar Variáveis de Ambiente para a Linha de Comando do Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)   
 [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
