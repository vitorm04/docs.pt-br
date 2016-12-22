---
title: "/rootnamespace | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/rootnamespace"
  - "rootnamespace"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Opção de compilador /rootnamespace [Visual Basic]"
  - "Opção de compilador rootnamespace [Visual Basic]"
  - "Opção de compilador -rootnamespace [Visual Basic]"
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /rootnamespace
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica um namespace para todas as declarações de tipo.  
  
## Sintaxe  
  
```  
/rootnamespace:namespace  
```  
  
## Argumentos  
  
|||  
|-|-|  
|Termo|Definição|  
|`namespace`|O nome do namespace no qual fazer inclusão de todas as declarações de tipo para o projeto atual.|  
  
## Comentários  
 Se você usar o arquivo executável do Visual Studio \(devenv. exe\) para compilar um projeto criado no ambiente de desenvolvimento integrado do Visual Studio, use `/rootnamespace` para especificar o valor da <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> propriedade.  Consulte [Opções de linha de comando do desenvolvedor](/visual-studio/ide/reference/devenv-command-line-switches) para obter mais informações.  
  
 Use o common language runtime Desassemblador do MSIL \(eu`ldasm.exe`\) para exibir os nomes de namespace no seu arquivo de saída.  
  
||  
|-|  
|Para definir o Visual Studio \/rootnamespace ambiente de desenvolvimento integrado|  
|1.  Tenha um projeto selecionado no **Solution Explorer**.  No menu **Project**, clique em **Properties**..  Para obter mais informações, consulte [Introdução ao Project Designer](http://msdn.microsoft.com/pt-br/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique na guia **Application**.<br />3.  Modificar o valor de  **Namespace raiz** caixa.|  
  
## Exemplo  
 O código a seguir compila `In.vb` e inclui todas as declarações de tipo no namespace `mynamespace`.  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Ildasm.exe \(IL Disassembler\)](../Topic/Ildasm.exe%20\(IL%20Disassembler\).md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)