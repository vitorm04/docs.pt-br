---
title: "/recurse (C# Compiler Options) | Microsoft Docs"
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
  - "/recurse"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/recurse compiler option [C#]"
  - "recurse compiler option [C#]"
  - "-recurse compiler option [C#]"
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /recurse (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção \/recurse permite que você crie arquivo de código\-fonte em todos os diretórios filhos do diretório especificado \(dir\) ou do diretório do projeto.  
  
## Sintaxe  
  
```  
/recurse:[dir\]file  
```  
  
## Arguments  
 `dir` \(opcional\)  
 O diretório no qual você deseja começar a pesquisa.  Se isso não for especificado, a pesquisa começará no diretório do projeto.  
  
 `file`  
 O\(s\) arquivo\(s\) a ser\(em\) procurados.  Os caracteres curinga são permitidos.  
  
## Comentários  
 A opção de **\/recurse** permite a você criar arquivo de código\-fonte em todos os diretórios filhos do diretório especificado \(`dir`\) ou do diretório do projeto.  
  
 Você pode usar caracteres curinga em um nome de arquivo para compilar todos os arquivos correspondentes no diretório do projeto sem usar **\/recurse**.  
  
 Essa opção do compilador não estiver disponível no Visual Studio e não pode ser modificada programaticamente.  
  
## Exemplo  
 Cria todos os arquivos C\# no diretório atual:  
  
```  
csc *.cs  
```  
  
 Cria todos os arquivos C\# no diretório dir1 \\ dir2 e em todos os diretórios abaixo deles e gerenciar dir2.dll:  
  
```  
csc /target:library /out:dir2.dll /recurse:dir1\dir2\*.cs  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)