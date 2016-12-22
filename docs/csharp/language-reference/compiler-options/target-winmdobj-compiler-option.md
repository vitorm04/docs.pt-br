---
title: "/target:winmdobj (op&#231;&#245;es do compilador C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:winmdobj (op&#231;&#245;es do compilador C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Se você usar a opção de compilador **\/target:winmdobj**, o compilador criará um arquivo .winmdobj intermediário que você pode converter em um arquivo binário de Tempo de Execução do Windows \(.winmd\).  O arquivo .winmd pode ser consumido por programas de JavaScript e do C\+\+, além de programas de linguagem gerenciada.  
  
## Sintaxe  
  
```  
/target:winmdobj  
```  
  
## Comentários  
 A configuração **winmdobj** indica para o compilador que um módulo intermediário é necessário.  Em resposta, o Visual Studio compila a biblioteca de classes de C\# como um arquivo .winmdobj.  O arquivo .winmdobj pode então ser passado através da ferramenta de exportação de <xref:Microsoft.Build.Tasks.WinMDExp> para gerar um arquivo de metadados do Windows \(.winmd\).  O arquivo .winmd contém o código da biblioteca original e os metadados de WinMD que são usados pelo JavaScript ou C\+\+, e pelo Tempo de Execução do Windows.  
  
 A saída de um arquivo compilado usando a opção de compilador **\/target:winmdobj** é criada para ser usada somente como entrada para a ferramenta de exportação de WimMDExp; o próprio arquivo .winmdobj não é referenciado diretamente.  
  
 A menos que você use a opção [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), o nome do arquivo de saída leva o nome do primeiro arquivo de entrada.  Um método [Principal](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) não é necessário.  
  
 Se você especificar a opção \/target:winmdobj em um prompt de comando, todos os arquivos até o próxima opção **\/out** ou [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) serão usados para criar o programa do Windows.  
  
### Para definir esta opção de compilador no IDE do Visual Studio para um aplicativo da Windows Store  
  
1.  No **Gerenciador de Soluções**, abra o menu de atalho do projeto, e escolha **Propriedades**.  
  
2.  Escolha a guia **Aplicativo**.  
  
3.  Na lista de **Tipo de Saída**, escolha **Arquivo WinMD**.  
  
     A opção **Arquivo WinMD** está disponível apenas para os modelos de aplicativo de [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)].  
  
 Para obter informações sobre como configurar esta opção do compilador programaticamente, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## Exemplo  
 O comando a seguir compila `filename.cs` em um arquivo .winmdobj intermediário.  
  
```  
csc /target:winmdobj filename.cs  
```  
  
## Consulte também  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)