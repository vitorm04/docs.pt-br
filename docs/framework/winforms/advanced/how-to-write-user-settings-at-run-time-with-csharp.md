---
title: Como gravar configurações do usuário em tempo de execução com C#
description: Saiba como escrever configurações em tempo de execução com C#, mantendo as alterações nas configurações entre sessões de aplicativo chamando o método Save.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 6154ff1b92d6c2d4c788299e59eb8f73e6b69c4b
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904319"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="3629b-103">Como: gravar configurações de usuário em tempo de execução com C\#</span><span class="sxs-lookup"><span data-stu-id="3629b-103">How To: Write User Settings at Run Time with C\#</span></span>

<span data-ttu-id="3629b-104">As configurações com escopo de aplicativo são somente leitura e só podem ser alteradas em tempo de design ou alterando o arquivo. config entre sessões de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3629b-104">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="3629b-105">As configurações que têm escopo de usuário, no entanto, podem ser gravadas em tempo de execução, assim como você alteraria qualquer valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3629b-105">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="3629b-106">O novo valor persiste pela duração da sessão do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3629b-106">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="3629b-107">Você pode manter as alterações nas configurações entre sessões do aplicativo chamando o método Save.</span><span class="sxs-lookup"><span data-stu-id="3629b-107">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="3629b-108">Como: gravar e persistir configurações de usuário em tempo de execução com C\#</span><span class="sxs-lookup"><span data-stu-id="3629b-108">How To: Write and Persist User Settings at Run Time with C\#</span></span>
  
1. <span data-ttu-id="3629b-109">Acesse a configuração e atribua um novo valor, conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="3629b-109">Access the setting and assign it a new value as shown in this example:</span></span>  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. <span data-ttu-id="3629b-110">Se você quiser manter as alterações nas configurações entre as sessões do aplicativo, chame o método Save, conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="3629b-110">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
<span data-ttu-id="3629b-111">As configurações de usuário são salvas em um arquivo dentro de uma subpasta da pasta de dados de aplicativo oculto local do usuário.</span><span class="sxs-lookup"><span data-stu-id="3629b-111">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3629b-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="3629b-112">See also</span></span>

- [<span data-ttu-id="3629b-113">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="3629b-113">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="3629b-114">Como ler configurações em tempo de execução com C#</span><span class="sxs-lookup"><span data-stu-id="3629b-114">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="3629b-115">Visão geral das configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="3629b-115">Application Settings Overview</span></span>](application-settings-overview.md)
