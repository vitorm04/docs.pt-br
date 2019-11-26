---
title: 'How to: Read Application Settings'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 04726381f8d285ae61045d1624b3b41b7f47e491
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329563"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Como ler configurações do aplicativo no Visual Basic

Você pode ler uma configuração de usuário, acessando a propriedade da configuração no objeto `My.Settings`.  
  
 O objeto `My.Settings` expõe cada configuração como uma propriedade. O nome da propriedade é o mesmo que o nome da configuração e o tipo de propriedade é o mesmo que o tipo de configuração. O **Escopo** da configuração indica se a propriedade é somente leitura: a propriedade para uma configuração de escopo do **Aplicativo** é somente leitura, enquanto que a propriedade para uma configuração de escopo do **Usuário** é de leitura/gravação. Para obter mais informações, consulte [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Exemplo  

 Este exemplo exibe o valor da configuração `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Para que esse exemplo funcione, seu aplicativo deve ter uma configuração `Nickname`, do tipo `String`. Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Consulte também

- [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Como alterar configurações do usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Como persistir configurações do usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Como criar grades de propriedades para configurações do usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
