---
title: 'Como: Ler configurações em tempo de execução comC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d798b40e5e337ea7652c8e82cb7fa860a87528b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521745"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Como: Ler configurações em tempo de execução comC# #
Você pode ler as configurações de escopo do aplicativo tanto no escopo do usuário em tempo de execução por meio do objeto de propriedades. O objeto de propriedades expõe todas as configurações padrão para o projeto por meio do membro Properties.  
  
### <a name="to-read-settings-at-run-time-with-c"></a>Para ler configurações em tempo de execução comC#  
  
-   Acesse a configuração apropriada por meio do membro Properties. O exemplo a seguir mostra como atribuir uma configuração chamada `myColor` a uma propriedade BackColor. Exige que você criou anteriormente um arquivo de configurações que contém uma configuração denominada `myColor` do tipo `System.Drawing.Color`. Para obter informações sobre como criar um arquivo de configurações, consulte [How To: Criar uma nova configuração em tempo de Design](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a>Consulte também
- [Usando configurações do aplicativo e configurações do usuário](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [Como: Gravar configurações do usuário em tempo de execução comC#](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)
- [Visão Geral das Configurações do Aplicativo](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
