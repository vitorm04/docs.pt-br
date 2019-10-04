---
title: 'Como: Exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas'
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86ec8f9ae76f010ebbc3be393d8d257ba5cfc6b6
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834619"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="4892d-102">Como: Exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas</span><span class="sxs-lookup"><span data-stu-id="4892d-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>

<span data-ttu-id="4892d-103">À medida que desenvolver e distribuir controles, talvez você queira que esses controles apareçam na caixa de diálogo **escolher itens da Toolbox** do Visual Studio, que é exibido quando você clica com o botão direito do mouse na **Toolbox** e seleciona **escolher itens**.</span><span class="sxs-lookup"><span data-stu-id="4892d-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box of Visual Studio, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="4892d-104">Você pode permitir que seu controle apareça na caixa de diálogo usando o procedimento de registro AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="4892d-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>

<span data-ttu-id="4892d-105">Para exibir seu controle na caixa de diálogo escolher itens de caixa de ferramentas:</span><span class="sxs-lookup"><span data-stu-id="4892d-105">To display your control in the Choose Toolbox Items dialog box:</span></span>

- <span data-ttu-id="4892d-106">Instale o assembly do controle no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="4892d-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="4892d-107">Para obter mais informações, confira [Como: Instalar um assembly no cache de assembly global](../../app-domains/install-assembly-into-gac.md).</span><span class="sxs-lookup"><span data-stu-id="4892d-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../app-domains/install-assembly-into-gac.md).</span></span>

  <span data-ttu-id="4892d-108">- ou -</span><span class="sxs-lookup"><span data-stu-id="4892d-108">-or-</span></span>

- <span data-ttu-id="4892d-109">Registre o controle e assemblies de tempo de design associados usando o procedimento de registro AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="4892d-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="4892d-110">AssemblyFoldersEx é um local de Registro em que os fornecedores de terceiros armazenam caminhos para cada versão da estrutura à qual dão suporte.</span><span class="sxs-lookup"><span data-stu-id="4892d-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="4892d-111">A resolução de tempo de design pode procurar neste local do Registro para localizar assemblies de referência.</span><span class="sxs-lookup"><span data-stu-id="4892d-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="4892d-112">O script de Registro pode especificar os controles que deseja que apareçam na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="4892d-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="4892d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4892d-113">See also</span></span>

- [<span data-ttu-id="4892d-114">Desenvolvendo controles dos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="4892d-114">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="4892d-115">Como: Instalar um assembly no cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="4892d-115">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../app-domains/install-assembly-into-gac.md)
- [<span data-ttu-id="4892d-116">Passo a passo: Populando automaticamente a caixa de ferramentas com componentes personalizados</span><span class="sxs-lookup"><span data-stu-id="4892d-116">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
