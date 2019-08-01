---
title: 'Como: ler configurações em tempo de execução com C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 6a40718d57fad4041eeea2fded03b7256abbe8d1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710222"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Como: Ler configurações em tempo de execução com C\#

Você pode ler as configurações no escopo do aplicativo e no escopo do usuário em tempo de execução por meio do objeto de propriedades. O objeto Properties expõe todas as configurações padrão do projeto por meio do membro Properties. Settings. default no namespace padrão do projeto em que estão definidas.  
  
## <a name="to-read-settings-at-run-time-with-c"></a>Para ler as configurações em tempo de execução com C\#
  
Acesse a configuração apropriada por meio do membro Propriedades. Settings. default. O exemplo a seguir mostra como atribuir uma configuração chamada `myColor` a uma propriedade BackColor. Ele requer que você tenha criado anteriormente um arquivo de configurações que contém uma `myColor` configuração nomeada `System.Drawing.Color`do tipo. Para obter informações sobre como criar um arquivo de [configurações, consulte Como: Crie uma nova configuração em tempo](how-to-create-a-new-setting-at-design-time.md)de design.  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>Consulte também

- [Usando configurações do aplicativo e configurações do usuário](using-application-settings-and-user-settings.md)
- [Como: Gravar configurações de usuário em tempo de execução comC#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [Visão Geral das Configurações do Aplicativo](application-settings-overview.md)
