---
title: Como carregar arquivos no controle RichTextBox dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 003770e5d21383973946c4ebb83d560f0fa23207
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a>Como carregar arquivos no controle RichTextBox dos Windows Forms
Windows Forms <xref:System.Windows.Forms.RichTextBox> controle pode exibir um texto sem formatação, em texto sem formatação Unicode ou arquivo de formato de Rich Text (RTF). Para fazer isso, chame o <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> método. Você também pode usar o <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> método para carregar dados de um fluxo. Para obter mais informações, consulte <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a>Para carregar um Arquivo no controle RichTextBox  
  
1.  Determinar o caminho do arquivo a ser aberto usando o <xref:System.Windows.Forms.OpenFileDialog> componente. Para obter uma visão geral, consulte [Visão geral do componente OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md).  
  
2.  Chamar o <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> método o <xref:System.Windows.Forms.RichTextBox> controle, especificando o arquivo para carregar e, opcionalmente, um tipo de arquivo. No exemplo a seguir, o arquivo a ser carregado é obtido a <xref:System.Windows.Forms.OpenFileDialog> do componente <xref:System.Windows.Forms.FileDialog.FileName%2A> propriedade. Se você chamar o método com um nome de arquivo como seu único argumento, o tipo de arquivo será considerado como RTF. Para especificar outro tipo de arquivo, chame o método com um valor de <xref:System.Windows.Forms.RichTextBoxStreamType> enumeração como seu segundo argumento.  
  
     No exemplo a seguir, o <xref:System.Windows.Forms.OpenFileDialog> componente é mostrado quando um botão é clicado. O arquivo selecionado é aberto e exibido no <xref:System.Windows.Forms.RichTextBox> controle. Este exemplo supõe que um formulário tem um botão, `btnOpenFile`.  
  
    ```vb  
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles btnOpenFile.Click  
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then  
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _  
              RichTextBoxStreamType.RichText)  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    private void btnOpenFile_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == DialogResult.OK)  
       {  
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void btnOpenFile_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          if(openFileDialog1->ShowDialog() == DialogResult::OK)  
          {  
             richTextBox1->LoadFile(openFileDialog1->FileName,  
                RichTextBoxStreamType::RichText);  
          }  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Coloque o seguinte código no construtor de formulários para registrar o manipulador de eventos.  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  Para executar esse processo, seu assembly pode exigir um nível de privilégio concedido pela <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe. Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes. Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [Controle RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
