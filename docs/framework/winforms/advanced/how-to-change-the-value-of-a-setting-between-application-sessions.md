---
title: 'Como: alterar o valor de uma configuração entre sessões do aplicativo'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 95e613cb280813cd75d887d3cf147d7c897bc2e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004426"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>Como: alterar o valor de uma configuração entre sessões do aplicativo
Às vezes, você talvez queira alterar o valor de uma configuração entre sessões do aplicativo depois que o aplicativo foi compilado e implantado. Por exemplo, você talvez queira alterar uma cadeia de caracteres de conexão para apontar para o local do banco de dados correto. Uma vez que as ferramentas de tempo de design não ficam disponíveis depois que o aplicativo foi compilado e implantado, você deve alterar o valor da configuração manualmente no arquivo.  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>Para alterar o valor de uma configuração entre sessões do aplicativo  
  
1. Usando o Microsoft Notepad ou algum outro texto ou editor XML, abra o arquivo. config associado ao seu aplicativo.  
  
2. Localize a entrada para a configuração que você deseja alterar. Ele deve ser semelhante ao exemplo a apresentada a seguir.  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3. Digite um novo valor para a sua configuração e salve o arquivo.  
  
## <a name="see-also"></a>Consulte também

- [Usando configurações do aplicativo e configurações do usuário](using-application-settings-and-user-settings.md)
- [Visão Geral das Configurações do Aplicativo](application-settings-overview.md)
