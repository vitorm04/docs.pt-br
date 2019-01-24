---
title: 'Como: Ler configurações em tempo de execução comC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d798b40e5e337ea7652c8e82cb7fa860a87528b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521745"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="45b4d-102">Como: Ler configurações em tempo de execução comC#</span><span class="sxs-lookup"><span data-stu-id="45b4d-102">How To: Read Settings at Run Time With C#</span></span> #
<span data-ttu-id="45b4d-103">Você pode ler as configurações de escopo do aplicativo tanto no escopo do usuário em tempo de execução por meio do objeto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="45b4d-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="45b4d-104">O objeto de propriedades expõe todas as configurações padrão para o projeto por meio do membro Properties.</span><span class="sxs-lookup"><span data-stu-id="45b4d-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
### <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="45b4d-105">Para ler configurações em tempo de execução comC#</span><span class="sxs-lookup"><span data-stu-id="45b4d-105">To Read Settings at Run Time with C#</span></span>  
  
-   <span data-ttu-id="45b4d-106">Acesse a configuração apropriada por meio do membro Properties.</span><span class="sxs-lookup"><span data-stu-id="45b4d-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="45b4d-107">O exemplo a seguir mostra como atribuir uma configuração chamada `myColor` a uma propriedade BackColor.</span><span class="sxs-lookup"><span data-stu-id="45b4d-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="45b4d-108">Exige que você criou anteriormente um arquivo de configurações que contém uma configuração denominada `myColor` do tipo `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="45b4d-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="45b4d-109">Para obter informações sobre como criar um arquivo de configurações, consulte [How To: Criar uma nova configuração em tempo de Design](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="45b4d-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="45b4d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45b4d-110">See also</span></span>
- [<span data-ttu-id="45b4d-111">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="45b4d-111">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [<span data-ttu-id="45b4d-112">Como: Gravar configurações do usuário em tempo de execução comC#</span><span class="sxs-lookup"><span data-stu-id="45b4d-112">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="45b4d-113">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="45b4d-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
