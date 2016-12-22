---
title: "Acessando formul&#225;rios de aplicativo (Visual Basic) | Microsoft Docs"
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
  - "formulários de aplicativo, acessando"
  - "formulários, acessando todos os abertos"
  - "formulários, acessando um a partir de outro"
  - "formulários, comunicando entre"
  - "Objeto My.Forms"
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Acessando formul&#225;rios de aplicativo (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O objeto `My.Forms` fornece uma maneira fácil de acessar uma instância de cada Windows Form declarado no projeto do aplicativo.  Você também pode usar propriedades do objeto `My.Application` para acessar a tela inicial e formulário principal \(main form\) do aplicativo, e obter uma lista dos formulários abertos do aplicativo  
  
## Tarefas  
 A tabela a seguir lista exemplos mostrando como acessar os formulários do aplicativo.  
  
|||  
|-|-|  
|Para|Consulte|  
|Acessar um formulário a partir de outro formulário em um aplicativo.|[Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|Exibir os títulos de todos os formulários abertos do aplicativo.|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|Atualizar a tela inicial com informações de status enquanto um aplicativo é iniciado.|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>   
 [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)