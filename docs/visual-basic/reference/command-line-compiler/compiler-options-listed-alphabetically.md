---
title: "Opções de compilador do Visual Basic listadas em ordem alfabética | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 93246b3a38002955234a7a93529d05b71ab4e580
ms.lasthandoff: 03/13/2017

---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Opções de compilador do Visual Basic listadas em ordem alfabética
O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador de linha de comando é fornecido como uma alternativa para compilar programas de [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE). A seguir está uma lista da [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] classificadas em ordem alfabética de opções do compilador de linha de comando.  
  
|Opção|Finalidade|  
|------------|-------------|  
|[Em (Especificar arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Especifica um arquivo de resposta.|  
|[/?](../../../visual-basic/reference/command-line-compiler/help.md)|Exibe opções do compilador. Esse comando é o mesmo que especificar o `/help` opção. Nenhuma compilação ocorre.|  
|`/additionalfile`|Nomes de arquivos adicionais que não afetam diretamente a geração de código, mas podem ser usados por analisadores para produzir erros ou avisos.|  
|[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Faz com que o compilador verifique todos os tipos de informações de arquivos especificados disponíveis para o projeto que você está compilando.|  
|`/analyzer`|Executar os analisadores desse assembly (forma abreviada: / a)|  
|[/baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Especifica o endereço base de uma DLL.|  
|[/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Cria um arquivo que contém informações que torna mais fácil relatar um bug.|  
|`/checksumalgorithm:<alg>`|Especifique o algoritmo para calcular a soma de verificação de arquivo de origem armazenada no PDB.  Valores com suporte são: SHA1 (padrão) ou SHA256.|  
|[/codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.|  
|[/debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Gera informações de depuração.|  
|[/define](../../../visual-basic/reference/command-line-compiler/define.md)|Define símbolos de compilação condicional.|  
|[/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Especifica se o assembly será assinado total ou parcialmente.|  
|[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Processa comentários de documentação para um arquivo XML.|  
|[/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Especifica como o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador deve relatar erros do compilador interno.|  
|[/filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Especifica onde a alinhar as seções do arquivo de saída.|  
|[/Help](../../../visual-basic/reference/command-line-compiler/help.md)|Exibe opções do compilador. Esse comando é o mesmo que especificar o `/?` opção. Nenhuma compilação ocorre.|  
|[/highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Indica se um determinado executável suporta alta entropia endereço espaço Layout aleatória (ASLR).|  
|[/imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importa um namespace de um assembly especificado.|  
|[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Especifica um nome de contêiner de chave para um par de chaves dar um nome forte de um assembly.|  
|[/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Especifica um arquivo que contém uma chave ou par de chaves para dar um nome forte de um assembly.|  
|[/langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Especificar a versão de idioma: 9 | 9.0 | 10 | 10.0 | 11 | 11.0.|  
|[/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Especifica o local dos assemblies referenciados pelo [/Reference](../../../visual-basic/reference/command-line-compiler/reference.md) opção.|  
|[/linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Cria um link a um recurso gerenciado.|  
|[/main](../../../visual-basic/reference/command-line-compiler/main.md)|Especifica a classe que contém o `Sub``Main` procedimento a ser usado na inicialização.|  
|[/moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Especifica o nome do assembly que um módulo será uma parte.|  
|`/modulename:<string>`|Especifique o nome do módulo de origem|  
|[/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Define o compilador como destino o [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].|  
|[/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Não compile com Vbc.|  
|[/nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Suprime as informações de faixa de compilador.|  
|[/nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Faz com que o compilador não referencie as bibliotecas padrão.|  
|[/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Suprime a capacidade do compilador para gerar avisos.|  
|[/nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Instrui o compilador não incorporar nenhum manifesto do aplicativo para o arquivo executável.|  
|[/optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Habilita/desabilita a otimização de código.|  
|[/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Especifica se as comparações de cadeia de caracteres devem ser binário ou usar semântica de texto específica de localidade.|  
|[/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Aplica a declaração explícita de variáveis.|  
|[/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Permite o uso de inferência de tipo local nas declarações de variáveis.|  
|[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Impõe semântica de linguagem estrita.|  
|[/out](../../../visual-basic/reference/command-line-compiler/out.md)|Especifica um arquivo de saída.|  
|`/parallel[+&#124;-]`|Especifica se deve usar compilação simultânea (+).|  
|[/platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Especifica a plataforma do processador as metas do compilador para o arquivo de saída.|  
|`/preferreduilang`|Especifique o nome do idioma de saída preferencial.|  
|[/quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Impede que o compilador de mostrar código para erros relacionados à sintaxe e avisos.|  
|[/recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Pesquisa subdiretórios arquivos de código-fonte compilar.|  
|[/reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importa os metadados de um assembly.|  
|[/removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Desabilita a verificação de estouro de inteiro.|  
|[/resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Insere um recurso gerenciado em um assembly.|  
|[/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Especifica um namespace para todas as declarações de tipo.|  
|`/ruleset:<file>`|Especifique um arquivo de conjunto de regras que desabilita o diagnóstico específico.|  
|[/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Especifica o local de mscorlib. dll e Microsoft.VisualBasic.dll.|  
|[/subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|Especifica a versão mínima do subsistema que o arquivo executável gerado pode usar.|  
|[/target](../../../visual-basic/reference/command-line-compiler/target.md)|Especifica o formato do arquivo de saída.|  
|[/utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Exibe a saída do compilador usando a codificação UTF-8.|  
|[/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Especifica que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic ou com uma referência a uma biblioteca de tempo de execução específico.|  
|[/verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Gera informações extras durante a compilação.|  
|[/warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Promove a avisos de erros.|  
|[/win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Insere um arquivo. ico no arquivo de saída.|  
|[/win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identifica um definido pelo usuário aplicativo arquivo de manifesto Win32 a ser inserido no arquivo PE (portable executable) de um projeto.|  
|[/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Insere um recurso do Win32 no arquivo de saída.|  
  
## <a name="see-also"></a>Consulte também  
 [Opções de compilador do Visual Basic listadas por categoria](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)   
 [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)   
 [Opções do compilador c# listadas em ordem alfabética](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)   
 [Opções do compilador de C# listadas por categoria](../../../csharp/language-reference/compiler-options/listed-by-category.md)
