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
ms.openlocfilehash: 32fbdd222e34f642d29255e6c594076b6d2a91e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188832"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>Visão geral do controle PrintPreviewDialog (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.PrintPreviewDialog> controle é uma caixa de diálogo pré-configurada usada para exibir como um [PrintDocument](printdocument-component-windows-forms.md) aparecerá quando impresso. Use-o em seu aplicativo baseado no Windows como uma solução simples em vez de configurar sua própria caixa de diálogo. O controle contém botões para imprimir, aumentar o zoom, exibir uma ou várias páginas e fechar a caixa de diálogo.  
  
## <a name="key-properties-and-methods"></a>Métodos e propriedades de chave  
 Propriedade de chave do controle é <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, que define o documento a ser visualizado. O documento deve ser um <xref:System.Drawing.Printing.PrintDocument> objeto. Para exibir a caixa de diálogo, você deve chamar seu <xref:System.Windows.Forms.Form.ShowDialog%2A> método. A suavização pode tornar o texto mais suave, mas também pode tornar a exibição mais lenta; para usá-lo, defina as <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> propriedade para `true`.  
  
 Certas propriedades estão disponíveis por meio de <xref:System.Windows.Forms.PrintPreviewControl> que o <xref:System.Windows.Forms.PrintPreviewDialog> contém. (Não é preciso adicionar isso <xref:System.Windows.Forms.PrintPreviewControl> ao formulário; ele é automaticamente incluído no <xref:System.Windows.Forms.PrintPreviewDialog> quando você adiciona a caixa de diálogo ao formulário.) Exemplos de propriedades disponíveis por meio de <xref:System.Windows.Forms.PrintPreviewControl> são a <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> e <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> propriedades que determinam o número de páginas exibidas horizontal e verticalmente no controle. Você pode acessar o <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a propriedade como `PrintPreviewDialog1.PrintPreviewControl.Columns` no Visual Basic `printPreviewDialog1.PrintPreviewControl.Columns` no Visual C#, ou `printPreviewDialog1->PrintPreviewControl->Columns` na [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].  
  
## <a name="printpreviewdialog-performance"></a>Desempenho PrintPreviewDialog

Sob as seguintes condições, o <xref:System.Windows.Forms.PrintPreviewDialog> controle inicializa muito lenta:

- Uma impressora de rede é usada.
- As preferências do usuário para essa impressora, como as configurações duplex, são modificadas.
  
Para aplicativos em execução no .NET Framework 4.5.2, você pode adicionar a seguinte chave para o \<appSettings > seção do arquivo de configuração para melhorar o desempenho de <xref:System.Windows.Forms.PrintPreviewDialog> controlam a inicialização:

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
Se o `EnablePrintPreviewOptimization` chave é definida como qualquer outro valor, ou se a chave não estiver presente, a otimização não é aplicada.

Para aplicativos em execução no .NET Framework 4.6 ou versões posteriores, você pode adicionar a seguinte opção para o [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elemento no [ \<tempo de execução >](../../configure-apps/file-schema/runtime/index.md) seção do arquivo de configuração de aplicativo:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
Se a opção não estiver presente ou se ele for definido como qualquer outro valor, a otimização não é aplicada. 

Se você usar o <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> evento para modificar as configurações de impressora, o desempenho do <xref:System.Windows.Forms.PrintPreviewDialog> controle não melhorará o mesmo que uma opção de configuração de otimização é definida.  

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [Visão geral do controle PrintPreviewControl](printpreviewcontrol-control-overview-windows-forms.md)
- [Controle PrintPreviewDialog](printpreviewdialog-control-windows-forms.md)
- [Controles e componentes da caixa de diálogo](dialog-box-controls-and-components-windows-forms.md)
