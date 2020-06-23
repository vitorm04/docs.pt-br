---
title: Usando configurações do aplicativo e configurações do usuário
ms.date: 03/30/2017
description: Saiba como usar configurações de aplicativo e configurações de usuário para criar e acessar valores que são persistidos entre sessões de execução de aplicativo.
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
ms.openlocfilehash: a30fd354986265eca002fce57bccf5b3bb2adc15
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903162"
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="46aa2-103">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="46aa2-103">Using Application Settings and User Settings</span></span>
<span data-ttu-id="46aa2-104">Ao começar com o .NET Framework 2.0, é possível criar e acessar valores mantidos entre as sessões de execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="46aa2-104">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="46aa2-105">Esses valores são chamados de *configurações*.</span><span class="sxs-lookup"><span data-stu-id="46aa2-105">These values are called *settings*.</span></span> <span data-ttu-id="46aa2-106">Configurações podem representar preferências do usuário ou informações valiosas que o aplicativo precisar usar.</span><span class="sxs-lookup"><span data-stu-id="46aa2-106">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="46aa2-107">Por exemplo, é possível criar uma série de configurações que armazenam as preferências do usuário para o esquema de cores de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="46aa2-107">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="46aa2-108">Ou, então, você pode armazenar a cadeia de conexão que especifica um banco de dados usado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="46aa2-108">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="46aa2-109">As configurações lhe permitem manter informações críticas ao aplicativo fora do código e criar perfis que armazenam as preferências dos usuários individualmente.</span><span class="sxs-lookup"><span data-stu-id="46aa2-109">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="46aa2-110">Os tópicos nesta seção descrevem como usar as configurações no tempo de design e tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="46aa2-110">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46aa2-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="46aa2-111">In This Section</span></span>  
 [<span data-ttu-id="46aa2-112">Como criar uma nova configuração em tempo de design</span><span class="sxs-lookup"><span data-stu-id="46aa2-112">How To: Create a New Setting at Design Time</span></span>](how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="46aa2-113">Explica como usar o Visual Studio para criar uma nova configuração para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="46aa2-113">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="46aa2-114">Como Alterar o Valor de uma Configuração Existente em Tempo de Design</span><span class="sxs-lookup"><span data-stu-id="46aa2-114">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="46aa2-115">Descreve como usar o Visual Studio para alterar o valor de uma configuração existente.</span><span class="sxs-lookup"><span data-stu-id="46aa2-115">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="46aa2-116">Como alterar o valor de uma configuração entre sessões do aplicativo</span><span class="sxs-lookup"><span data-stu-id="46aa2-116">How To: Change the Value of a Setting Between Application Sessions</span></span>](how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="46aa2-117">Detalha como alterar o valor de uma configuração em um aplicativo compilado entre sessões do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="46aa2-117">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="46aa2-118">Como ler configurações em tempo de execução com C#</span><span class="sxs-lookup"><span data-stu-id="46aa2-118">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="46aa2-119">Descreve como usar código para ler as configurações com c#.</span><span class="sxs-lookup"><span data-stu-id="46aa2-119">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="46aa2-120">Como gravar configurações do usuário em tempo de execução com C#</span><span class="sxs-lookup"><span data-stu-id="46aa2-120">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="46aa2-121">Explica como usar o código para gravar e salvar os valores das configurações do usuário com c#.</span><span class="sxs-lookup"><span data-stu-id="46aa2-121">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="46aa2-122">Como adicionar vários conjuntos de configurações a um aplicativo em C#</span><span class="sxs-lookup"><span data-stu-id="46aa2-122">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="46aa2-123">Detalha como adicionar vários conjuntos de configurações a um aplicativo em C#.</span><span class="sxs-lookup"><span data-stu-id="46aa2-123">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46aa2-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="46aa2-124">See also</span></span>

- [<span data-ttu-id="46aa2-125">Configurações do aplicativo para Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46aa2-125">Application Settings for Windows Forms</span></span>](application-settings-for-windows-forms.md)
