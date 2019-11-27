---
title: Desenvolvimento de aplicativo rápido com My.Resources e My.Settings
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: ce9a5bf76ba3132f58aa40227a145d8b5bf1591d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349259"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Desenvolvimento de aplicativo rápido com My.Resources e My.Settings (Visual Basic)

O objeto `My.Resources` fornece acesso aos recursos do aplicativo e permite que você recupere dinamicamente os recursos para seu aplicativo.  
  
## <a name="retrieving-resources"></a>Recuperando recursos  

 Vários recursos, como arquivos de áudio, ícones, imagens e cadeias de caracteres, podem ser recuperados por meio do objeto `My.Resources`. Por exemplo, você pode acessar os arquivos de recursos específicos da cultura do aplicativo. O exemplo a seguir define o ícone do formulário para o ícone chamado `Form1Icon` armazenado no arquivo de recurso do aplicativo.  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 O objeto `My.Resources` expõe apenas recursos globais. Ele não fornece acesso aos arquivos de recursos associados aos formulários. Você deve acessar os recursos do formulário no formulário.  
  
 Da mesma forma, o objeto `My.Settings` fornece acesso às configurações do aplicativo e permite que você armazene e recupere dinamicamente as configurações de propriedade e outras informações para seu aplicativo. Para obter mais informações, consulte [My. Resources](../../../visual-basic/language-reference/objects/my-resources-object.md) Object e [My. Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Consulte também

- [Objeto My.Resources](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [Objeto My.Settings](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Acessando configurações de aplicativo](../../../visual-basic/developing-apps/programming/app-settings/index.md)
