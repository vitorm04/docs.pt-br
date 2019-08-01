---
title: 'Como: ler configurações em tempo de execução com C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 6a40718d57fad4041eeea2fded03b7256abbe8d1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710222"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="c44e7-102">Como: Ler configurações em tempo de execução com C\#</span><span class="sxs-lookup"><span data-stu-id="c44e7-102">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="c44e7-103">Você pode ler as configurações no escopo do aplicativo e no escopo do usuário em tempo de execução por meio do objeto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="c44e7-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="c44e7-104">O objeto Properties expõe todas as configurações padrão do projeto por meio do membro Properties. Settings. default no namespace padrão do projeto em que estão definidas.</span><span class="sxs-lookup"><span data-stu-id="c44e7-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member in the default namespace of the project they are defined in.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="c44e7-105">Para ler as configurações em tempo de execução com C\#</span><span class="sxs-lookup"><span data-stu-id="c44e7-105">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="c44e7-106">Acesse a configuração apropriada por meio do membro Propriedades. Settings. default.</span><span class="sxs-lookup"><span data-stu-id="c44e7-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="c44e7-107">O exemplo a seguir mostra como atribuir uma configuração chamada `myColor` a uma propriedade BackColor.</span><span class="sxs-lookup"><span data-stu-id="c44e7-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="c44e7-108">Ele requer que você tenha criado anteriormente um arquivo de configurações que contém uma `myColor` configuração nomeada `System.Drawing.Color`do tipo.</span><span class="sxs-lookup"><span data-stu-id="c44e7-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="c44e7-109">Para obter informações sobre como criar um arquivo de [configurações, consulte Como: Crie uma nova configuração em tempo](how-to-create-a-new-setting-at-design-time.md)de design.</span><span class="sxs-lookup"><span data-stu-id="c44e7-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="c44e7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c44e7-110">See also</span></span>

- [<span data-ttu-id="c44e7-111">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="c44e7-111">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="c44e7-112">Como: Gravar configurações de usuário em tempo de execução comC#</span><span class="sxs-lookup"><span data-stu-id="c44e7-112">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="c44e7-113">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="c44e7-113">Application Settings Overview</span></span>](application-settings-overview.md)
