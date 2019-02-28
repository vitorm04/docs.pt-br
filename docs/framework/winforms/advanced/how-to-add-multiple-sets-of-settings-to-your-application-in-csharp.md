---
title: 'Como: Adicionar vários conjuntos de configurações para seu aplicativo noC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 447d171cf9dbe2672ae138e9e902cbd72a206c94
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969629"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="462f1-102">Como: Adicionar vários conjuntos de configurações ao seu aplicativo em C\#</span><span class="sxs-lookup"><span data-stu-id="462f1-102">How To: Add Multiple Sets of Settings To Your Application in C\#</span></span>
<span data-ttu-id="462f1-103">Em alguns casos, convém ter vários conjuntos de configurações em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="462f1-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="462f1-104">Por exemplo, se você estiver desenvolvendo um aplicativo no qual se supõe que um determinado grupo de configurações deve ser alterado com frequência, talvez seja mais inteligente separá-las em um único arquivo, de modo que esse arquivo possa ser substituído em massa sem que as demais configurações sejam afetadas.</span><span class="sxs-lookup"><span data-stu-id="462f1-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="462f1-105">O Visual Studio lhe permite adicionar vários conjuntos de configurações ao projeto.</span><span class="sxs-lookup"><span data-stu-id="462f1-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="462f1-106">Conjuntos de configurações adicionais podem ser acessados através do objeto Properties.Settings.</span><span class="sxs-lookup"><span data-stu-id="462f1-106">Additional sets of settings can be accessed via the Properties.Settings object.</span></span>  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a><span data-ttu-id="462f1-107">Para adicionar um conjunto de configurações adicional ao aplicativo</span><span class="sxs-lookup"><span data-stu-id="462f1-107">To Add an Additional Set of Setting to your Application</span></span>  
  
1.  <span data-ttu-id="462f1-108">No menu **Projeto**, escolha **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="462f1-108">From the **Project** menu, choose **Add New Item**.</span></span> <span data-ttu-id="462f1-109">A caixa de diálogo **Adicionar Novo Item** é aberta.</span><span class="sxs-lookup"><span data-stu-id="462f1-109">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="462f1-110">Na caixa de diálogo **Adicionar Novo Item**, selecione **Arquivo de Configurações**, digite um nome para o arquivo e clique em **Adicionar** para adicionar um novo arquivo de configurações à sua solução.</span><span class="sxs-lookup"><span data-stu-id="462f1-110">In the **Add New Item** dialog box, select **Settings File**, type in a name for the file, and click **Add** to add a new settings file to your solution.</span></span>  
  
3.  <span data-ttu-id="462f1-111">No **Gerenciador de Soluções**, arraste o novo arquivo de configurações para a pasta **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="462f1-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="462f1-112">Isso faz com que as suas novas configurações fiquem disponíveis no código.</span><span class="sxs-lookup"><span data-stu-id="462f1-112">This allows your new settings to be available in code.</span></span>  
  
4.  <span data-ttu-id="462f1-113">Adicione e use configurações nesse arquivo da mesma forma que faria em qualquer outro arquivo de configurações.</span><span class="sxs-lookup"><span data-stu-id="462f1-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="462f1-114">Você pode acessar esse grupo de configurações por intermédio do objeto Properties.Settings.</span><span class="sxs-lookup"><span data-stu-id="462f1-114">You can access this group of settings via the Properties.Settings object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="462f1-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="462f1-115">See also</span></span>
- [<span data-ttu-id="462f1-116">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="462f1-116">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [<span data-ttu-id="462f1-117">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="462f1-117">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
