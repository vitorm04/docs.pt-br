---
title: 'Como: gravar configurações do usuário em tempo de execução com C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 264fa9706f9255d7324cad6d02c36cc424e28995
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778827"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>Como: Gravar configurações do usuário em tempo de execução c\#

As configurações que estão no escopo do aplicativo são somente leitura e só podem ser alteradas em tempo de design ou alterando o arquivo. config entre sessões do aplicativo. Configurações que estão no escopo do usuário, no entanto, podem ser gravadas em tempo de execução assim como você alteraria qualquer valor de propriedade. O novo valor será mantido enquanto durar a sessão do aplicativo. Você pode persistir as alterações das configurações entre sessões do aplicativo chamando o método Save.  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>Como: Gravar e manter as configurações do usuário em tempo de execução c\#
  
1. Acesse a configuração e atribuir um novo valor conforme mostrado neste exemplo:  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. Se você quiser manter as alterações das configurações entre sessões do aplicativo, chame o método Save conforme mostrado neste exemplo:  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
Configurações de usuário são salvas em um arquivo em uma subpasta da pasta de dados do aplicativo oculto local do usuário.  
  
## <a name="see-also"></a>Consulte também

- [Usando configurações do aplicativo e configurações do usuário](using-application-settings-and-user-settings.md)
- [Como: Ler configurações em tempo de execução comC#](how-to-read-settings-at-run-time-with-csharp.md)
- [Visão Geral das Configurações do Aplicativo](application-settings-overview.md)
