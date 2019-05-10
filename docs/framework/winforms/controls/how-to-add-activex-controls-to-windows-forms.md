---
title: 'Como: Adicionar controles do ActiveX ao Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 17311adade187ef3c8e4e639299e6c5cbbcd98a9
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210385"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="e6f2f-102">Como: Adicionar controles do ActiveX ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6f2f-102">How to: Add ActiveX Controls to Windows Forms</span></span>

<span data-ttu-id="e6f2f-103">Enquanto o Designer de formulários do Windows no Visual Studio é otimizado para hospedar controles dos Windows Forms, você também pode colocar controles ActiveX nos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e6f2f-103">While the Windows Forms Designer in Visual Studio is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>

> [!CAUTION]
> <span data-ttu-id="e6f2f-104">Há limitações de desempenho para o Windows Forms quando os controles ActiveX são adicionados a ele.</span><span class="sxs-lookup"><span data-stu-id="e6f2f-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>

<span data-ttu-id="e6f2f-105">Antes de adicionar controles ActiveX ao seu formulário, você deve adicioná-los à caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="e6f2f-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="e6f2f-106">Para obter mais informações, consulte [Componentes COM, Caixa de diálogo Personalizar caixa de ferramentas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e6f2f-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span></span>

## <a name="add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="e6f2f-107">Adicionar um controle ActiveX ao seu formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="e6f2f-107">Add an ActiveX control to your Windows Form</span></span>

<span data-ttu-id="e6f2f-108">Para adicionar um controle ActiveX ao seu formulário do Windows, clique duas vezes o controle na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="e6f2f-108">To add an ActiveX control to your Windows Form, double-click the control on the Toolbox.</span></span>

<span data-ttu-id="e6f2f-109">Visual Studio adiciona todas as referências ao controle em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="e6f2f-109">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="e6f2f-110">Para obter mais informações sobre as coisas para ter em mente ao usar controles ActiveX nos Windows Forms, consulte [Considerações sobre quando hospedar um controle ActiveX em um Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="e6f2f-110">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e6f2f-111">O Importador de controle ActiveX dos Windows Forms (AxImp.exe) cria os argumentos de evento de um tipo diferente do que o esperado após a importação de bibliotecas de link dinâmico do ActiveX.</span><span class="sxs-lookup"><span data-stu-id="e6f2f-111">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="e6f2f-112">Os argumentos criados pelo AxImp.exe são semelhantes ao seguinte: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, quando `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` for esperado.</span><span class="sxs-lookup"><span data-stu-id="e6f2f-112">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="e6f2f-113">Lembre-se de que essa irregularidade não impede que o código funcione normalmente.</span><span class="sxs-lookup"><span data-stu-id="e6f2f-113">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="e6f2f-114">Para obter detalhes, consulte [Importador de Controle ActiveX dos Windows Forms (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="e6f2f-114">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e6f2f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6f2f-115">See also</span></span>

- [<span data-ttu-id="e6f2f-116">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6f2f-116">Windows Forms Controls</span></span>](index.md)
- <span data-ttu-id="e6f2f-117">[Controles e objetos programáveis comparados em diversas linguagens e bibliotecas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e6f2f-117">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="e6f2f-118">Como: Adicionar controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6f2f-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="e6f2f-119">Organizando Controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6f2f-119">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="e6f2f-120">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="e6f2f-120">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="e6f2f-121">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6f2f-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="e6f2f-122">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="e6f2f-122">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
