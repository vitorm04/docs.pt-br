---
title: Fontes internacionais em Windows Forms e controles
ms.date: 03/30/2017
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
dev_langs:
- csharp
- vb
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
ms.openlocfilehash: 0ddbd6d7a1b614d588a2572b410957a5ed3b768c
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956912"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a>Fontes internacionais em Windows Forms e controles

Em aplicativos internacionais, o método recomendado para selecionar fontes é usar o fallback de fonte sempre que possível. Fallback de fonte significa que o sistema determina a qual script o caractere pertence.

## <a name="using-font-fallback"></a>Usando fallback de fonte

Para aproveitar esse recurso, não defina a propriedade <xref:System.Drawing.Font> para seu formulário ou qualquer outro elemento. O aplicativo usará automaticamente a fonte padrão do sistema, que difere de um idioma localizado do sistema operacional para outro. Quando o aplicativo é executado, o sistema fornecerá automaticamente a fonte correta para a cultura selecionada no sistema operacional.

Há uma exceção à regra de não definir a fonte, que é para alterar o estilo da fonte. Isso pode ser importante para um aplicativo no qual o usuário clica em um botão para exibir texto em uma caixa de texto em negrito. Para fazer isso, crie uma função para alterar o estilo da fonte da caixa de texto para negrito, tendo como base qualquer fonte usada pelo formulário. É importante chamar essa função em dois locais: no manipulador de eventos <xref:System.Windows.Forms.Control.Click> do botão e no manipulador de eventos <xref:System.Windows.Forms.Control.FontChanged>. Se a função for chamada apenas no manipulador de eventos <xref:System.Windows.Forms.Control.Click> e alguma outra parte do código alterar a família de fontes do formulário inteiro, a caixa de texto não será alterada com o restante do formulário.

```vb
Private Sub MakeBold()
   ' Change the TextBox to a bold version of the form font
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)
End Sub

Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
   ' Clicking this button makes the TextBox bold
   MakeBold()
End Sub

Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged
   ' If the TextBox is already bold and the form's font changes,
   ' change the TextBox to a bold version of the new form font
   If (TextBox1.Font.Style = FontStyle.Bold) Then
      MakeBold()
   End If
End Sub
```

```csharp
private void button1_Click(object sender, System.EventArgs e)
{
   // Clicking this button makes the TextBox bold
   MakeBold();
}

private void MakeBold()
{
   // Change the TextBox to a bold version of the form's font
   textBox1.Font = new Font(this.Font, FontStyle.Bold);
}

private void Form1_FontChanged(object sender, System.EventArgs e)
{
   // If the TextBox is already bold and the form's font changes,
   // change the TextBox to a bold version of the new form font
   if (textBox1.Font.Style == FontStyle.Bold)
   {
      MakeBold();
   }
}
```

No entanto, quando você localiza o aplicativo, a fonte em negrito pode ser exibida incorretamente para determinados idiomas. Se isso for uma preocupação, será recomendável proporcionar aos localizadores a opção de alternar a fonte de negrito para texto normal. Como os localizadores normalmente não são desenvolvedores e não têm acesso ao código-fonte, somente aos arquivos de recursos, essa opção precisa ser definida nos arquivos de recursos. Para fazer isso, defina a propriedade <xref:System.Drawing.Font.Bold%2A> como `true`. Isso resulta na configuração de fonte nos arquivos de recurso, nos quais os localizadores podem editá-la. Você escreverá então código após o método `InitializeComponent` para redefinir a fonte com base em qualquer fonte usada, porém utilizando o estilo da fonte especificado no arquivo de recurso.

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a>Consulte também

- [Usando fontes e texto](using-fonts-and-text.md)
