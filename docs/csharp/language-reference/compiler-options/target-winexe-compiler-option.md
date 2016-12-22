---
title: "/target:winexe (C# Compiler Options) | Microsoft Docs"
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
  - "/target:winexe"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/target compiler options [C#], /target:winexe"
  - "-target compiler options [C#], /target:winexe"
  - "target compiler options [C#], /target:winexe"
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:winexe (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/target:winexe** faz com que o compilador cria um executável \(EXE\), programa do windows.  
  
## Sintaxe  
  
```  
/target:winexe  
```  
  
## Comentários  
 O arquivo executável será criado com a extensão de arquivo.  Um programa do windows é um que fornece uma interface de usuário da biblioteca do.NET Framework ou por meio de APIs Win32.  
  
 Use [\/target: exe](../Topic/-target:exe%20\(C%23%20Compiler%20Options\).md) para criar um aplicativo de console.  
  
 Salvo indicação em contrário com a opção de [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) , o nome do arquivo de saída tem o nome do arquivo de entrada que contém o método de [Principal](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) .  
  
 Quando especificados na linha de comando, todos os arquivos que **\/out** próximo ou a opção de [\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) são usados para criar o programa do windows.  
  
 Um e apenas um desses métodos de **Principal** são necessários em arquivos de origem que são criados em um arquivo .exe.  A opção de [\/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) permite especificar que a classe contém o método de **Principal** , nos casos em que o código tem mais de uma classe com um método de **Principal** .  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Clique na página de propriedades de **Aplicativo** .  
  
3.  Modifique a propriedade de **Tipo de Saída** .  
  
 Para obter informações sobre como definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## Exemplo  
 Criar `in.cs` em um programa do windows:  
  
```  
csc /target:winexe in.cs  
```  
  
## Consulte também  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)