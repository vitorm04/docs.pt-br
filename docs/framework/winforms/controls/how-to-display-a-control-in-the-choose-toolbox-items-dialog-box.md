---
title: 'Como: Exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas'
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: d504ace9e5571246ae0e78e165a7ad2bc23fa481
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954213"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="79150-102">Como: Exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas</span><span class="sxs-lookup"><span data-stu-id="79150-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>
<span data-ttu-id="79150-103">Ao desenvolver e distribuir controles, é possível fazer com que esses controles apareçam na caixa de diálogo **Escolher itens da caixa de ferramentas** que é exibida quando você clica com o botão direito do mouse na **Caixa de ferramentas** e seleciona **Escolher itens**.</span><span class="sxs-lookup"><span data-stu-id="79150-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="79150-104">Você pode permitir que seu controle apareça na caixa de diálogo usando o procedimento de registro AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="79150-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="79150-105">Para exibir o controle na caixa de diálogo Escolher itens da caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="79150-105">To display your control in the Choose Toolbox Items dialog box</span></span>  
  
- <span data-ttu-id="79150-106">Instale o assembly do controle no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="79150-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="79150-107">Para obter mais informações, confira [Como: Instalar um assembly no cache de assembly global](../../app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="79150-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>  
  
     <span data-ttu-id="79150-108">- ou -</span><span class="sxs-lookup"><span data-stu-id="79150-108">-or-</span></span>  
  
- <span data-ttu-id="79150-109">Registre o controle e assemblies de tempo de design associados usando o procedimento de registro AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="79150-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="79150-110">AssemblyFoldersEx é um local de Registro em que os fornecedores de terceiros armazenam caminhos para cada versão da estrutura à qual dão suporte.</span><span class="sxs-lookup"><span data-stu-id="79150-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="79150-111">A resolução de tempo de design pode procurar neste local do Registro para localizar assemblies de referência.</span><span class="sxs-lookup"><span data-stu-id="79150-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="79150-112">O script de Registro pode especificar os controles que deseja que apareçam na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="79150-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span> <span data-ttu-id="79150-113">Para obter mais informações, consulte [Implantando um controle personalizado e Assemblies de tempo de Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="79150-113">For more information, see [Deploying a Custom Control and Design-time Assemblies](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79150-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79150-114">See also</span></span>

- <span data-ttu-id="79150-115">[Caixa de diálogo Escolher Itens da Caixa de Ferramentas (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="79150-115">[Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span></span>
- <span data-ttu-id="79150-116">[Implantando um controle personalizado e Assemblies de tempo de Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="79150-116">[Deploying a Custom Control and Design-time Assemblies](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))</span></span>
- [<span data-ttu-id="79150-117">Desenvolvendo controles dos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="79150-117">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="79150-118">Como: Instalar um assembly no cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="79150-118">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [<span data-ttu-id="79150-119">Passo a passo: Preenchendo automaticamente a caixa de ferramentas com componentes personalizados</span><span class="sxs-lookup"><span data-stu-id="79150-119">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
