---
title: "Como ler configurações em tempo de execução com C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c23fd88d33ff4ca480c435f2058f4c568320578
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="8e917-102">Como ler configurações em tempo de execução com C#</span><span class="sxs-lookup"><span data-stu-id="8e917-102">How To: Read Settings at Run Time With C#</span></span> #
<span data-ttu-id="8e917-103">Você pode ler as configurações no escopo do aplicativo tanto no escopo do usuário em tempo de execução por meio do objeto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="8e917-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="8e917-104">O objeto de propriedades expõe todas as configurações padrão do projeto por meio do membro Properties.Settings.Default.</span><span class="sxs-lookup"><span data-stu-id="8e917-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
### <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="8e917-105">Leitura de configurações em tempo de execução com c#</span><span class="sxs-lookup"><span data-stu-id="8e917-105">To Read Settings at Run Time with C#</span></span>  
  
-   <span data-ttu-id="8e917-106">Acesse a configuração apropriada por meio do membro Properties.Settings.Default.</span><span class="sxs-lookup"><span data-stu-id="8e917-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="8e917-107">O exemplo a seguir mostra como atribuir uma configuração denominada `myColor` a uma propriedade BackColor.</span><span class="sxs-lookup"><span data-stu-id="8e917-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="8e917-108">Requer que você criou anteriormente um arquivo de configurações que contém uma configuração denominada `myColor` do tipo `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="8e917-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="8e917-109">Para obter informações sobre como criar um arquivo de configurações, consulte [como: criar uma nova configuração em tempo de Design](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="8e917-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8e917-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e917-110">See Also</span></span>  
 [<span data-ttu-id="8e917-111">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="8e917-111">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="8e917-112">Como Gravar Configurações do Usuário em Tempo de Execução com C#</span><span class="sxs-lookup"><span data-stu-id="8e917-112">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="8e917-113">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="8e917-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
