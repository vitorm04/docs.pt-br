---
title: "Como adicionar vários conjuntos de configurações a um aplicativo em C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec541a8f83990eec79226be7fb4880ef8dda639d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Como adicionar vários conjuntos de configurações a um aplicativo em C# #
Em alguns casos, convém ter vários conjuntos de configurações em um aplicativo. Por exemplo, se você estiver desenvolvendo um aplicativo no qual se supõe que um determinado grupo de configurações deve ser alterado com frequência, talvez seja mais inteligente separá-las em um único arquivo, de modo que esse arquivo possa ser substituído em massa sem que as demais configurações sejam afetadas. O Visual Studio lhe permite adicionar vários conjuntos de configurações ao projeto. Conjuntos de configurações adicionais podem ser acessados através do objeto Properties.Settings.  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>Para adicionar um conjunto de configurações adicional ao aplicativo  
  
1.  No menu **Projeto**, escolha **Adicionar Novo Item**. A caixa de diálogo **Adicionar Novo Item** é aberta.  
  
2.  Na caixa de diálogo **Adicionar Novo Item**, selecione **Arquivo de Configurações**, digite um nome para o arquivo e clique em **Adicionar** para adicionar um novo arquivo de configurações à sua solução.  
  
3.  No **Gerenciador de Soluções**, arraste o novo arquivo de configurações para a pasta **Propriedades**. Isso faz com que as suas novas configurações fiquem disponíveis no código.  
  
4.  Adicione e use configurações nesse arquivo da mesma forma que faria em qualquer outro arquivo de configurações. Você pode acessar esse grupo de configurações por intermédio do objeto Properties.Settings.  
  
## <a name="see-also"></a>Consulte também  
 [Usando configurações do aplicativo e configurações do usuário](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Visão Geral das Configurações do Aplicativo](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
