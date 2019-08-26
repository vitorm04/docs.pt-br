---
title: 'Como: Alterar configurações de usuário no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 553ebc5b0d6381f56783df8be83344f96a21dd8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968401"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Como: Alterar configurações de usuário no Visual Basic
Você pode alterar uma configuração do usuário atribuindo um novo valor à propriedade da configuração no objeto `My.Settings`.  
  
 O objeto `My.Settings` expõe cada configuração como uma propriedade. O nome da propriedade é o mesmo que o nome da configuração e o tipo de propriedade é o mesmo que o tipo de configuração. O **Escopo** da configuração determina se a propriedade é somente leitura: A propriedade de uma configuração no escopo do **Aplicativo** é somente leitura, enquanto a propriedade de uma configuração no escopo do **Usuário** é leitura/gravação. Para obter mais informações, consulte [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Embora você possa alterar e salvar os valores das configurações de escopo do usuário em tempo de execução, as configurações de escopo do aplicativo são somente leitura e não podem ser alteradas programaticamente. Você pode alterar as configurações de escopo do aplicativo ao criar o aplicativo usando o **Designer de Projeto** ou editando o arquivo de configuração de aplicativo. Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Exemplo  
 Este exemplo altera o valor da configuração do usuário `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 Para que esse exemplo funcione, seu aplicativo deve ter uma configuração do usuário `Nickname`, do tipo `String`.  
  
 O aplicativo salva as configurações do usuário quando o aplicativo é desligado. Para salvar as configurações imediatamente, chame o método `My.Settings.Save`. Para obter mais informações, confira [Como: Persistir configurações de usuário em Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Consulte também

- [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Como: ler configurações do aplicativo no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Como: persistir configurações de usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Como: criar grades de propriedades para configurações do usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
