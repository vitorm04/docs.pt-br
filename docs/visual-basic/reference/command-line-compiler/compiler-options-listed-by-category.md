---
title: Opções de compilador listadas por categoria
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: 8b6c142041024e672fe42c8c6f2d3ebe7b07cd65
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344803"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Visual Basic opções de compilador listadas por categoria
O compilador de linha de comando Visual Basic é fornecido como uma alternativa à compilação de programas de dentro do ambiente de desenvolvimento integrado (IDE) do Visual Studio. Veja a seguir uma lista de Visual Basic opções do compilador de linha de comando classificadas por categoria funcional.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Saída do compilador  
  
|Opção|Finalidade|  
|---|---|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Suprime as informações da faixa do compilador.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Exibe a saída do compilador usando a codificação UTF-8.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Gera informações extras durante a compilação.|  
|`-modulename:<string>`|Especificar o nome do módulo de origem|  
|[/preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Especifique uma linguagem para a saída do compilador.|
  
## <a name="optimization"></a>Otimização  
  
|Opção|Finalidade|  
|---|---|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Especifica onde alinhar as seções do arquivo de saída.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Habilita/desabilita otimizações.|  
  
## <a name="output-files"></a>Arquivos de saída  
  
|Opção|Finalidade|  
|---|---|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Processa comentários de documentação em um arquivo XML.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Faz com que o compilador gere um assembly de conteúdo binário idêntico entre compilações se as entradas são idênticas.|
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Define o compilador para o .NET Compact Framework de destino.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Especifica um arquivo de saída.|  
|[/refonly](refonly-compiler-option.md)|Gera apenas um assembly de referência.|
|[/refout](refout-compiler-option.md)|Especifica o caminho de saída de um assembly de referência.|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Especifica o formato da saída.|  
  
## <a name="net-assemblies"></a>Assemblies .NET  
  
|Opção|Finalidade|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Faz com que o compilador verifique todos os tipos de informações de arquivos especificados disponíveis para o projeto que você está compilando.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Especifica se o assembly será assinado total ou parcialmente.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importa um namespace de um assembly especificado.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Especifica um nome de contêiner de chave para um par de chaves para dar a um assembly um nome forte.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Especifica um arquivo que contém uma chave ou um par de chaves para fornecer um nome forte ao assembly.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Especifica o local dos assemblies referenciados pela opção [-Reference](../../../visual-basic/reference/command-line-compiler/reference.md) .|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importa metadados de um assembly.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Especifica o nome do assembly do qual um módulo fará parte.|  
|`-analyzer`|Executar os analisadores com basse nesse assembly (forma abreviada: -a)|  
|`-additionalfile`|Nomeia outros arquivos que não afetam diretamente a geração de código, mas podem ser usados por analisadores para produzir erros ou avisos.|  
  
## <a name="debuggingerror-checking"></a>Depuração/verificação de erros  
  
|Opção|Finalidade|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Cria um arquivo que contém informações que tornam mais fácil relatar um bug.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Produz informações de depuração.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Suprime a capacidade do compilador de gerar avisos.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Impede que o compilador exiba código para erros e avisos relacionados à sintaxe.|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Desabilita a verificação de estouro de inteiros.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Promove avisos a erros.|  
|`-ruleset:<file>`|Especifique um arquivo de conjunto de regras que desabilita o diagnóstico específico.|  
  
## <a name="help"></a>Ajuda  
  
|Opção|Finalidade|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Exibe as opções do compilador. Esse comando é o mesmo que especificar a opção de `-help`. Nenhuma compilação ocorre.|  
|[ajuda](../../../visual-basic/reference/command-line-compiler/help.md)|Exibe as opções do compilador. Esse comando é o mesmo que especificar a opção de `-?`. Nenhuma compilação ocorre.|  
  
## <a name="language"></a>Linguagem  
  
|Opção|Finalidade|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Especifique a versão do idioma&#124;:&#124;9&#124;9,0&#124;10&#124;10,0 11 11,0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Impõe uma declaração explícita de variáveis.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Impõe semântica de tipo estrito.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Especifica se as comparações de cadeia de caracteres devem ser binárias ou usar a semântica de texto específica à localidade.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Permite o uso de inferência de tipo local nas declarações de variáveis.|  
  
## <a name="preprocessor"></a>Pré-processador  
  
|Opção|Finalidade|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Define os símbolos para a compilação condicional.|  
  
## <a name="resources"></a>Recursos  
  
|Opção|Finalidade|  
|---|---|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Cria um link a um recurso gerenciado.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Insere um recurso gerenciado em um assembly.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Insere um arquivo. ico no arquivo de saída.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Insere um recurso do Win32 no arquivo de saída.|  
  
## <a name="miscellaneous"></a>Diversos  
  
|Opção|Finalidade|  
|---|---|  
|[Em (Especificar arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Especifica um arquivo de resposta.|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Especifica o endereço base de uma DLL.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Especifica como o compilador de Visual Basic deve relatar erros internos do compilador.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Informa ao kernel do Windows se um executável específico dá suporte a alta (randomização de layout de espaço de endereço) de entropia.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Especifica a classe que contém o procedimento de `Sub Main` a ser usado na inicialização.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Não compilar com Vbc. rsp|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Faz com que o compilador não referencie as bibliotecas padrão.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Instrui o compilador a não inserir nenhum manifesto de aplicativo no arquivo executável.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Especifica a plataforma do processador que o compilador tem como destino para o arquivo de saída.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Pesquisa em subdiretórios arquivos de código-fonte a serem compilados.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Especifica um namespace para todas as declarações de tipo.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Especifica o local de mscorlib. dll e Microsoft. VisualBasic. dll.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Especifica que o compilador deve compilar sem uma referência para a biblioteca de tempo de execução Visual Basic ou com uma referência a uma biblioteca de tempo de execução específica.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identifica um arquivo de manifesto do aplicativo Win32 definido pelo usuário para ser inserido no arquivo executável portátil (PE) de um projeto.|  
|`-parallel[+&#124;-]`|Especifica se deve o build simultâneo deve ser usado (+).|  
|`-checksumalgorithm:<alg>`|Especifique o algoritmo para calcular a soma de verificação do arquivo de origem armazenada no PDB.  Os valores com suporte são: SHA1 (padrão) ou SHA256. <br>Devido a problemas de colisão com o SHA1, a Microsoft recomenda SHA256 ou melhor.|  
  
## <a name="see-also"></a>Consulte também

- [Opções do compilador do Visual Basic listadas em ordem alfabética](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)
- [Gerenciar propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
