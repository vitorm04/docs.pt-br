---
title: "Como ler configurações em tempo de execução com C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85dc3a2c97b8fe5003c6026874dbdcaa9af89d77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
