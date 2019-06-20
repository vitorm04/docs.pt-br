---
title: Opções de compilador do Visual Basic listadas por categoria
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: b945edca8bd739e6f122ed8b3e950508ecc28510
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268170"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Opções de compilador do Visual Basic listadas por categoria
O compilador de linha de comando do Visual Basic é fornecido como uma alternativa para compilar programas de dentro do ambiente de desenvolvimento integrado (IDE) do Visual Studio. O exemplo a seguir é uma lista das opções de linha de comando do compilador Visual Basic classificadas por categoria funcional.  

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
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Define o compilador para ter como destino o .NET Compact Framework.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Especifica um arquivo de saída.|  
|[/refonly](refonly-compiler-option.md)|Gera apenas um assembly de referência.|
|[/refout](refout-compiler-option.md)|Especifica o caminho de saída de um assembly de referência.|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Especifica o formato da saída.|  
  
## <a name="net-assemblies"></a>Assemblies do .NET  
  
|Opção|Finalidade|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Faz com que o compilador verifique todos os tipos de informações de arquivos especificados disponíveis para o projeto que você está compilando.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Especifica se o assembly será assinado total ou parcialmente.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importa um namespace de um assembly especificado.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Especifica um nome de contêiner de chave para um par de chaves dar um nome forte de um assembly.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Especifica um arquivo que contém uma chave ou par de chaves para dar um nome forte de um assembly.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Especifica o local dos assemblies referenciados pelo [-referência](../../../visual-basic/reference/command-line-compiler/reference.md) opção.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importa os metadados de um assembly.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Especifica o nome do assembly que um módulo fará parte do.|  
|`-analyzer`|Executar os analisadores com basse nesse assembly (forma abreviada: -a)|  
|`-additionalfile`|Nomeia outros arquivos que não afetam diretamente a geração de código, mas podem ser usados por analisadores para produzir erros ou avisos.|  
  
## <a name="debuggingerror-checking"></a>Verificação de depuração/erros  
  
|Opção|Finalidade|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Cria um arquivo que contém informações que tornam mais fácil relatar um bug.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Gera informações de depuração.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Suprime a capacidade do compilador para gerar avisos.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Impede que o compilador exibindo o código para avisos e erros de sintaxe.|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Desabilita a verificação de estouro de inteiro.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Promove avisos a erros.|  
|`-ruleset:<file>`|Especifique um arquivo de conjunto de regras que desabilita o diagnóstico específico.|  
  
## <a name="help"></a>Ajuda  
  
|Opção|Finalidade|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Exibe as opções do compilador. Esse comando é o mesmo que especificar o `-help` opção. Nenhuma compilação ocorre.|  
|[ajuda](../../../visual-basic/reference/command-line-compiler/help.md)|Exibe as opções do compilador. Esse comando é o mesmo que especificar o `-?` opção. Nenhuma compilação ocorre.|  
  
## <a name="language"></a>Idioma  
  
|Opção|Finalidade|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Especificar a versão do idioma: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Impõe a declaração explícita de variáveis.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Impõe semântica de tipo estrito.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Especifica se as comparações de cadeia de caracteres devem ser binário ou usam a semântica de texto específica de localidade.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Permite o uso de inferência de tipo local nas declarações de variáveis.|  
  
## <a name="preprocessor"></a>Pré-processador  
  
|Opção|Finalidade|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Define símbolos de compilação condicional.|  
  
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
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Especifica o endereço básico de uma DLL.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Especifica como o compilador do Visual Basic deve relatar erros internos do compilador.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Informa ao kernel do Windows se um determinado executável dá suporte a randomização de Layout do espaço de endereço (ASLR) de alta entropia.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Especifica a classe que contém o `Sub Main` procedimento a ser usado na inicialização.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Não são compilados com Vbc|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Faz com que o compilador não referencie as bibliotecas padrão.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Instrui o compilador a não inserir nenhum manifesto de aplicativo no arquivo executável.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Especifica a plataforma de processador as metas de compilador para o arquivo de saída.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Pesquisa em subdiretórios arquivos de código-fonte a serem compilados.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Especifica um namespace para todas as declarações de tipo.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Especifica o local de mscorlib. dll e VisualBasic.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Especifica que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic, ou com uma referência a uma biblioteca de tempo de execução específico.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identifica um definidos pelo usuário aplicativo arquivo manifesto Win32 a ser inserido no arquivo PE (executável portátil) de um projeto.|  
|`-parallel[+&#124;-]`|Especifica se deve o build simultâneo deve ser usado (+).|  
|`-checksumalgorithm:<alg>`|Especifique o algoritmo para calcular a soma de verificação do arquivo de origem armazenada no PDB.  Os valores compatíveis são: SHA1 (padrão) ou SHA256.|  
  
## <a name="see-also"></a>Consulte também

- [Opções do compilador do Visual Basic listadas em ordem alfabética](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)
- [Gerenciar propriedades do projeto e da solução](/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017)
