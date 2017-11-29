---
title: "Como ler configurações do aplicativo no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6cfc529262053daf7c8111271de2c51e9cab4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Como ler configurações do aplicativo no Visual Basic
Você pode ler uma configuração de usuário, acessando a propriedade da configuração no objeto `My.Settings`.  
  
 O objeto `My.Settings` expõe cada configuração como uma propriedade. O nome da propriedade é o mesmo que o nome da configuração e o tipo de propriedade é o mesmo que o tipo de configuração. O **Escopo** da configuração indica se a propriedade é somente leitura: a propriedade para uma configuração de escopo do **Aplicativo** é somente leitura, enquanto que a propriedade para uma configuração de escopo do **Usuário** é de leitura/gravação. Para obter mais informações, consulte [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo exibe o valor da configuração `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 Para que esse exemplo funcione, seu aplicativo deve ter uma configuração `Nickname`, do tipo `String`. Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Consulte também  
 [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Como alterar configurações do usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Como persistir configurações do usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Como criar grades de propriedades para configurações do usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
