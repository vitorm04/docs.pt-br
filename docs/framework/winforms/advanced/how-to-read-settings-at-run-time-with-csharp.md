---
title: 'Como: ler configurações em tempo de execução com C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8cdc1a79f1ab327ae037cd6a04aa769196405127
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966891"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Como: Ler configurações em tempo de execução c\#

Você pode ler as configurações de escopo do aplicativo tanto no escopo do usuário em tempo de execução por meio do objeto de propriedades. O objeto de propriedades expõe todas as configurações padrão para o projeto por meio do membro Properties.  
  
## <a name="to-read-settings-at-run-time-with-c"></a>Para ler configurações em tempo de execução c\#
  
Acesse a configuração apropriada por meio do membro Properties. O exemplo a seguir mostra como atribuir uma configuração chamada `myColor` a uma propriedade BackColor. Exige que você criou anteriormente um arquivo de configurações que contém uma configuração denominada `myColor` do tipo `System.Drawing.Color`. Para obter informações sobre como criar um arquivo de configurações, consulte [How To: Criar uma nova configuração em tempo de Design](how-to-create-a-new-setting-at-design-time.md).  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>Consulte também

- [Usando configurações do aplicativo e configurações do usuário](using-application-settings-and-user-settings.md)
- [Como: Gravar configurações do usuário em tempo de execução comC#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [Visão Geral das Configurações do Aplicativo](application-settings-overview.md)
