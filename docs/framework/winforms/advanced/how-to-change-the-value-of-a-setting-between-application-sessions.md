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
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="bbeda-102">Como alterar o valor de uma configuração entre sessões do aplicativo</span><span class="sxs-lookup"><span data-stu-id="bbeda-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="bbeda-103">Às vezes, você talvez queira alterar o valor de uma configuração entre sessões do aplicativo depois que o aplicativo foi compilado e implantado.</span><span class="sxs-lookup"><span data-stu-id="bbeda-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="bbeda-104">Por exemplo, convém alterar uma cadeia de caracteres de conexão para apontar para o local do banco de dados correto.</span><span class="sxs-lookup"><span data-stu-id="bbeda-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="bbeda-105">Como as ferramentas de tempo de design não estão disponíveis depois que o aplicativo foi compilado e implantado, você deve alterar o valor da configuração manualmente no arquivo.</span><span class="sxs-lookup"><span data-stu-id="bbeda-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="bbeda-106">Para alterar o valor de uma configuração entre sessões do aplicativo</span><span class="sxs-lookup"><span data-stu-id="bbeda-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1.  <span data-ttu-id="bbeda-107">Usando o Microsoft Notepad ou algum outro editor de texto ou XML, abra o arquivo. config associado ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bbeda-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2.  <span data-ttu-id="bbeda-108">Localize a entrada para a configuração que você deseja alterar.</span><span class="sxs-lookup"><span data-stu-id="bbeda-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="bbeda-109">Ela deve ser semelhante ao exemplo apresentado abaixo.</span><span class="sxs-lookup"><span data-stu-id="bbeda-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  <span data-ttu-id="bbeda-110">Digite um novo valor para a sua configuração e salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="bbeda-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbeda-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbeda-111">See Also</span></span>  
 [<span data-ttu-id="bbeda-112">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="bbeda-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="bbeda-113">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="bbeda-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
