---
title: 'Como: Gravar configurações do usuário em tempo de execução comC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: a62bf540ebdc383f26bd4aed760b2562437047aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560927"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="a78bc-102">Como: Gravar configurações do usuário em tempo de execução comC#</span><span class="sxs-lookup"><span data-stu-id="a78bc-102">How To: Write User Settings at Run Time with C#</span></span> #
<span data-ttu-id="a78bc-103">As configurações que estão no escopo do aplicativo são somente leitura e só podem ser alteradas em tempo de design ou alterando o arquivo. config entre sessões do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a78bc-103">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="a78bc-104">Configurações que estão no escopo do usuário, no entanto, podem ser gravadas em tempo de execução assim como você alteraria qualquer valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="a78bc-104">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="a78bc-105">O novo valor será mantido enquanto durar a sessão do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a78bc-105">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="a78bc-106">Você pode persistir as alterações das configurações entre sessões do aplicativo chamando o método Save.</span><span class="sxs-lookup"><span data-stu-id="a78bc-106">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="a78bc-107">Como: Gravar e manter as configurações do usuário em tempo de execução comC#</span><span class="sxs-lookup"><span data-stu-id="a78bc-107">How To: Write and Persist User Settings at Run Time with C#</span></span>  
  
1.  <span data-ttu-id="a78bc-108">Acesse a configuração e atribuir um novo valor conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="a78bc-108">Access the setting and assign it a new value as shown in this example:</span></span>  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  <span data-ttu-id="a78bc-109">Se você quiser manter as alterações das configurações entre sessões do aplicativo, chame o método Save conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="a78bc-109">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     <span data-ttu-id="a78bc-110">Configurações de usuário são salvas em um arquivo em uma subpasta da pasta de dados do aplicativo oculto local do usuário.</span><span class="sxs-lookup"><span data-stu-id="a78bc-110">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a78bc-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a78bc-111">See also</span></span>
- [<span data-ttu-id="a78bc-112">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="a78bc-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [<span data-ttu-id="a78bc-113">Como: Ler configurações em tempo de execução comC#</span><span class="sxs-lookup"><span data-stu-id="a78bc-113">How To: Read Settings at Run Time With C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="a78bc-114">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="a78bc-114">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
