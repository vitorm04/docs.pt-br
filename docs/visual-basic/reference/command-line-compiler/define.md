---
title: "/define (Visual Basic) | Microsoft Docs"
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
  - "Opção de compilador /d [Visual Basic]"
  - "Opção de compilador /define [Visual Basic]"
  - "Opção de compilador d [Visual Basic]"
  - "Opção de compilador -d [Visual Basic]"
  - "Opção de compilador define [Visual Basic]"
  - "Opção de compilador -define [Visual Basic]"
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /define (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Define as constantes de compilador condicional.  
  
## Sintaxe  
  
```  
/define:["]symbol[=value][,symbol[=value]]["] ' -or- /d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## Arguments  
  
|||  
|-|-|  
|Termo|Definição|  
|`symbol`|Obrigatório.  O símbolo a ser definido.|  
|`value`|Opcional.  O valor para atribuir `symbol`.  Se `value` for uma cadeia de caracteres, deverá ser colocado entre sequências de barra invertida\/aspas \(\\"\), em vez de aspas.  Se nenhum valor for especificado, será considerado como True.|  
  
## Comentários  
 A opção `/define` tem um efeito semelhante a usar uma diretiva de pré\-processador `#Const` em seu arquivo de origem, exceto que as constantes definidas com `/define` são públicas e se aplicam a todos os arquivos do projeto.  
  
 Você pode usar símbolos criados por essa opção com a diretiva `#If`...`Then`...`#Else` para compilar os arquivos de origem condicionalmente.  
  
 `/d` é a forma abreviada de `/define`.  
  
 Você pode definir vários símbolos com `/define` usando uma vírgula para separar as definições de símbolos.  
  
||  
|-|  
|Para configurar \/define no ambiente de desenvolvimento integrado do Visual Studio|  
|1.  Selecione um projeto no **Gerenciador de Soluções**.  No menu **Projeto**, clique em **Propriedades**.  Para obter mais informações, consulte [Introdução ao Project Designer](http://msdn.microsoft.com/pt-br/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique na guia **Compilar**.<br />3.  Clique em **Avançado**.<br />4.  Modifique o valor na caixa **Constantes Personalizadas**.|  
  
## Exemplo  
 O código a seguir define e usa duas constantes de compilador condicional.  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Diretivas \#If...Then...\#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Diretiva \#Const](../../../visual-basic/language-reference/directives/const-directive.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)