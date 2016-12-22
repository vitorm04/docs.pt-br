---
title: "/target:appcontainerexe (op&#231;&#245;es do compilador C#) | Microsoft Docs"
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
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:appcontainerexe (op&#231;&#245;es do compilador C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Se você usar a opção de compilador **\/target:appcontainerexe**, o compilador criará um arquivo executável do Windows \(.exe\) que deve ser executado em um recipiente de aplicativo.  Essa opção é equivalente a [\/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md), mas destina\-se aos aplicativos do [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)].  
  
## Sintaxe  
  
```  
/target:appcontainerexe  
```  
  
## Comentários  
 Para exigir que o aplicativo seja executado em um recipiente de aplicativo, esta opção define um bit no arquivo [Executável portátil](http://go.microsoft.com/fwlink/p/?LinkId=236960) \(PE\).  Quando o bit for definido, um erro ocorrerá se o método CreateProcess tentar iniciar o arquivo executável fora de um contêiner do aplicativo.  
  
 A menos que você use a opção [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), o nome do arquivo de saída leva o nome do arquivo de entrada que contém o método [Principal](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md).  
  
 Ao especificar esta opção em um prompt de comando, todos os arquivos até a próxima opção de **\/out** ou de **\/target** serão usados para criar o arquivo executável.  
  
### Para definir esta opção do compilador no IDE  
  
1.  No **Gerenciador de Soluções**, abra o menu de atalho do projeto, e escolha **Propriedades**.  
  
2.  Na guia **Aplicativo**, na lista de **Tipo de Saída**, escolha **Aplicativo da Windows Store**.  
  
     Esta opção está disponível somente para modelos de aplicativo do [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)].  
  
 Para obter informações sobre como configurar esta opção do compilador programaticamente, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## Exemplo  
 O comando a seguir compila `filename.cs` em um arquivo executável do Windows que pode ser executado somente em um recipiente de aplicativo.  
  
```  
csc /target:appcontainerexe filename.cs  
```  
  
## Consulte também  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [\/target:winexe \(Create a Windows Program\)](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)