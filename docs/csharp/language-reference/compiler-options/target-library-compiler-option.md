---
title: "/target:library (C# Compiler Options) | Microsoft Docs"
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
  - "/dll"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-target compiler options [C#], /target:library"
  - "target compiler options [C#], /target:library"
  - "/target compiler options [C#], /target:library"
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:library (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/target:library** faz com que o compilador \(DLL\) criar uma biblioteca de vínculo dinâmico\) nativa em vez de um arquivo executável \(EXE\).  
  
## Sintaxe  
  
```  
/target:library  
```  
  
## Comentários  
 A DLL será criado com a extensão .dll de.  
  
 Salvo indicação em contrário com a opção de [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) , o nome do arquivo de saída tem o nome do primeiro arquivo de entrada.  
  
 Quando especificados na linha de comando, todos os arquivos que **\/out** próximo ou a opção de **\/target:module** são usados para criar o arquivo .dll.  
  
 Ao criar um arquivo .dll, um método de [Principal](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) não é necessário.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Clique na página de propriedades de **Aplicativo** .  
  
3.  Modifique a propriedade de **Tipo de Saída** .  
  
 Para obter informações sobre como definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## Exemplo  
 Criar `in.cs`, criando `in.dll`:  
  
```  
csc /target:library in.cs  
```  
  
## Consulte também  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)