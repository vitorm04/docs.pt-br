---
title: Salvar arquivos com controle RichTextBox
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
ms.openlocfilehash: a87b93a53347aeba54f944b0f4c455aa272ea243
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744821"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>Como salvar arquivos com o controle RichTextBox dos Windows Forms

O controle de <xref:System.Windows.Forms.RichTextBox> de Windows Forms pode gravar as informações exibidas em um dos vários formatos:

- Texto sem formatação

- Texto sem formatação Unicode

- RTF (Formato Rich Text)

- RTF com espaços em vez de objetos OLE

- Texto sem formatação com uma representação textual de objetos OLE

Para salvar um arquivo, chame o método <xref:System.Windows.Forms.RichTextBox.SaveFile%2A>. Você também pode usar o método **SaveFile** para salvar dados em um fluxo. Para obter mais informações, consulte <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.

### <a name="to-save-the-contents-of-the-control-to-a-file"></a>Para salvar o conteúdo do controle em um arquivo

1. Determine o caminho do arquivo a ser salvo.

    Para fazer isso em um aplicativo do mundo real, você normalmente usará o componente <xref:System.Windows.Forms.SaveFileDialog>. Para obter uma visão geral, consulte [Visão geral do componente SaveFileDialog](savefiledialog-component-overview-windows-forms.md).

2. Chame o método <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> do controle <xref:System.Windows.Forms.RichTextBox>, especificando o arquivo a ser salvo e, opcionalmente, um tipo de arquivo. Se você chamar o método com um nome de arquivo como seu único argumento, o arquivo será salvo como RTF. Para especificar outro tipo de arquivo, chame o método com um valor da enumeração <xref:System.Windows.Forms.RichTextBoxStreamType> como seu segundo argumento.

    No exemplo de código a seguir, o caminho definido para o do arquivo rich-text é a pasta **Meus documentos**. Esse local é usado porque você pode supor que a maioria dos computadores que executam o sistema operacional Windows incluem essa pasta. Escolher esse local também permite que os usuários com níveis mínimos de acesso ao sistema executem com mais segurança o aplicativo. O exemplo a seguir pressupõe um formulário com um controle de <xref:System.Windows.Forms.RichTextBox> já adicionado.

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
    > Este exemplo cria um novo arquivo, se o arquivo ainda não existe. Se um aplicativo precisar criar um arquivo, essa aplicativo precisará de acesso Criar para a pasta. As permissões são definidas usando listas de controle de acesso. Se o arquivo já existir, o aplicativo precisará apenas de acesso Gravar, um privilégio menor. Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder acesso de leitura a um único arquivo, em vez de acesso Criar a uma pasta. Além disso, é mais seguro gravar dados em pastas de usuário do que na pasta raiz ou na pasta Arquivos de Programas.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](richtextbox-control-windows-forms.md)
- [Controles a serem usados no Windows Forms](controls-to-use-on-windows-forms.md)
