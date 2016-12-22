---
title: "Como criar um m&#233;todo para adicionar extens&#227;o usado por um inicializador de cole&#231;&#227;o (Visual Basic) | Microsoft Docs"
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
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar um m&#233;todo para adicionar extens&#227;o usado por um inicializador de cole&#231;&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você usa um inicializador de coleta para criar uma coleção, o compilador Visual Basic procura um `Add` o método do tipo de coleção para os quais os parâmetros para o `Add` método correspondem aos tipos dos valores em um inicializador de coleção.  Isso `Add` método é usado para preencher a coleção com os valores do inicializador de coleção.  
  
 Se nenhuma correspondência `Add` método existe e você não pode modificar o código para a coleção, você pode adicionar um método de extensão chamado `Add` que leva os parâmetros necessários para o inicializador de coleção.  Normalmente, isso é o que você precisa fazer quando você usa os inicializadores de coleção para coleções genéricas.  
  
## Exemplo  
 O exemplo a seguir mostra como adicionar um método de extensão para a genérica <xref:System.Collections.Generic.List%601> digite de forma que um inicializador de coleção pode ser usado para adicionar objetos do tipo `Employee`.  O método de extensão permite que você use a sintaxe do inicializador de coleção abreviado.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## Consulte também  
 [Inicializadores de coleção](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Como criar uma coleção usada por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)