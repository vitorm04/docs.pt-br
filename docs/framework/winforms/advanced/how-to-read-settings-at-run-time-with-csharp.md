---
title: Como ler configurações em tempo de execução com C#
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8259e2f429718793c01868855651d1000620fae5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521008"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Como ler configurações em tempo de execução com C# #
Você pode ler as configurações no escopo do aplicativo tanto no escopo do usuário em tempo de execução por meio do objeto de propriedades. O objeto de propriedades expõe todas as configurações padrão do projeto por meio do membro Properties.Settings.Default.  
  
### <a name="to-read-settings-at-run-time-with-c"></a>Leitura de configurações em tempo de execução com c#  
  
-   Acesse a configuração apropriada por meio do membro Properties.Settings.Default. O exemplo a seguir mostra como atribuir uma configuração denominada `myColor` a uma propriedade BackColor. Requer que você criou anteriormente um arquivo de configurações que contém uma configuração denominada `myColor` do tipo `System.Drawing.Color`. Para obter informações sobre como criar um arquivo de configurações, consulte [como: criar uma nova configuração em tempo de Design](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Usando configurações do aplicativo e configurações do usuário](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Como Gravar Configurações do Usuário em Tempo de Execução com C#](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [Visão Geral das Configurações do Aplicativo](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
