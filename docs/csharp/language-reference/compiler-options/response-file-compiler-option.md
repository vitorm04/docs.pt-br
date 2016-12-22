---
title: "@ (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "@"
dev_langs: 
  - "CSharp"
  - "CSharp"
helpviewer_keywords: 
  - "response files, specifying for compilation [C#]"
  - "@ compiler option"
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# @ (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção @ permite especificar um arquivo que contém opções e arquivo de código\-fonte do compilador criar.  
  
## Sintaxe  
  
```  
@response_file  
```  
  
## Arguments  
 `response_file`  
 Um arquivo que lista as opções ou arquivo de origem do compilador criar.  
  
## Comentários  
 As opções e os arquivos de código\-fonte do compilador serão processados pelo compilador como se tivesse sido especificadas na linha de comando.  
  
 Para especificar mais de um arquivo de resposta em uma compilação, especificar várias opções de arquivo de resposta.  Por exemplo:  
  
```  
@file1.rsp @file2.rsp  
```  
  
 Em um arquivo de resposta, várias opções e os arquivos de código\-fonte do compilador podem aparecer em uma linha.  Uma única especificação da opção do compilador deve aparecer em uma linha \(não pode abranger várias linhas\).  Os arquivos de resposta podem ter os comentários que começam com \# símbolo.  
  
 Especifique opções do compilador do arquivo de resposta é exatamente como emita os comandos na linha de comando.  Consulte [Criar de linha de comando](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) para obter mais informações.  
  
 O compilador processa as opções de comando a medida que são encontrados.  Consequentemente, os argumentos de linha de comando podem substituir as opções listadas anteriormente em arquivos de resposta.  Por outro lado, as opções em um arquivo de resposta substituirão as opções listadas anteriormente na linha de comando ou em outros arquivos de resposta.  
  
 O fornece o arquivo de csc.rsp, que está localizado no mesmo diretório do arquivo de csc.exe.  Consulte [\/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) para obter mais informações sobre como csc.rsp.  
  
 Essa opção de compilador não pode ser definida no ambiente de desenvolvimento do Visual Studio, nem pode ser modificada programaticamente.  
  
## Exemplo  
 A seguir estão algumas linhas de um arquivo de exemplo de resposta:  
  
```  
# build the first output file  
/target:exe /out:MyExe.exe source1.cs source2.cs  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)