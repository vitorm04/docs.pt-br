---
title: Visão geral do controle PrintPreviewDialog (Windows Forms)
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dce6bf9cb9872183e60e6ccdf7eaf79b6630db51
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053690"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="a1c1b-102">Visão geral do controle PrintPreviewDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a1c1b-102">PrintPreviewDialog control overview (Windows Forms)</span></span>

<span data-ttu-id="a1c1b-103">Os formulários do Windows <xref:System.Windows.Forms.PrintPreviewDialog> controle é uma caixa de diálogo pré-configurada usada para exibir como um [PrintDocument](printdocument-component-windows-forms.md) aparecerá quando impresso.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="a1c1b-104">Use-o em seu aplicativo baseado no Windows como uma solução simples em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="a1c1b-105">O controle contém botões para imprimir, aumentar o zoom, exibir uma ou várias páginas e fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="a1c1b-106">Métodos e propriedades de chave</span><span class="sxs-lookup"><span data-stu-id="a1c1b-106">Key properties and methods</span></span>

<span data-ttu-id="a1c1b-107">Propriedade de chave do controle é <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, que define o documento a ser visualizado.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="a1c1b-108">O documento deve ser um <xref:System.Drawing.Printing.PrintDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="a1c1b-109">Para exibir a caixa de diálogo, você deve chamar seu <xref:System.Windows.Forms.Form.ShowDialog%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="a1c1b-110">A suavização pode tornar o texto mais suave, mas também pode tornar a exibição mais lenta; para usá-lo, defina as <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>

<span data-ttu-id="a1c1b-111">Certas propriedades estão disponíveis por meio de <xref:System.Windows.Forms.PrintPreviewControl> que o <xref:System.Windows.Forms.PrintPreviewDialog> contém.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="a1c1b-112">(Não é preciso adicionar isso <xref:System.Windows.Forms.PrintPreviewControl> ao formulário; ele é automaticamente incluído no <xref:System.Windows.Forms.PrintPreviewDialog> quando você adiciona a caixa de diálogo ao formulário.) Exemplos de propriedades disponíveis por meio de <xref:System.Windows.Forms.PrintPreviewControl> são a <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> e <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> propriedades que determinam o número de páginas exibidas horizontal e verticalmente no controle.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="a1c1b-113">Você pode acessar o <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a propriedade como `PrintPreviewDialog1.PrintPreviewControl.Columns` no Visual Basic `printPreviewDialog1.PrintPreviewControl.Columns` no Visual C#, ou `printPreviewDialog1->PrintPreviewControl->Columns` no Visual C++.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` in Visual C#, or `printPreviewDialog1->PrintPreviewControl->Columns` in Visual C++.</span></span>

## <a name="printpreviewdialog-performance"></a><span data-ttu-id="a1c1b-114">Desempenho PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="a1c1b-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="a1c1b-115">Sob as seguintes condições, o <xref:System.Windows.Forms.PrintPreviewDialog> controle inicializa muito lenta:</span><span class="sxs-lookup"><span data-stu-id="a1c1b-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="a1c1b-116">Uma impressora de rede é usada.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-116">A network printer is used.</span></span>
- <span data-ttu-id="a1c1b-117">As preferências do usuário para essa impressora, como as configurações duplex, são modificadas.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-117">User preferences for this printer, such as duplex settings, are modified.</span></span>

<span data-ttu-id="a1c1b-118">Para aplicativos em execução no .NET Framework 4.5.2, você pode adicionar a seguinte chave para o \<appSettings > seção do arquivo de configuração para melhorar o desempenho de <xref:System.Windows.Forms.PrintPreviewDialog> controlam a inicialização:</span><span class="sxs-lookup"><span data-stu-id="a1c1b-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

<span data-ttu-id="a1c1b-119">Se o `EnablePrintPreviewOptimization` chave é definida como qualquer outro valor, ou se a chave não estiver presente, a otimização não é aplicada.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="a1c1b-120">Para aplicativos em execução no .NET Framework 4.6 ou versões posteriores, você pode adicionar a seguinte opção para o [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elemento no [ \<tempo de execução >](../../configure-apps/file-schema/runtime/index.md) seção do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="a1c1b-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

<span data-ttu-id="a1c1b-121">Se a opção não estiver presente ou se ele for definido como qualquer outro valor, a otimização não é aplicada.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span>

<span data-ttu-id="a1c1b-122">Se você usar o <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> evento para modificar as configurações de impressora, o desempenho do <xref:System.Windows.Forms.PrintPreviewDialog> controle não melhorará o mesmo que uma opção de configuração de otimização é definida.</span><span class="sxs-lookup"><span data-stu-id="a1c1b-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1c1b-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1c1b-123">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [<span data-ttu-id="a1c1b-124">Visão geral do controle PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="a1c1b-124">PrintPreviewControl Control Overview</span></span>](printpreviewcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="a1c1b-125">Controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="a1c1b-125">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="a1c1b-126">Controles e componentes da caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="a1c1b-126">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
