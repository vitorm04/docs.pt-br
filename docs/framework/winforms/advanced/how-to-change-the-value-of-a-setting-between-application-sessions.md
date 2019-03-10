---
title: 'Como: Altere o valor de uma configuração entre sessões do aplicativo'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: c1626cea581e5c180665d0ce805dea3e67f27a05
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714353"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="3db94-102">Como: Altere o valor de uma configuração entre sessões do aplicativo</span><span class="sxs-lookup"><span data-stu-id="3db94-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="3db94-103">Às vezes, você talvez queira alterar o valor de uma configuração entre sessões do aplicativo depois que o aplicativo foi compilado e implantado.</span><span class="sxs-lookup"><span data-stu-id="3db94-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="3db94-104">Por exemplo, você talvez queira alterar uma cadeia de caracteres de conexão para apontar para o local do banco de dados correto.</span><span class="sxs-lookup"><span data-stu-id="3db94-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="3db94-105">Uma vez que as ferramentas de tempo de design não ficam disponíveis depois que o aplicativo foi compilado e implantado, você deve alterar o valor da configuração manualmente no arquivo.</span><span class="sxs-lookup"><span data-stu-id="3db94-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="3db94-106">Para alterar o valor de uma configuração entre sessões do aplicativo</span><span class="sxs-lookup"><span data-stu-id="3db94-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1.  <span data-ttu-id="3db94-107">Usando o Microsoft Notepad ou algum outro texto ou editor XML, abra o arquivo. config associado ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3db94-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2.  <span data-ttu-id="3db94-108">Localize a entrada para a configuração que você deseja alterar.</span><span class="sxs-lookup"><span data-stu-id="3db94-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="3db94-109">Ele deve ser semelhante ao exemplo a apresentada a seguir.</span><span class="sxs-lookup"><span data-stu-id="3db94-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  <span data-ttu-id="3db94-110">Digite um novo valor para a sua configuração e salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="3db94-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db94-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3db94-111">See also</span></span>
- [<span data-ttu-id="3db94-112">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="3db94-112">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="3db94-113">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="3db94-113">Application Settings Overview</span></span>](application-settings-overview.md)
