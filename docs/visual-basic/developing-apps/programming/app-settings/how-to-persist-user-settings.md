---
title: "Como persistir configura&#231;&#245;es de usu&#225;rio no Visual Basic | Microsoft Docs"
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
  - "Objeto My.Settings, persistindo configurações de usuário"
  - "persistência, persistindo configurações de usuário [Visual Basic]"
  - "configurações do usuário, persistindo"
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como persistir configura&#231;&#245;es de usu&#225;rio no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode usar o método `My.Settings.Save` para persistir alterações em configurações de usuário.  
  
 Normalmente, aplicativos são projetados para persistirem as alterações às configurações do usuário quando o aplicativo é desligado.  Isso ocorre porque salvar as configurações pode levar, dependendo de vários fatores, alguns segundos.  
  
 Para obter mais informações, consulte [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Embora você possa alterar e salvar os valores das configurações de escopo de usuário em tempo de execução, configurações de escopo de aplicativo são somente para leitura e não podem ser alteradas através de programação.  Você pode alterar configurações de escopo de aplicativo ao criar o aplicativo, através do **Project Designer**, ou editando o arquivo de configuração de aplicativo.  Para obter mais informações, consulte [Gerenciando configurações de aplicativo \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet).  
  
## Exemplo  
 Este exemplo altera o valor da configuração do usuário `LastChanged` e salva essa alteração chamando o método `My.Settings.Save`.  
  
 [!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-persist-user-settings_1.vb)]  
  
 Para que este exemplo funcione, seu aplicativo deve ter uma configuração de usuário `LastChanged`, do tipo `Date`.  Para obter mais informações, consulte [Gerenciando configurações de aplicativo \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet).  
  
## Consulte também  
 [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [Como ler configurações do aplicativo no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [Como alterar configurações do usuário no Visual Basic](../Topic/How%20to:%20Change%20User%20Settings%20in%20Visual%20Basic.md)   
 [Como criar grades de propriedades para configurações de usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [Gerenciando configurações de aplicativo \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)