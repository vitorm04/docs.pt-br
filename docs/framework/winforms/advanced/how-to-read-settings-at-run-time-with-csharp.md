---
title: 'Como: ler configurações em tempo de execução com C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8cdc1a79f1ab327ae037cd6a04aa769196405127
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966891"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="dc118-102">Como: Ler configurações em tempo de execução c\#</span><span class="sxs-lookup"><span data-stu-id="dc118-102">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="dc118-103">Você pode ler as configurações de escopo do aplicativo tanto no escopo do usuário em tempo de execução por meio do objeto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="dc118-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="dc118-104">O objeto de propriedades expõe todas as configurações padrão para o projeto por meio do membro Properties.</span><span class="sxs-lookup"><span data-stu-id="dc118-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="dc118-105">Para ler configurações em tempo de execução c\#</span><span class="sxs-lookup"><span data-stu-id="dc118-105">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="dc118-106">Acesse a configuração apropriada por meio do membro Properties.</span><span class="sxs-lookup"><span data-stu-id="dc118-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="dc118-107">O exemplo a seguir mostra como atribuir uma configuração chamada `myColor` a uma propriedade BackColor.</span><span class="sxs-lookup"><span data-stu-id="dc118-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="dc118-108">Exige que você criou anteriormente um arquivo de configurações que contém uma configuração denominada `myColor` do tipo `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="dc118-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="dc118-109">Para obter informações sobre como criar um arquivo de configurações, consulte [How To: Criar uma nova configuração em tempo de Design](how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="dc118-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc118-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc118-110">See also</span></span>

- [<span data-ttu-id="dc118-111">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="dc118-111">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="dc118-112">Como: Gravar configurações do usuário em tempo de execução comC#</span><span class="sxs-lookup"><span data-stu-id="dc118-112">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="dc118-113">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="dc118-113">Application Settings Overview</span></span>](application-settings-overview.md)
