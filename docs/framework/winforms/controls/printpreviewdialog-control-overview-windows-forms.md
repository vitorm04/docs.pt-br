---
title: "Visão geral do controle PrintPreviewDialog (Windows Forms)"
ms.custom: 
ms.date: 01/08/2018
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewDialog
helpviewer_keywords: PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1228a3cf39ea412cde341c4c4b8b83e0ab2f0299
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>Visão geral do controle PrintPreviewDialog (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> controle é uma caixa de diálogo pré-configurada usada para exibir como um [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) aparecerá quando impresso. Use-o em seu aplicativo baseado no Windows como uma solução simples em vez de configurar sua própria caixa de diálogo. O controle contém botões para imprimir, aumentar o zoom, exibir uma ou várias páginas e fechar a caixa de diálogo.  
  
## <a name="key-properties-and-methods"></a>Métodos e propriedades de chave  
 Propriedade de chave do controle é <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, que define o documento a ser visualizado. O documento deve ser um <xref:System.Drawing.Printing.PrintDocument> objeto. Para exibir a caixa de diálogo, você deve chamar o <xref:System.Windows.Forms.Form.ShowDialog%2A> método. A suavização pode fazer o texto pareça mais suave, mas ele também pode tornar a exibição mais lenta; para usá-lo, defina o <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> propriedade `true`.  
  
 Determinadas propriedades estão disponíveis por meio de <xref:System.Windows.Forms.PrintPreviewControl> que o <xref:System.Windows.Forms.PrintPreviewDialog> contém. (Você não precisa adicionar este <xref:System.Windows.Forms.PrintPreviewControl> para o formulário; ele é automaticamente incluído no <xref:System.Windows.Forms.PrintPreviewDialog> quando você adiciona a caixa de diálogo ao formulário.) Exemplos de propriedades disponíveis por meio de <xref:System.Windows.Forms.PrintPreviewControl> são o <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> e <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> propriedades, que determina o número de páginas exibidas horizontalmente e verticalmente no controle. Você pode acessar o <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a propriedade como `PrintPreviewDialog1.PrintPreviewControl.Columns` na [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], `printPreviewDialog1.PrintPreviewControl.Columns` na [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], ou `printPreviewDialog1->PrintPreviewControl->Columns` em [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].  
  
## <a name="printpreviewdialog-performance"></a>Desempenho PrintPreviewDialog

Sob as seguintes condições, o <xref:System.Windows.Forms.PrintPreviewDialog> controle inicializa muito lenta:

- Uma impressora de rede é usada.
- Preferências do usuário para esta impressora, como configurações de duplex são modificadas.
  
Para aplicativos em execução no .NET Framework 4.5.2, você pode adicionar a seguinte chave para o \<appSettings > seção do arquivo de configuração para melhorar o desempenho de <xref:System.Windows.Forms.PrintPreviewDialog> controlam a inicialização:

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
Se o `EnablePrintPreviewOptimization` chave é definida como qualquer outro valor, ou se a chave não estiver presente, a otimização não é aplicada.

Para aplicativos em execução no .NET Framework 4.6 ou posterior, você pode adicionar a seguinte opção para o [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elemento o [ \<tempo de execução >](../../configure-apps/file-schema/runtime/index.md) seção de seu arquivo de configuração do aplicativo:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
Se a opção não estiver presente ou se ele é definido como qualquer outro valor, a otimização não é aplicada. 

Se você usar o <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> eventos para modificar as configurações de impressora, o desempenho do <xref:System.Windows.Forms.PrintPreviewDialog> controle não melhorará o mesmo que uma opção de configuração de otimização é definida.  

## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [Visão geral do controle PrintPreviewControl](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [Controle PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Controles e componentes da caixa de diálogo](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
