---
title: Objeto My. Settings (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: a962f7cce961b1ee6829702a6815ba02c534efb4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840361"
---
# <a name="mysettings-object"></a>Objeto My.Settings
Fornece propriedades e métodos para acessar as configurações do aplicativo.  
  
## <a name="remarks"></a>Comentários  
 O `My.Settings` objeto fornece acesso às configurações do aplicativo e permite que você armazene dinamicamente e recupere as configurações de propriedade e outras informações para seu aplicativo. Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Propriedades  
 As propriedades do objeto `My.Settings` fornecem acesso às configurações do seu aplicativo. Para adicionar ou remover configurações, use o **Designer de configurações**.  
  
 Cada configuração tem um **nome**, **tipo**, **escopo**, e **valor**, e essas configurações determinam como a propriedade para acessar cada configuração aparece no `My.Settings` objeto:  
  
-   **Nome** determina o nome da propriedade.  
  
-   **Tipo** determina o tipo da propriedade.  
  
-   **Escopo** indica se a propriedade é somente leitura. Se o valor for **Application**, a propriedade é somente leitura; se o valor estiver **usuário**, a propriedade é leitura / gravação.  
  
-   **Valor** é o valor padrão da propriedade.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|---|---|  
|`Reload`|Recarrega as configurações do usuário dos últimos valores salvos.|  
|`Save`|Salva as configurações do usuário atual.|  
  
 O `My.Settings` objeto também fornece propriedades avançadas e métodos, herdados da <xref:System.Configuration.ApplicationSettingsBase> classe.  
  
## <a name="tasks"></a>Tarefas  
 A tabela a seguir lista exemplos de tarefas que envolvem o `My.Settings` objeto.  
  
|Para|Consulte|  
|---|---|  
|Ler uma configuração de aplicativo|[Como: ler configurações do aplicativo no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Alterar uma configuração de usuário|[Como: alterar configurações do usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Persistir configurações do usuário|[Como: persistir configurações de usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Criar uma grade de propriedade para as configurações do usuário|[Como: criar grades de propriedades para configurações do usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Exemplo  
 Este exemplo exibe o valor da configuração `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Para que esse exemplo funcione, seu aplicativo deve ter uma configuração `Nickname`, do tipo `String`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Configuration.ApplicationSettingsBase>
- [Como: ler configurações do aplicativo no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Como: alterar configurações do usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Como: persistir configurações de usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Como: criar grades de propriedades para configurações do usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
