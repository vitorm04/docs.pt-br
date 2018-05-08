---
title: Desenvolvimento de aplicativo rápido com My.Resources e My.Settings (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 808e02510d4f0a237ad4354b2edac8fa024b5f83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Desenvolvimento de aplicativo rápido com My.Resources e My.Settings (Visual Basic)
O `My.Resources` objeto fornece acesso aos recursos do aplicativo e permite que você recupere dinamicamente recursos para seu aplicativo.  
  
## <a name="retrieving-resources"></a>Recuperando recursos  
 Um número de recursos, como arquivos de áudio, ícones, imagens e cadeias de caracteres pode ser recuperado por meio de `My.Resources` objeto. Por exemplo, você pode acessar arquivos de recursos específicos de cultura do aplicativo. O exemplo a seguir define o ícone do formulário para o ícone chamado `Form1Icon` armazenados no arquivo de recurso do aplicativo.  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 O `My.Resources` objeto expõe apenas recursos globais. Ele não fornece acesso aos arquivos de recursos associados a formulários. Você deve acessar os recursos de formulário do formulário.  
  
 Da mesma forma, o `My.Settings` objeto fornece acesso às configurações do aplicativo e permite que você armazene dinamicamente e recupere as configurações de propriedade e outras informações para seu aplicativo. Para obter mais informações, consulte [objeto My. Resources](../../../visual-basic/language-reference/objects/my-resources-object.md) e [objeto My. Settings](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Consulte também  
 [Objeto My.Resources](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [Objeto My.Settings](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Acessando configurações de aplicativo](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
