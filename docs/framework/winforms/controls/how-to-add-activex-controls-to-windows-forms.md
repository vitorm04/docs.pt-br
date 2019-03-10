---
title: 'Como: Adicionar controles ActiveX ao Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 68e25cb2cd7e1f1c63954b20d24f028a49431553
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707983"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="8dc6a-102">Como: Adicionar controles ActiveX ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8dc6a-102">How to: Add ActiveX Controls to Windows Forms</span></span>
<span data-ttu-id="8dc6a-103">Enquanto o Designer de Formulários do Windows é otimizado para hospedar controles dos Windows Forms, também é possível colocar controles ActiveX nos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8dc6a-103">While the Windows Forms Designer is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8dc6a-104">Há limitações de desempenho para o Windows Forms quando os controles ActiveX são adicionados a ele.</span><span class="sxs-lookup"><span data-stu-id="8dc6a-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>  
  
 <span data-ttu-id="8dc6a-105">Antes de adicionar controles ActiveX ao seu formulário, você deve adicioná-los à caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="8dc6a-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="8dc6a-106">Para obter mais informações, consulte [Componentes COM, Caixa de diálogo Personalizar caixa de ferramentas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8dc6a-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dc6a-107">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="8dc6a-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8dc6a-108">Para alterar as configurações, clique em **Importar e exportar configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="8dc6a-108">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8dc6a-109">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="8dc6a-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="8dc6a-110">Para adicionar um controle ActiveX ao seu Windows Form</span><span class="sxs-lookup"><span data-stu-id="8dc6a-110">To add an ActiveX control to your Windows Form</span></span>  
  
-   <span data-ttu-id="8dc6a-111">Clique duas vezes no controle na Caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="8dc6a-111">Double-click the control on the Toolbox.</span></span>  
  
     <span data-ttu-id="8dc6a-112">Visual Studio adiciona todas as referências ao controle em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="8dc6a-112">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="8dc6a-113">Para obter mais informações sobre as coisas para ter em mente ao usar controles ActiveX nos Windows Forms, consulte [Considerações sobre quando hospedar um controle ActiveX em um Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="8dc6a-113">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8dc6a-114">O Importador de controle ActiveX dos Windows Forms (AxImp.exe) cria os argumentos de evento de um tipo diferente do que o esperado após a importação de bibliotecas de link dinâmico do ActiveX.</span><span class="sxs-lookup"><span data-stu-id="8dc6a-114">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="8dc6a-115">Os argumentos criados pelo AxImp.exe são semelhantes ao seguinte: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, quando `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` for esperado.</span><span class="sxs-lookup"><span data-stu-id="8dc6a-115">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="8dc6a-116">Lembre-se de que essa irregularidade não impede que o código funcione normalmente.</span><span class="sxs-lookup"><span data-stu-id="8dc6a-116">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="8dc6a-117">Para obter detalhes, consulte [Importador de Controle ActiveX dos Windows Forms (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="8dc6a-117">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc6a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8dc6a-118">See also</span></span>
- [<span data-ttu-id="8dc6a-119">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8dc6a-119">Windows Forms Controls</span></span>](index.md)
- <span data-ttu-id="8dc6a-120">[Controles e objetos programáveis comparados em diversas linguagens e bibliotecas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8dc6a-120">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="8dc6a-121">Como: Adicionar controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8dc6a-121">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="8dc6a-122">Organizando Controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8dc6a-122">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="8dc6a-123">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="8dc6a-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="8dc6a-124">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8dc6a-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="8dc6a-125">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="8dc6a-125">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
