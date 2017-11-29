---
title: "Como gravar configurações do usuário em tempo de execução com C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5966aef77c994d2657bd282ad15e8f59a64eeb47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>Como gravar configurações do usuário em tempo de execução com C# #
As configurações que estão no escopo do aplicativo são somente leitura e só podem ser alteradas em tempo de design ou alterando o arquivo. config entre as sessões do aplicativo. Configurações que estão no escopo do usuário, no entanto, podem ser gravadas em tempo de execução assim como qualquer valor de propriedade deve ser alterada. Persiste o novo valor para a duração da sessão do aplicativo. Você pode manter as alterações das configurações entre sessões do aplicativo chamando o método de salvar.  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>Como: Gravar e salvar as configurações do usuário em tempo de execução com c#  
  
1.  A configuração de acesso e atribuir um novo valor conforme mostrado neste exemplo:  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  Se você quiser manter as alterações das configurações entre sessões do aplicativo, chame o método Save conforme mostrado neste exemplo:  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     Configurações de usuário são salvas em um arquivo em uma subpasta da pasta de dados de aplicativo oculta local do usuário.  
  
## <a name="see-also"></a>Consulte também  
 [Usando configurações do aplicativo e configurações do usuário](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Como Ler Configurações em Tempo de Execução com C#](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [Visão Geral das Configurações do Aplicativo](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
