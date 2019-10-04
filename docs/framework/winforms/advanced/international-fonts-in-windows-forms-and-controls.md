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
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="54604-102">Fontes internacionais em Windows Forms e controles</span><span class="sxs-lookup"><span data-stu-id="54604-102">International fonts in Windows Forms and controls</span></span>

<span data-ttu-id="54604-103">Em aplicativos internacionais, o método recomendado para selecionar fontes é usar o fallback de fonte sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="54604-103">In International applications, the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="54604-104">Fallback de fonte significa que o sistema determina a qual script o caractere pertence.</span><span class="sxs-lookup"><span data-stu-id="54604-104">Font fallback means that the system determines what script the character belongs to.</span></span>

## <a name="using-font-fallback"></a><span data-ttu-id="54604-105">Usando fallback de fonte</span><span class="sxs-lookup"><span data-stu-id="54604-105">Using font fallback</span></span>

<span data-ttu-id="54604-106">Para aproveitar esse recurso, não defina a propriedade <xref:System.Drawing.Font> para seu formulário ou qualquer outro elemento.</span><span class="sxs-lookup"><span data-stu-id="54604-106">To take advantage of this feature, don't set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="54604-107">O aplicativo usará automaticamente a fonte padrão do sistema, que difere de um idioma localizado do sistema operacional para outro.</span><span class="sxs-lookup"><span data-stu-id="54604-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="54604-108">Quando o aplicativo é executado, o sistema fornecerá automaticamente a fonte correta para a cultura selecionada no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="54604-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>

<span data-ttu-id="54604-109">Há uma exceção à regra de não definir a fonte, que é para alterar o estilo da fonte.</span><span class="sxs-lookup"><span data-stu-id="54604-109">There's an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="54604-110">Isso pode ser importante para um aplicativo no qual o usuário clica em um botão para exibir texto em uma caixa de texto em negrito.</span><span class="sxs-lookup"><span data-stu-id="54604-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="54604-111">Para fazer isso, crie uma função para alterar o estilo da fonte da caixa de texto para negrito, tendo como base qualquer fonte usada pelo formulário.</span><span class="sxs-lookup"><span data-stu-id="54604-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="54604-112">É importante chamar essa função em dois locais: no manipulador de eventos <xref:System.Windows.Forms.Control.Click> do botão e no manipulador de eventos <xref:System.Windows.Forms.Control.FontChanged>.</span><span class="sxs-lookup"><span data-stu-id="54604-112">It's important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="54604-113">Se a função for chamada apenas no manipulador de eventos <xref:System.Windows.Forms.Control.Click> e alguma outra parte do código alterar a família de fontes do formulário inteiro, a caixa de texto não será alterada com o restante do formulário.</span><span class="sxs-lookup"><span data-stu-id="54604-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box doesn't change with the rest of the form.</span></span>

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

<span data-ttu-id="54604-114">No entanto, quando você localiza o aplicativo, a fonte em negrito pode ser exibida incorretamente para determinados idiomas.</span><span class="sxs-lookup"><span data-stu-id="54604-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="54604-115">Se isso for uma preocupação, será recomendável proporcionar aos localizadores a opção de alternar a fonte de negrito para texto normal.</span><span class="sxs-lookup"><span data-stu-id="54604-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="54604-116">Como os localizadores normalmente não são desenvolvedores e não têm acesso ao código-fonte, somente aos arquivos de recursos, essa opção precisa ser definida nos arquivos de recursos.</span><span class="sxs-lookup"><span data-stu-id="54604-116">Since localizers are typically not developers and don't have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="54604-117">Para fazer isso, defina a propriedade <xref:System.Drawing.Font.Bold%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="54604-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="54604-118">Isso resulta na configuração de fonte nos arquivos de recurso, nos quais os localizadores podem editá-la.</span><span class="sxs-lookup"><span data-stu-id="54604-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="54604-119">Você escreverá então código após o método `InitializeComponent` para redefinir a fonte com base em qualquer fonte usada, porém utilizando o estilo da fonte especificado no arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="54604-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a><span data-ttu-id="54604-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54604-120">See also</span></span>

- [<span data-ttu-id="54604-121">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="54604-121">Using Fonts and Text</span></span>](using-fonts-and-text.md)
