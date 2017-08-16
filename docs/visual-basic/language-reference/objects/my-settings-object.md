---
title: Objeto My. Settings | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
dev_langs:
- VB
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: d48d3556f55ef286e2f501e2df5bf5035d3aff90
ms.lasthandoff: 03/13/2017

---
# <a name="mysettings-object"></a>Objeto My.Settings
Fornece propriedades e métodos para acessar as configurações do aplicativo.  
  
## <a name="remarks"></a>Comentários  
 O `My.Settings` objeto fornece acesso às configurações do aplicativo e permite que você armazene dinamicamente e recupere as configurações de propriedade e outras informações para seu aplicativo. Para obter mais informações, consulte [configurações de aplicativo de gerenciamento (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Propriedades  
 As propriedades do `My.Settings` objeto fornecem acesso às configurações do aplicativo. Para adicionar ou remover configurações, use o **Settings Designer**.  
  
 Cada configuração tem um **nome**, **tipo**, **escopo**, e **valor**, e essas configurações determinam como a propriedade para acessar cada configuração aparece no `My.Settings` objeto:  
  
-   **Nome** determina o nome da propriedade.  
  
-   **Tipo** determina o tipo da propriedade.  
  
-   **Escopo** indica se a propriedade é somente leitura. Se o valor for **aplicativo**, a propriedade é somente leitura; se o valor for **usuário**, a propriedade é leitura / gravação.  
  
-   **Valor** é o valor padrão da propriedade.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|---|---|  
|`Reload`|Recarrega as configurações do usuário dos últimos valores salvos.|  
|`Save`|Salva as configurações do usuário atual.|  
  
 O `My.Settings` objeto também fornece propriedades avançadas e métodos, herdados da <xref:System.Configuration.ApplicationSettingsBase>classe.</xref:System.Configuration.ApplicationSettingsBase>  
  
## <a name="tasks"></a>Tarefas  
 A tabela a seguir lista exemplos de tarefas envolvendo o `My.Settings` objeto.  
  
|Para|Consulte|  
|---|---|  
|Ler uma configuração de aplicativo|[Como: ler configurações do aplicativo no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Alterar uma configuração de usuário|[Como: alterar as configurações de usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Persistir configurações de usuário|[Como: persistir configurações de usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Criar uma grade de propriedade para configurações de usuário|[Como: criar grades de propriedades para configurações de usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Exemplo  
 Este exemplo exibe o valor de `Nickname` configuração.  
  
 [!code-vb[VbVbalrMyResources&#14;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 Para esse exemplo funcione, seu aplicativo deve ter uma `Nickname` configuração, do tipo `String`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Configuration.ApplicationSettingsBase></xref:System.Configuration.ApplicationSettingsBase>   
 [Como: ler configurações do aplicativo no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [Como: alterar as configurações de usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [Como: persistir configurações de usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [Como: criar grades de propriedades para configurações de usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [Gerenciando configurações de aplicativo (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)
