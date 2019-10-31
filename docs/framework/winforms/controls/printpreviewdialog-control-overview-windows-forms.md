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
# <a name="printpreviewdialog-control-overview-windows-forms"></a>Visão geral do controle PrintPreviewDialog (Windows Forms)

O controle de <xref:System.Windows.Forms.PrintPreviewDialog> de Windows Forms é uma caixa de diálogo pré-configurada usada para exibir como um [documento](printdocument-component-windows-forms.md) impresso será exibido na impressão. Use-o em seu aplicativo baseado no Windows como uma solução simples em vez de configurar sua própria caixa de diálogo. O controle contém botões para imprimir, aumentar o zoom, exibir uma ou várias páginas e fechar a caixa de diálogo.

## <a name="key-properties-and-methods"></a>Propriedades e métodos de chave

A propriedade de chave do controle é <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, que define o documento a ser visualizado. O documento deve ser um objeto <xref:System.Drawing.Printing.PrintDocument>. Para exibir a caixa de diálogo, você deve chamar seu método <xref:System.Windows.Forms.Form.ShowDialog%2A>. A suavização de serrilhado pode fazer com que o texto pareça mais suave, mas também pode tornar a tela mais lenta; para usá-lo, defina a propriedade <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> como `true`.

Determinadas propriedades estão disponíveis por meio do <xref:System.Windows.Forms.PrintPreviewControl> que o <xref:System.Windows.Forms.PrintPreviewDialog> contém. (Você não precisa adicionar esse <xref:System.Windows.Forms.PrintPreviewControl> ao formulário; ele é automaticamente contido na <xref:System.Windows.Forms.PrintPreviewDialog> quando você adiciona a caixa de diálogo ao formulário.) Exemplos de propriedades disponíveis por meio de <xref:System.Windows.Forms.PrintPreviewControl> são as propriedades <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> e <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>, que determinam o número de páginas exibidas horizontal e verticalmente no controle. Você pode acessar a propriedade <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> como `PrintPreviewDialog1.PrintPreviewControl.Columns` em Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` no Visual C#ou `printPreviewDialog1->PrintPreviewControl->Columns` no Visual C++.

## <a name="printpreviewdialog-performance"></a>Desempenho do PrintPreviewDialog

Sob as condições a seguir, o controle de <xref:System.Windows.Forms.PrintPreviewDialog> Inicializa muito lentamente:

- Uma impressora de rede é usada.
- As preferências do usuário para essa impressora, como configurações de duplex, são modificadas.

Para aplicativos em execução no .NET Framework 4.5.2, você pode adicionar a chave a seguir à seção \<appSettings > do arquivo de configuração para melhorar o desempenho da inicialização do controle de <xref:System.Windows.Forms.PrintPreviewDialog>:

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

Se a chave de `EnablePrintPreviewOptimization` for definida como qualquer outro valor, ou se a chave não estiver presente, a otimização não será aplicada.

Para aplicativos em execução no .NET Framework 4,6 ou versões posteriores, você pode adicionar a opção a seguir para o elemento [\<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [> do tempo de execução\<](../../configure-apps/file-schema/runtime/index.md) do seu arquivo de configuração de aplicativo:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

Se a opção não estiver presente ou se estiver definida como qualquer outro valor, a otimização não será aplicada.

Se você usar o evento <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> para modificar as configurações da impressora, o desempenho do controle de <xref:System.Windows.Forms.PrintPreviewDialog> não será melhorado mesmo se uma opção de configuração de otimização for definida.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [Visão geral do controle PrintPreviewControl](printpreviewcontrol-control-overview-windows-forms.md)
- [Controle PrintPreviewDialog](printpreviewdialog-control-windows-forms.md)
- [Controles e componentes da caixa de diálogo](dialog-box-controls-and-components-windows-forms.md)
