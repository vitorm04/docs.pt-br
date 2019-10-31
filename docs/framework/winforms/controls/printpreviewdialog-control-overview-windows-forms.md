---
title: Visão geral do controle PrintPreviewDialog (Windows Forms)
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
ms.openlocfilehash: 670886956e1b348895862c117ccf9cf586bde8bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141223"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="bdb6c-102">Visão geral do controle PrintPreviewDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="bdb6c-102">PrintPreviewDialog control overview (Windows Forms)</span></span>

<span data-ttu-id="bdb6c-103">O controle de <xref:System.Windows.Forms.PrintPreviewDialog> de Windows Forms é uma caixa de diálogo pré-configurada usada para exibir como um [documento](printdocument-component-windows-forms.md) impresso será exibido na impressão.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="bdb6c-104">Use-o em seu aplicativo baseado no Windows como uma solução simples em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="bdb6c-105">O controle contém botões para imprimir, aumentar o zoom, exibir uma ou várias páginas e fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="bdb6c-106">Propriedades e métodos de chave</span><span class="sxs-lookup"><span data-stu-id="bdb6c-106">Key properties and methods</span></span>

<span data-ttu-id="bdb6c-107">A propriedade de chave do controle é <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, que define o documento a ser visualizado.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="bdb6c-108">O documento deve ser um objeto <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="bdb6c-109">Para exibir a caixa de diálogo, você deve chamar seu método <xref:System.Windows.Forms.Form.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="bdb6c-110">A suavização de serrilhado pode fazer com que o texto pareça mais suave, mas também pode tornar a tela mais lenta; para usá-lo, defina a propriedade <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>

<span data-ttu-id="bdb6c-111">Determinadas propriedades estão disponíveis por meio do <xref:System.Windows.Forms.PrintPreviewControl> que o <xref:System.Windows.Forms.PrintPreviewDialog> contém.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="bdb6c-112">(Você não precisa adicionar esse <xref:System.Windows.Forms.PrintPreviewControl> ao formulário; ele é automaticamente contido na <xref:System.Windows.Forms.PrintPreviewDialog> quando você adiciona a caixa de diálogo ao formulário.) Exemplos de propriedades disponíveis por meio de <xref:System.Windows.Forms.PrintPreviewControl> são as propriedades <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> e <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>, que determinam o número de páginas exibidas horizontal e verticalmente no controle.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="bdb6c-113">Você pode acessar a propriedade <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> como `PrintPreviewDialog1.PrintPreviewControl.Columns` em Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` no Visual C#ou `printPreviewDialog1->PrintPreviewControl->Columns` no Visual C++.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` in Visual C#, or `printPreviewDialog1->PrintPreviewControl->Columns` in Visual C++.</span></span>

## <a name="printpreviewdialog-performance"></a><span data-ttu-id="bdb6c-114">Desempenho do PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="bdb6c-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="bdb6c-115">Sob as condições a seguir, o controle de <xref:System.Windows.Forms.PrintPreviewDialog> Inicializa muito lentamente:</span><span class="sxs-lookup"><span data-stu-id="bdb6c-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="bdb6c-116">Uma impressora de rede é usada.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-116">A network printer is used.</span></span>
- <span data-ttu-id="bdb6c-117">As preferências do usuário para essa impressora, como configurações de duplex, são modificadas.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-117">User preferences for this printer, such as duplex settings, are modified.</span></span>

<span data-ttu-id="bdb6c-118">Para aplicativos em execução no .NET Framework 4.5.2, você pode adicionar a chave a seguir à seção \<appSettings > do arquivo de configuração para melhorar o desempenho da inicialização do controle de <xref:System.Windows.Forms.PrintPreviewDialog>:</span><span class="sxs-lookup"><span data-stu-id="bdb6c-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

<span data-ttu-id="bdb6c-119">Se a chave de `EnablePrintPreviewOptimization` for definida como qualquer outro valor, ou se a chave não estiver presente, a otimização não será aplicada.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="bdb6c-120">Para aplicativos em execução no .NET Framework 4,6 ou versões posteriores, você pode adicionar a opção a seguir para o elemento [\<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [> do tempo de execução\<](../../configure-apps/file-schema/runtime/index.md) do seu arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="bdb6c-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

<span data-ttu-id="bdb6c-121">Se a opção não estiver presente ou se estiver definida como qualquer outro valor, a otimização não será aplicada.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span>

<span data-ttu-id="bdb6c-122">Se você usar o evento <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> para modificar as configurações da impressora, o desempenho do controle de <xref:System.Windows.Forms.PrintPreviewDialog> não será melhorado mesmo se uma opção de configuração de otimização for definida.</span><span class="sxs-lookup"><span data-stu-id="bdb6c-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdb6c-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdb6c-123">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [<span data-ttu-id="bdb6c-124">Visão geral do controle PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="bdb6c-124">PrintPreviewControl Control Overview</span></span>](printpreviewcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="bdb6c-125">Controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="bdb6c-125">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="bdb6c-126">Controles e componentes da caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="bdb6c-126">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
