---
title: "Desenvolvimento de aplicativo r&#225;pido com My.Resources e My.Settings (Visual Basic) | Microsoft Docs"
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
  - "Objeto My.Resources, desenvolvendo aplicativos"
  - "Objeto My.Settings, desenvolvendo aplicativos"
  - "desenvolvimento rápido de aplicativos (RAD), My.Resources"
  - "desenvolvimento rápido de aplicativos (RAD), My.Settings"
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Desenvolvimento de aplicativo r&#225;pido com My.Resources e My.Settings (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O objeto `My.Resources` fornece acesso aos recursos do aplicativo e permite que você se recupere dinamicamente recursos para seu aplicativo.  
  
## Recuperando Recursos  
 Um número de recursos, tais como arquivos de áudio, ícones, imagens e sequências de caracteres podem ser recuperados por meio do objeto `My.Resources`.  Por exemplo, você pode acessar os arquivos de recursos específicos de cultura do aplicativo.  Este exemplo a seguir define o ícone do formulário para o ícone chamado `Form1Icon` armazenado no arquivo de recurso do aplicativo.  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 O objeto `My.Resources` expõe apenas recursos globais.  Ele não fornece acesso aos arquivos de recursos associados a formulários.  Você deve acessar os recursos de formulário a partir do formulário.  Para obter mais informações, consulte [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/pt-br/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
 Da mesma forma, o objeto `My.Settings` fornece acesso às configurações do aplicativo e permite que você armazene dinamicamente e recupere as configurações de propriedade e outras informações para seu aplicativo.  Para obter mais informações, consulte [Objeto My.Resources](../../../visual-basic/language-reference/objects/my-resources-object.md) e [Objeto My.Settings](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## Consulte também  
 [Objeto My.Resources](../../../visual-basic/language-reference/objects/my-resources-object.md)   
 [Objeto My.Settings](../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [Acessando configurações de aplicativo](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)