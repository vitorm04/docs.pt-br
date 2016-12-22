---
title: "/preferreduilang (C# Compiler Options) | Microsoft Docs"
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
  - "/preferreduilang"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "preferreduilang compiler option [C#]"
  - "/preferreduilang compiler option [C#]"
  - "-preferreduilang compiler option [C#]"
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /preferreduilang (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Usando a opção de compilador de `/preferreduilang` , você pode especificar o idioma no qual o compilador C\# exibe a saída, como mensagens de erro.  
  
## Sintaxe  
  
```  
/preferreduilang: language  
```  
  
## Arguments  
 `language`  
 [nome do idioma](http://go.microsoft.com/fwlink/p/?LinkId=236992) O idioma a ser usado para saída do compilador.  
  
## Comentários  
 Você pode usar a opção do compilador de `/preferreduilang` especificar o idioma desejado o compilador C\# para usar para mensagens de erro e outras saída de linha de comando.  Se o bloco de idioma para o idioma não é instalado, a configuração de idioma de sistema operacional será usado, e nenhum erro for relatado.  
  
```c#  
csc.exe /preferreduilang:ja-JP  
```  
  
## Requisitos  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)