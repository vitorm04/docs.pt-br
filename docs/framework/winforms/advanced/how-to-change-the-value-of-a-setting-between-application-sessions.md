---
title: "Como alterar o valor de uma configuração entre sessões do aplicativo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c00e61001d9c8877b1fcaa0e938c92249c7915e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="5b24a-102">Como alterar o valor de uma configuração entre sessões do aplicativo</span><span class="sxs-lookup"><span data-stu-id="5b24a-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="5b24a-103">Às vezes, você talvez queira alterar o valor de uma configuração entre sessões do aplicativo depois que o aplicativo foi compilado e implantado.</span><span class="sxs-lookup"><span data-stu-id="5b24a-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="5b24a-104">Por exemplo, convém alterar uma cadeia de caracteres de conexão para apontar para o local do banco de dados correto.</span><span class="sxs-lookup"><span data-stu-id="5b24a-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="5b24a-105">Como as ferramentas de tempo de design não estão disponíveis depois que o aplicativo foi compilado e implantado, você deve alterar o valor da configuração manualmente no arquivo.</span><span class="sxs-lookup"><span data-stu-id="5b24a-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="5b24a-106">Para alterar o valor de uma configuração entre sessões do aplicativo</span><span class="sxs-lookup"><span data-stu-id="5b24a-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1.  <span data-ttu-id="5b24a-107">Usando o Microsoft Notepad ou algum outro editor de texto ou XML, abra o arquivo. config associado ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5b24a-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2.  <span data-ttu-id="5b24a-108">Localize a entrada para a configuração que você deseja alterar.</span><span class="sxs-lookup"><span data-stu-id="5b24a-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="5b24a-109">Ela deve ser semelhante ao exemplo apresentado abaixo.</span><span class="sxs-lookup"><span data-stu-id="5b24a-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  <span data-ttu-id="5b24a-110">Digite um novo valor para a sua configuração e salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="5b24a-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b24a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b24a-111">See Also</span></span>  
 [<span data-ttu-id="5b24a-112">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="5b24a-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="5b24a-113">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="5b24a-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
