---
title: 'Como: Adicionar controles do ActiveX ao Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 8c4c6c3f96c49401b032e360314794cc800c0551
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987065"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="be498-102">Como: Adicionar controles do ActiveX ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be498-102">How to: Add ActiveX Controls to Windows Forms</span></span>

<span data-ttu-id="be498-103">Embora o Designer de Formulários do Windows no Visual Studio seja otimizado para hospedar controles de Windows Forms, você também pode colocar controles ActiveX em Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="be498-103">While the Windows Forms Designer in Visual Studio is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>

> [!CAUTION]
> <span data-ttu-id="be498-104">Há limitações de desempenho para o Windows Forms quando os controles ActiveX são adicionados a ele.</span><span class="sxs-lookup"><span data-stu-id="be498-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>

<span data-ttu-id="be498-105">Antes de adicionar controles ActiveX ao seu formulário, você deve adicioná-los à caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="be498-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="be498-106">Para obter mais informações, consulte [Componentes COM, Caixa de diálogo Personalizar caixa de ferramentas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="be498-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span></span>

## <a name="add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="be498-107">Adicionar um controle ActiveX ao seu formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="be498-107">Add an ActiveX control to your Windows Form</span></span>

<span data-ttu-id="be498-108">Para adicionar um controle ActiveX ao seu formulário do Windows, clique duas vezes no controle na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="be498-108">To add an ActiveX control to your Windows Form, double-click the control on the Toolbox.</span></span>

<span data-ttu-id="be498-109">O Visual Studio adiciona todas as referências ao controle em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="be498-109">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="be498-110">Para obter mais informações sobre as coisas para ter em mente ao usar controles ActiveX nos Windows Forms, consulte [Considerações sobre quando hospedar um controle ActiveX em um Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="be498-110">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>

> [!NOTE]
> <span data-ttu-id="be498-111">O Importador de controle ActiveX dos Windows Forms (AxImp.exe) cria os argumentos de evento de um tipo diferente do que o esperado após a importação de bibliotecas de link dinâmico do ActiveX.</span><span class="sxs-lookup"><span data-stu-id="be498-111">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="be498-112">Os argumentos criados pelo AxImp.exe são semelhantes ao seguinte: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, quando `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` for esperado.</span><span class="sxs-lookup"><span data-stu-id="be498-112">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="be498-113">Lembre-se de que essa irregularidade não impede que o código funcione normalmente.</span><span class="sxs-lookup"><span data-stu-id="be498-113">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="be498-114">Para obter detalhes, consulte [Importador de Controle ActiveX dos Windows Forms (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="be498-114">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="be498-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be498-115">See also</span></span>

- [<span data-ttu-id="be498-116">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be498-116">Windows Forms Controls</span></span>](index.md)
- <span data-ttu-id="be498-117">[Controles e objetos programáveis comparados em diversas linguagens e bibliotecas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="be498-117">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="be498-118">Como: Adicionar controles a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be498-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="be498-119">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="be498-119">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="be498-120">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be498-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="be498-121">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="be498-121">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
