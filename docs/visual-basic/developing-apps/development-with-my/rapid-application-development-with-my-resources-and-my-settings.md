---
title: Desenvolvimento de aplicativo rápido com My.Resources e My.Settings (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 1d5fe35ea491c2c2d3de82ef208fec59a6079a25
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976064"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Desenvolvimento de aplicativo rápido com My.Resources e My.Settings (Visual Basic)
O `My.Resources` objeto fornece acesso aos recursos do aplicativo e permite que você recupere dinamicamente recursos para seu aplicativo.  
  
## <a name="retrieving-resources"></a>Recuperando recursos  
 Um número de recursos, como cadeias de caracteres, ícones, imagens e arquivos de áudio pode ser recuperado por meio de `My.Resources` objeto. Por exemplo, você pode acessar arquivos de recurso específico de cultura do aplicativo. O exemplo a seguir define o ícone do formulário para o ícone chamado `Form1Icon` armazenadas no arquivo de recurso do aplicativo.  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 O `My.Resources` objeto expõe apenas recursos globais. Ele não fornece acesso aos arquivos de recurso associados a formulários. Você deve acessar os recursos de formulário do formulário.  
  
 Da mesma forma, o `My.Settings` objeto fornece acesso às configurações do aplicativo e permite que você armazene dinamicamente e recupere as configurações de propriedade e outras informações para seu aplicativo. Para obter mais informações, consulte [objeto My. Resources](../../../visual-basic/language-reference/objects/my-resources-object.md) e [objeto My. Settings](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Consulte também
- [Objeto My.Resources](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [Objeto My.Settings](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Acessando configurações de aplicativo](../../../visual-basic/developing-apps/programming/app-settings/index.md)
