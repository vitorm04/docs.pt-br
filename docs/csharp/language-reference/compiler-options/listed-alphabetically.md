---
title: "C# Compiler Options Listed Alphabetically | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
  - "CSharp"
helpviewer_keywords: 
  - "compiler options [C#], listed alpabetically"
  - "C# language, compiler options listed alphabitically"
  - "Visual C# compiler, options listed alphabetically"
  - "Visual C#, compiler options listed alphabetically"
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# C# Compiler Options Listed Alphabetically
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

As opções do compilador são classificadas em ordem alfabética.  Para obter uma lista categórica, consulte [C\# Compiler Options Listed by Category](../../../csharp/language-reference/compiler-options/listed-by-category.md).  
  
|Opção|Finalidade|  
|-----------|----------------|  
|[@](../../../csharp/language-reference/compiler-options/response-file-compiler-option.md)|Lê um arquivo de resposta para obter mais opções.|  
|[\/?](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Exibe uma mensagem de uso para stdout.|  
|`/additionalfile`|Nomes de arquivos adicionais que não afetam diretamente a geração de código, mas podem ser usados por analisadores para produzir erros ou avisos.|  
|[\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md)|Vincula os módulos especificados neste assembly|  
|`/analyzer`|Executar os analisadores desse assembly \(forma abreviada: \/ a\)|  
|[\/AppConfig](../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)|Especifica o local do App. config em tempo de associação de assembly.|  
|[\/baseaddress](../../../csharp/language-reference/compiler-options/baseaddress-compiler-option.md)|Especifica o endereço base para a biblioteca a ser criada.|  
|[\/bugreport](../../../csharp/language-reference/compiler-options/bugreport-compiler-option.md)|Cria um arquivo 'Bug Report'.  Esse arquivo será enviado junto com qualquer informação de falha se ele for usado com **\/errorreport:prompt** ou **\/errorreport:send**.|  
|[\/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md)|Faz com que o compilador gere a verificação de estouro.|  
|`/checksumalgorithm:<alg>`|Especifique o algoritmo para calcular a soma de verificação de arquivo de origem armazenada no PDB.  Valores com suporte são: SHA1 \(padrão\) ou SHA256.|  
|[\/codepage](../../../csharp/language-reference/compiler-options/codepage-compiler-option.md)|Especifica a página de código a ser utilizada na abertura de arquivos de código fonte.|  
|[\/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md)|Envia informações de depuração.|  
|[\/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md)|Define símbolos de compilação condicional.|  
|[\/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)|Sinais de atraso do assembly usando somente a parte pública da chave de nome forte.|  
|[\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)|Especifica um arquivo de documentação XML para gerar.|  
|[\/errorreport](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)|Especifica como tratar erros do compilador interno: prompt, send ou none.  O padrão é none.|  
|[\/filealign](../../../csharp/language-reference/compiler-options/filealign-compiler-option.md)|Especifica o alinhamento usado para seções do arquivo de saída.|  
|[\/fullpaths](../../../csharp/language-reference/compiler-options/fullpaths-compiler-option.md)|Faz com que o compilador gere caminhos totalmente qualificados.|  
|[\/help](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Exibe uma mensagem de uso para stdout.|  
|[\/highentropyva](../../../csharp/language-reference/compiler-options/highentropyva-compiler-option.md)|Especifica que alta entropia que ASLR é suportado.|  
|**\/incremental**|Habilita a compilação incremental \[obsoleta\].|  
|[\/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md)|Especifica um contêiner de chaves de nome forte.|  
|[\/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)|Especifica um arquivo de chave de nome forte.|  
|[\/langversion: \< string \>](../../../csharp/language-reference/compiler-options/langversion-compiler-option.md)|Especificar modo de versão de linguagem: ISO\-1, ISO\-2, 3, 4, 5, 6 ou padrão|  
|[\/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)|Especifica diretórios adicionais na qual procurar referências.|  
|[\/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md)|Disponibiliza informações de tipo COM em assemblies especificados para o projeto.|  
|[\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)|Vincula o recurso especificado a este assembly.|  
|[\/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md)|Especifica o tipo que contém o ponto de entrada \(ignorar todos os outros pontos de entrada possíveis\).|  
|[\/moduleassemblyname](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)|Especifica um assembly cujos tipos não públicos um.  netmodule pode acessar.|  
|`/modulename:<string>`|Especifique o nome do módulo de origem|  
|[\/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)|Instrui o compilador não automático incluem CSC. Arquivo RSP.|  
|[\/nologo](../../../csharp/language-reference/compiler-options/nologo-compiler-option.md)|Suprime a mensagem de direitos autorais do compilador.|  
|[\/nostdlib](../../../csharp/language-reference/compiler-options/nostdlib-compiler-option.md)|Instrui o compilador não a referência de biblioteca padrão \(mscorlib. dll\).|  
|[\/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md)|Desabilita as mensagens de aviso específicas|  
|[\/nowin32manifest](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)|Instrui o compilador não incorporar um manifesto de aplicativo no arquivo executável.|  
|[\/optimize](../../../csharp/language-reference/compiler-options/optimize-compiler-option.md)|Habilita\/desabilita otimizações.|  
|[\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md)|Especifica o nome do arquivo de saída \(padrão: nome base do arquivo com classe main ou primeiro arquivo\).|  
|`/parallel[+&#124;-]`|Especifica se deve usar a compilação simultânea \(\+\).|  
|[\/pdb](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)|Especifica o nome do arquivo e o local do arquivo. PDB.|  
|[\/platform](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)|Limites de quais plataformas este código pode ser executado: x86, Itanium, x64, anycpu, ou anycpu32bitpreferred.  O padrão é anycpu.|  
|[\/preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Especifica o idioma a ser usado para a saída do compilador.|  
|[\/recurse](../../../csharp/language-reference/compiler-options/recurse-compiler-option.md)|Inclui todos os arquivos no diretório atual e subdiretórios de acordo com as especificações de curinga.|  
|[\/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)|Metadados de referências de arquivos de assembly especificados.|  
|[\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)|Incorpora o recurso especificado.|  
|`/ruleset:<file>`|Especifica um arquivo de conjunto de regras que desabilita o diagnóstico específico.|  
|[\/subsystemversion](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)|Especifica a versão mínima do subsistema que pode usar o arquivo executável.|  
|[\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md)|Especifica o formato do arquivo de saída, usando uma das quatro opções:[\/target: appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md), [\/target: exe](../Topic/-target:exe%20\(C%23%20Compiler%20Options\).md), [: Library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md), [\/target: Module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), [\/target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md),  [\/target: winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md).|  
|[\/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)|Permite [unsafe](../../../csharp/language-reference/keywords/unsafe.md) código.|  
|[\/utf8output](../../../csharp/language-reference/compiler-options/utf8output-compiler-option.md)|Produz mensagens de compilador em codificação UTF\-8.|  
|[\/Warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md)|Define o nível de aviso \(0\-4\).|  
|[\/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)|Relata avisos específicos como erros.|  
|[\/win32icon](../../../csharp/language-reference/compiler-options/win32icon-compiler-option.md)|Usa esse ícone para a saída.|  
|[\/win32manifest](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)|Especifica um arquivo de manifesto win32 personalizado.|  
|[\/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md)|Especifica o arquivo de recurso win32 \(. res\).|  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [C\# Compiler Options Listed by Category](../../../csharp/language-reference/compiler-options/listed-by-category.md)   
 [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)   
 [Elemento \<compiler\>](../Topic/%3Ccompiler%3E%20Element.md)