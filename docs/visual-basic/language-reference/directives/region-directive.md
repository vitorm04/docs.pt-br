---
title: "Diretiva #Region | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Region"
  - "vb.#Region"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Diretiva #region"
  - "Palavra-chave #Region"
  - "diretiva de região (#region)"
  - "compilador do Visual Basic, diretivas de compilador"
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Diretiva #Region
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Recolhe e oculta seções de código em arquivos do Visual Basic.  
  
## Sintaxe  
  
```  
  
        #Region "identifier_string"  
#End Region  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`identifier_string`|Obrigatório.  Cadeia de caracteres que atua como o título de uma região quando ele estiver recolhido.  Regiões estão recolhidas por padrão.|  
|`#End Region`|Encerra o `#Region` bloco.|  
  
## Comentários  
 Use o `#Region` diretiva para especificar um bloco de código para expandir ou recolher ao usar o recurso de estruturação do Editor de código do Visual Studio.  Você pode colocar, ou *aninhar*, regiões em outras regiões para agrupar regiões semelhantes.  
  
## Exemplo  
 Este exemplo usa a `#Region` diretiva.  
  
 [!CODE [VbVbalrConditionalComp#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrConditionalComp#4)]  
  
## Consulte também  
 [Diretivas \#If...Then...\#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Estrutura de tópicos](/visual-studio/ide/outlining)   
 [Como recolher e ocultar seções do código](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)