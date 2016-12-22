---
title: "Inst&#226;ncias de objeto padr&#227;o fornecidas por My.Forms e My.WebServices (Visual Basic) | Microsoft Docs"
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
  - "Objeto My.Forms, desenvolvendo aplicativos"
  - "Objeto My.WebServices, desenvolvendo aplicativos"
  - "desenvolvimento rápido de aplicativos (RAD), My.Forms"
  - "desenvolvimento rápido de aplicativos (RAD), My.WebServices"
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Inst&#226;ncias de objeto padr&#227;o fornecidas por My.Forms e My.WebServices (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os objetos [My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) e o [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) fornecem acesso a formulários, fontes de dados, e Web Services XML usado por seu aplicativo.  Eles fazem isso, fornecendo coleções de *Instâncias padrão* de cada um desses objetos.  
  
## Instâncias padrão  
 Uma instância padrão é uma instância da classe que é fornecida em tempo de execução e não precisa ser declarada e instanciada usando instruções  `Dim` e `New` .  O exemplo a seguir demonstra como você pode ter declarado e instanciado uma instância de uma classe <xref:System.Windows.Forms.Form> chamada `Form1`,e como agora você pode conseguir obter uma instância padrão desta classe <xref:System.Windows.Forms.Form> por `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 O objeto `My.Forms` retorna uma coleção de instâncias padrão para cada classe `Form` que existe em seu projeto.  Da mesma forma, o `My.WebServices` fornece uma instância padrão da classe do proxy para cada serviço da Web que você tenha criado uma referência em seu aplicativo.  
  
## Consulte também  
 [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)   
 [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)