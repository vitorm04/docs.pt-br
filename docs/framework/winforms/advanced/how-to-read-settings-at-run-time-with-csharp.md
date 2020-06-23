---
title: Como ler configurações em tempo de execução com C#
description: Saiba como ler as configurações no escopo do aplicativo e no escopo do usuário em tempo de execução com C# por meio do objeto de propriedades.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d784544e018bb693c501e35ea36fcae1946ef5eb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903344"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="3fcc7-103">Como: ler configurações em tempo de execução com C\#</span><span class="sxs-lookup"><span data-stu-id="3fcc7-103">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="3fcc7-104">Você pode ler as configurações no escopo do aplicativo e no escopo do usuário em tempo de execução por meio do objeto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="3fcc7-104">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="3fcc7-105">O objeto Properties expõe todas as configurações padrão do projeto por meio do membro Properties. Settings. default no namespace padrão do projeto em que estão definidas.</span><span class="sxs-lookup"><span data-stu-id="3fcc7-105">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member in the default namespace of the project they are defined in.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="3fcc7-106">Para ler as configurações em tempo de execução com C\#</span><span class="sxs-lookup"><span data-stu-id="3fcc7-106">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="3fcc7-107">Acesse a configuração apropriada por meio do membro Propriedades. Settings. default.</span><span class="sxs-lookup"><span data-stu-id="3fcc7-107">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="3fcc7-108">O exemplo a seguir mostra como atribuir uma configuração chamada `myColor` a uma propriedade BackColor.</span><span class="sxs-lookup"><span data-stu-id="3fcc7-108">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="3fcc7-109">Ele requer que você tenha criado anteriormente um arquivo de configurações que contém uma configuração nomeada `myColor` do tipo `System.Drawing.Color` .</span><span class="sxs-lookup"><span data-stu-id="3fcc7-109">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="3fcc7-110">Para obter informações sobre como criar um arquivo de configurações, consulte [como: criar uma nova configuração em tempo de design](how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="3fcc7-110">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="3fcc7-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="3fcc7-111">See also</span></span>

- [<span data-ttu-id="3fcc7-112">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="3fcc7-112">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="3fcc7-113">Como gravar configurações do usuário em tempo de execução com C#</span><span class="sxs-lookup"><span data-stu-id="3fcc7-113">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="3fcc7-114">Visão geral das configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="3fcc7-114">Application Settings Overview</span></span>](application-settings-overview.md)
