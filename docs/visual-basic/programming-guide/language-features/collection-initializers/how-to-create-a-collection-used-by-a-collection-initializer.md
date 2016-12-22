---
title: "Como criar uma cole&#231;&#227;o usada por um inicializador de cole&#231;&#227;o (Visual Basic) | Microsoft Docs"
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
  - "inicializadores de coleção [Visual Basic]"
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar uma cole&#231;&#227;o usada por um inicializador de cole&#231;&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você usa um inicializador de coleta para criar uma coleção, o compilador Visual Basic procura um `Add` o método do tipo de coleção para os quais os parâmetros para o `Add` método correspondem aos tipos dos valores em um inicializador de coleção.  Isso `Add` método é usado para preencher a coleção com os valores do inicializador de coleção.  
  
## Exemplo  
 A exemplo a seguir mostra um `OrderCollection` coleção que contém um relatório público `Add` método um inicializador de coleção pode usar para adicionar objetos do tipo `Order`.  O `Add` método permite que você use a sintaxe do inicializador de coleção abreviado.  
  
 [!CODE [VbVbalrCollectionInitializersHowTo2#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2#4)]  
  
 [!CODE [VbVbalrCollectionInitializersHowTo2#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2#1)]  
  
 [!CODE [VbVbalrCollectionInitializersHowTo2#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2#2)]  
  
 [!CODE [VbVbalrCollectionInitializersHowTo2#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2#3)]  
  
## Consulte também  
 [Inicializadores de coleção](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Como criar um método para adicionar extensão usado por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)