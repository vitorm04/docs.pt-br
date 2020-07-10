---
title: Como adicionar vários conjuntos de configurações a um aplicativo em C#
description: Saiba como adicionar vários conjuntos de configurações de Windows Forms ao seu aplicativo em C# usando o Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 579374ff101758b3224bc122c46b891280ed2609
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173439"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="0a778-103">Como: adicionar vários conjuntos de configurações ao seu aplicativo em C\#</span><span class="sxs-lookup"><span data-stu-id="0a778-103">How To: Add Multiple Sets of Settings To Your Application in C\#</span></span>

<span data-ttu-id="0a778-104">Em alguns casos, convém ter vários conjuntos de configurações em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0a778-104">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="0a778-105">Por exemplo, se você estiver desenvolvendo um aplicativo no qual se supõe que um determinado grupo de configurações deve ser alterado com frequência, talvez seja mais inteligente separá-las em um único arquivo, de modo que esse arquivo possa ser substituído em massa sem que as demais configurações sejam afetadas.</span><span class="sxs-lookup"><span data-stu-id="0a778-105">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="0a778-106">O Visual Studio lhe permite adicionar vários conjuntos de configurações ao projeto.</span><span class="sxs-lookup"><span data-stu-id="0a778-106">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="0a778-107">Conjuntos de configurações adicionais podem ser acessados por meio do `Properties.Settings` objeto.</span><span class="sxs-lookup"><span data-stu-id="0a778-107">Additional sets of settings can be accessed via the `Properties.Settings` object.</span></span>

## <a name="add-an-additional-set-of-settings"></a><span data-ttu-id="0a778-108">Adicionar um conjunto adicional de configurações</span><span class="sxs-lookup"><span data-stu-id="0a778-108">Add an Additional Set of Settings</span></span>

1. <span data-ttu-id="0a778-109">No Visual Studio, no menu **projeto** , escolha **Adicionar novo item**.</span><span class="sxs-lookup"><span data-stu-id="0a778-109">In Visual Studio, from the **Project** menu, choose **Add New Item**.</span></span>

   <span data-ttu-id="0a778-110">A caixa de diálogo **Adicionar Novo Item** é aberta.</span><span class="sxs-lookup"><span data-stu-id="0a778-110">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="0a778-111">Na caixa de diálogo **Adicionar novo item** , selecione **arquivo de configurações**, insira um nome para o arquivo e clique em **Adicionar** para adicionar um novo arquivo de configurações à sua solução.</span><span class="sxs-lookup"><span data-stu-id="0a778-111">In the **Add New Item** dialog box, select **Settings File**, enter a name for the file, and click **Add** to add a new settings file to your solution.</span></span>

3. <span data-ttu-id="0a778-112">No **Gerenciador de Soluções**, arraste o novo arquivo de configurações para a pasta **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="0a778-112">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="0a778-113">Isso faz com que as suas novas configurações fiquem disponíveis no código.</span><span class="sxs-lookup"><span data-stu-id="0a778-113">This allows your new settings to be available in code.</span></span>

4. <span data-ttu-id="0a778-114">Adicione e use configurações nesse arquivo da mesma forma que faria em qualquer outro arquivo de configurações.</span><span class="sxs-lookup"><span data-stu-id="0a778-114">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="0a778-115">Você pode acessar esse grupo de configurações por meio do `Properties.Settings` objeto.</span><span class="sxs-lookup"><span data-stu-id="0a778-115">You can access this group of settings via the `Properties.Settings` object.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a778-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="0a778-116">See also</span></span>

- [<span data-ttu-id="0a778-117">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="0a778-117">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="0a778-118">Visão geral das configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="0a778-118">Application Settings Overview</span></span>](application-settings-overview.md)
