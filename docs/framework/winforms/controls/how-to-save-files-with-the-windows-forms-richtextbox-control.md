---
title: 'Como: Salvar arquivos com o controle RichTextBox dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: 739cc33df873ef2c8ec7a2f5eaf867abadb8da75
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539773"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>Como: Salvar arquivos com o controle RichTextBox dos Windows Forms
Os formulários do Windows <xref:System.Windows.Forms.RichTextBox> controle pode gravar as informações exibidas em um dos vários formatos:  
  
-   Texto sem formatação  
  
-   Texto sem formatação Unicode  
  
-   RTF (Formato Rich Text)  
  
-   RTF com espaços em vez de objetos OLE  
  
-   Texto sem formatação com uma representação textual de objetos OLE  
  
 Para salvar um arquivo, chame o <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> método. Você também pode usar o método **SaveFile** para salvar dados em um fluxo. Para obter mais informações, consulte <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a>Para salvar o conteúdo do controle em um arquivo  
  
1.  Determine o caminho do arquivo a ser salvo.  
  
     Para fazer isso em um aplicativo do mundo real, você normalmente usaria o <xref:System.Windows.Forms.SaveFileDialog> componente. Para obter uma visão geral, consulte [Visão geral do componente SaveFileDialog](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md).  
  
2.  Chame o <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> método da <xref:System.Windows.Forms.RichTextBox> controle, especificando o arquivo a ser salvo e, opcionalmente, um tipo de arquivo. Se você chamar o método com um nome de arquivo como seu único argumento, o arquivo será salvo como RTF. Para especificar outro tipo de arquivo, chame o método com um valor da <xref:System.Windows.Forms.RichTextBoxStreamType> enumeração como seu segundo argumento.  
  
     No exemplo de código a seguir, o caminho definido para o do arquivo rich-text é a pasta **Meus documentos**. Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows inclui essa pasta. Escolher esse local também permite que os usuários com níveis mínimos de acesso ao sistema executem com mais segurança o aplicativo. O exemplo a seguir supõe um formulário com um <xref:System.Windows.Forms.RichTextBox> controle já adicionado.  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  Este exemplo cria um novo arquivo, se o arquivo ainda não existe. Se um aplicativo precisar criar um arquivo, essa aplicativo precisará de acesso Criar para a pasta. As permissões são definidas usando listas de controle de acesso. Se o arquivo já existir, o aplicativo precisará apenas de acesso Gravar, um privilégio menor. Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder acesso de leitura a um único arquivo, em vez de acesso Criar a uma pasta. Além disso, é mais seguro gravar dados em pastas de usuário do que na pasta raiz ou na pasta Arquivos de Programas.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)
- [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
