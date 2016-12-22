---
title: "Como ler configura&#231;&#245;es do aplicativo no Visual Basic | Microsoft Docs"
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
  - "configurações de aplicativo, lendo"
  - "Objeto My.Settings, lendo configurações do aplicativo"
  - "lendo configurações do aplicativo"
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como ler configura&#231;&#245;es do aplicativo no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode ler uma configuração de usuário acessando a propriedade da configuração no objeto `My.Settings`.  
  
 O objeto `My.Settings` expõe cada configuração como uma propriedade.  O nome da propriedade é o mesmo do nome da configuração, e o tipo da propriedade é o mesmo do tipo da configuração.  O **Scope** das configurações  indica se a propriedade é somente leitura; a propriedade para uma configuração de escopo **Application** é somente para leitura, enquanto a propriedade para uma configuração de escopo **User** é leitura\-gravação.  Para obter mais informações, consulte [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## Exemplo  
 Este exemplo exibe o valor da configuração `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 Para este exemplo funcionar, seu aplicativo deve ter uma configuração `Nickname`, do tipo `String`.  Para obter mais informações, consulte [Gerenciando configurações de aplicativo \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet).  
  
## Consulte também  
 [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [Como alterar configurações do usuário no Visual Basic](../Topic/How%20to:%20Change%20User%20Settings%20in%20Visual%20Basic.md)   
 [Como persistir configurações de usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [Como criar grades de propriedades para configurações de usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [Gerenciando configurações de aplicativo \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)