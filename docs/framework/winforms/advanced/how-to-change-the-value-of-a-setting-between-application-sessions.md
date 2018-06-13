---
title: Como alterar o valor de uma configuração entre sessões do aplicativo
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 383f72f223fb92170d16a9538c94e67825009abb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523404"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>Como alterar o valor de uma configuração entre sessões do aplicativo
Às vezes, você talvez queira alterar o valor de uma configuração entre sessões do aplicativo depois que o aplicativo foi compilado e implantado. Por exemplo, convém alterar uma cadeia de caracteres de conexão para apontar para o local do banco de dados correto. Como as ferramentas de tempo de design não estão disponíveis depois que o aplicativo foi compilado e implantado, você deve alterar o valor da configuração manualmente no arquivo.  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>Para alterar o valor de uma configuração entre sessões do aplicativo  
  
1.  Usando o Microsoft Notepad ou algum outro editor de texto ou XML, abra o arquivo. config associado ao seu aplicativo.  
  
2.  Localize a entrada para a configuração que você deseja alterar. Ela deve ser semelhante ao exemplo apresentado abaixo.  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  Digite um novo valor para a sua configuração e salve o arquivo.  
  
## <a name="see-also"></a>Consulte também  
 [Usando configurações do aplicativo e configurações do usuário](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Visão Geral das Configurações do Aplicativo](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
