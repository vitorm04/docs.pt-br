---
title: "/imports (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Opção de compilador /imports [Visual Basic]"
  - "Opção de compilador imports [Visual Basic]"
  - "Opção de compilador -imports [Visual Basic]"
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /imports (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Importa namespaces de um assembly específico.  
  
## Sintaxe  
  
```  
/imports:namespaceList  
```  
  
## Argumentos  
  
|||  
|-|-|  
|Termo|Definição|  
|`namespaceList`|Obrigatório.  Lista delimitada por vírgula de namespaces a serem importados.|  
  
## Comentários  
 A opção `/imports` importa qualquer namespace definido no interior do conjunto atual de arquivos de origem ou de qualquer assembly referenciado.  
  
 Os membros no namespace especificado por `/imports` estão disponíveis para todos os arquivos de código\-fonte na compilação.  Use [Instrução Imports \(tipo e namespace .NET\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para utilizar um namespace em apenas um arquivo de código fonte.  
  
||  
|-|  
|Para configurar \/imports no ambiente de desenvolvimento integrado Visual Studio|  
|1.  Tenha um projeto selecionado no **Solution Explorer**.  No menu **Project**, clique em **Properties**..  Para obter mais informações, consulte [Introdução ao Project Designer](http://msdn.microsoft.com/pt-br/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique na aba **References**.<br />3.  Insira o nome do namespace na caixa ao lado do botão **Add User Import**.<br />4.  Clique no botão **Add User Import** .|  
  
## Exemplo  
 O código a seguir compila quando `/imports:system` é especificado.  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)