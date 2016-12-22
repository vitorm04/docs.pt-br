---
title: "/main (C# Compiler Options) | Microsoft Docs"
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
  - "/main"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-main compiler option [C#]"
  - "main compiler option [C#]"
  - "/main compiler option [C#]"
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /main (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Essa opção especifica a classe que contém o ponto de entrada para o programa, se mais de uma classe contém um método de **Principal** .  
  
## Sintaxe  
  
```  
/main:class  
```  
  
## Arguments  
 `class`  
 O tipo que contém o método de **Principal** .  
  
## Comentários  
 Se sua compilação inclui mais de um tipo com um método de [Principal](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) , você pode especificar que o tipo que contém o método de **Principal** que você deseja usar como ponto de entrada no programa.  
  
 Essa opção é para uso durante a criação de um arquivo .exe.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Clique na página de propriedades de **Aplicativo** .  
  
3.  Modifique a propriedade de **Objeto de inicialização** .  
  
     Para definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.  
  
## Exemplo  
 Criar `t2.cs` e `t3.cs`, especificando que o método de **Principal** será encontrada em `Test2`:  
  
```  
csc t2.cs t3.cs /main:Test2  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)