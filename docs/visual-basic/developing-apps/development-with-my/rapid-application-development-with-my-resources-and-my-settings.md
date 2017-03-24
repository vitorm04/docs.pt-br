---
title: "Desenvolvimento rápido de aplicativos com My. Resources e My. Settings (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.Settings object, developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object, developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: 6
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 41d4da4a76401a01e240f6e8767628e10185ce98
ms.lasthandoff: 03/13/2017

---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Desenvolvimento de aplicativo rápido com My.Resources e My.Settings (Visual Basic)
O `My.Resources` objeto fornece acesso aos recursos do aplicativo e permite que você se recupere dinamicamente recursos para seu aplicativo.  
  
## <a name="retrieving-resources"></a>Recuperando recursos  
 Um número de recursos, como arquivos de áudio, ícones, imagens e cadeias de caracteres pode ser recuperado através de `My.Resources` objeto. Por exemplo, você pode acessar arquivos de recurso com cultura específica do aplicativo. O exemplo a seguir define o ícone do formulário para o ícone chamado `Form1Icon` armazenados no arquivo de recurso do aplicativo.  
  
 [!code-vb[VbVbcnMy&#7;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 O `My.Resources` objeto expõe apenas recursos globais. Ele não fornece acesso aos arquivos de recursos associados a formulários. Você deve acessar os recursos de formulário do formulário. Para obter mais informações, consulte [Passo a passo: Localizando o Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
 Da mesma forma, o `My.Settings` objeto fornece acesso às configurações do aplicativo e permite que você armazene dinamicamente e recupere as configurações de propriedade e outras informações para seu aplicativo. Para obter mais informações, consulte [objeto My. Resources](../../../visual-basic/language-reference/objects/my-resources-object.md) e [objeto My. Settings](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Consulte também  
 [Objeto My. Resources](../../../visual-basic/language-reference/objects/my-resources-object.md)   
 [Objeto My. Settings](../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [Acessando configurações de aplicativo](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
