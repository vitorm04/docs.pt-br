---
title: Visão geral do controle PrintPreviewDialog (Windows Forms)
ms.custom: ''
ms.date: 01/08/2018
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5e5602a8aa4c83eb8dad33dff31f2dc0e7e7858e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="af8dc-102">Visão geral do controle PrintPreviewDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="af8dc-102">PrintPreviewDialog control overview (Windows Forms)</span></span>
<span data-ttu-id="af8dc-103">Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> controle é uma caixa de diálogo pré-configurada usada para exibir como um [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) aparecerá quando impresso.</span><span class="sxs-lookup"><span data-stu-id="af8dc-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="af8dc-104">Use-o em seu aplicativo baseado no Windows como uma solução simples em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="af8dc-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="af8dc-105">O controle contém botões para imprimir, aumentar o zoom, exibir uma ou várias páginas e fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="af8dc-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="af8dc-106">Métodos e propriedades de chave</span><span class="sxs-lookup"><span data-stu-id="af8dc-106">Key properties and methods</span></span>  
 <span data-ttu-id="af8dc-107">Propriedade de chave do controle é <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, que define o documento a ser visualizado.</span><span class="sxs-lookup"><span data-stu-id="af8dc-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="af8dc-108">O documento deve ser um <xref:System.Drawing.Printing.PrintDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="af8dc-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="af8dc-109">Para exibir a caixa de diálogo, você deve chamar o <xref:System.Windows.Forms.Form.ShowDialog%2A> método.</span><span class="sxs-lookup"><span data-stu-id="af8dc-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="af8dc-110">A suavização pode fazer o texto pareça mais suave, mas ele também pode tornar a exibição mais lenta; para usá-lo, defina o <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="af8dc-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="af8dc-111">Determinadas propriedades estão disponíveis por meio de <xref:System.Windows.Forms.PrintPreviewControl> que o <xref:System.Windows.Forms.PrintPreviewDialog> contém.</span><span class="sxs-lookup"><span data-stu-id="af8dc-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="af8dc-112">(Você não precisa adicionar este <xref:System.Windows.Forms.PrintPreviewControl> para o formulário; ele é automaticamente incluído no <xref:System.Windows.Forms.PrintPreviewDialog> quando você adiciona a caixa de diálogo ao formulário.) Exemplos de propriedades disponíveis por meio de <xref:System.Windows.Forms.PrintPreviewControl> são o <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> e <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> propriedades, que determina o número de páginas exibidas horizontalmente e verticalmente no controle.</span><span class="sxs-lookup"><span data-stu-id="af8dc-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="af8dc-113">Você pode acessar o <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a propriedade como `PrintPreviewDialog1.PrintPreviewControl.Columns` no Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` no Visual c#, ou `printPreviewDialog1->PrintPreviewControl->Columns` em [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af8dc-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` in Visual C#, or `printPreviewDialog1->PrintPreviewControl->Columns` in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span></span>  
  
## <a name="printpreviewdialog-performance"></a><span data-ttu-id="af8dc-114">Desempenho PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="af8dc-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="af8dc-115">Sob as seguintes condições, o <xref:System.Windows.Forms.PrintPreviewDialog> controle inicializa muito lenta:</span><span class="sxs-lookup"><span data-stu-id="af8dc-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="af8dc-116">Uma impressora de rede é usada.</span><span class="sxs-lookup"><span data-stu-id="af8dc-116">A network printer is used.</span></span>
- <span data-ttu-id="af8dc-117">Preferências do usuário para esta impressora, como configurações de duplex são modificadas.</span><span class="sxs-lookup"><span data-stu-id="af8dc-117">User preferences for this printer, such as duplex settings, are modified.</span></span>
  
<span data-ttu-id="af8dc-118">Para aplicativos em execução no .NET Framework 4.5.2, você pode adicionar a seguinte chave para o \<appSettings > seção do arquivo de configuração para melhorar o desempenho de <xref:System.Windows.Forms.PrintPreviewDialog> controlam a inicialização:</span><span class="sxs-lookup"><span data-stu-id="af8dc-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
<span data-ttu-id="af8dc-119">Se o `EnablePrintPreviewOptimization` chave é definida como qualquer outro valor, ou se a chave não estiver presente, a otimização não é aplicada.</span><span class="sxs-lookup"><span data-stu-id="af8dc-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="af8dc-120">Para aplicativos em execução no .NET Framework 4.6 ou posterior, você pode adicionar a seguinte opção para o [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elemento o [ \<tempo de execução >](../../configure-apps/file-schema/runtime/index.md) seção de seu arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="af8dc-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
<span data-ttu-id="af8dc-121">Se a opção não estiver presente ou se ele é definido como qualquer outro valor, a otimização não é aplicada.</span><span class="sxs-lookup"><span data-stu-id="af8dc-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span> 

<span data-ttu-id="af8dc-122">Se você usar o <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> eventos para modificar as configurações de impressora, o desempenho do <xref:System.Windows.Forms.PrintPreviewDialog> controle não melhorará o mesmo que uma opção de configuração de otimização é definida.</span><span class="sxs-lookup"><span data-stu-id="af8dc-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>  

## <a name="see-also"></a><span data-ttu-id="af8dc-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af8dc-123">See also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [<span data-ttu-id="af8dc-124">Visão geral do controle PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="af8dc-124">PrintPreviewControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="af8dc-125">Controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="af8dc-125">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="af8dc-126">Controles e componentes da caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="af8dc-126">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
