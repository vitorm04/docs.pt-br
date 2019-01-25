---
title: Fontes internacionais em formulários do Windows e controles
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
ms.openlocfilehash: 1f9afd575e2de04e0b11556ad34436839e13d968
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693234"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="d7d58-102">Fontes internacionais em formulários do Windows e controles</span><span class="sxs-lookup"><span data-stu-id="d7d58-102">International fonts in Windows Forms and controls</span></span>

<span data-ttu-id="d7d58-103">Em aplicativos internacionais, o método recomendado de selecionar fontes é usar fallback de fonte sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="d7d58-103">In International applications, the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="d7d58-104">Fallback de fonte significa que o sistema determina a qual script o caractere pertence.</span><span class="sxs-lookup"><span data-stu-id="d7d58-104">Font fallback means that the system determines what script the character belongs to.</span></span>

## <a name="using-font-fallback"></a><span data-ttu-id="d7d58-105">Usando fallback de fonte</span><span class="sxs-lookup"><span data-stu-id="d7d58-105">Using font fallback</span></span>

<span data-ttu-id="d7d58-106">Para tirar proveito desse recurso, não defina o <xref:System.Drawing.Font> propriedade para seu formulário ou qualquer outro elemento.</span><span class="sxs-lookup"><span data-stu-id="d7d58-106">To take advantage of this feature, don't set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="d7d58-107">O aplicativo usará automaticamente a fonte padrão do sistema, que difere de um idioma localizado do sistema operacional para outro.</span><span class="sxs-lookup"><span data-stu-id="d7d58-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="d7d58-108">Quando o aplicativo é executado, o sistema fornecerá automaticamente a fonte correta para a cultura selecionada no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="d7d58-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>

<span data-ttu-id="d7d58-109">Há uma exceção à regra de não configurar a fonte, o que é para alterar o estilo da fonte.</span><span class="sxs-lookup"><span data-stu-id="d7d58-109">There's an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="d7d58-110">Isso pode ser importante para um aplicativo no qual o usuário clica em um botão para exibir texto em uma caixa de texto em negrito.</span><span class="sxs-lookup"><span data-stu-id="d7d58-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="d7d58-111">Para fazer isso, crie uma função para alterar o estilo da fonte da caixa de texto para negrito, tendo como base qualquer fonte usada pelo formulário.</span><span class="sxs-lookup"><span data-stu-id="d7d58-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="d7d58-112">É importante chamar essa função em dois lugares: no botão <xref:System.Windows.Forms.Control.Click> manipulador de eventos e, no <xref:System.Windows.Forms.Control.FontChanged> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="d7d58-112">It's important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="d7d58-113">Se a função é chamada apenas no <xref:System.Windows.Forms.Control.Click> manipulador de eventos e alguma outra parte do código altera a família de fontes de todo o formulário, a caixa de texto não muda com o restante do formulário.</span><span class="sxs-lookup"><span data-stu-id="d7d58-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box doesn't change with the rest of the form.</span></span>

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

<span data-ttu-id="d7d58-114">No entanto, quando você localiza o aplicativo, a fonte em negrito pode ser exibida incorretamente para determinados idiomas.</span><span class="sxs-lookup"><span data-stu-id="d7d58-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="d7d58-115">Se isso for uma preocupação, será recomendável proporcionar aos localizadores a opção de alternar a fonte de negrito para texto normal.</span><span class="sxs-lookup"><span data-stu-id="d7d58-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="d7d58-116">Como os localizadores normalmente não são desenvolvedores e não tem acesso ao código-fonte, somente a arquivos de recurso, essa opção precisa ser definido nos arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="d7d58-116">Since localizers are typically not developers and don't have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="d7d58-117">Para fazer isso, você definiria o <xref:System.Drawing.Font.Bold%2A> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="d7d58-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="d7d58-118">Isso resulta na configuração de fonte nos arquivos de recurso, nos quais os localizadores podem editá-la.</span><span class="sxs-lookup"><span data-stu-id="d7d58-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="d7d58-119">Você escreverá então código após o método `InitializeComponent` para redefinir a fonte com base em qualquer fonte usada, porém utilizando o estilo da fonte especificado no arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="d7d58-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a><span data-ttu-id="d7d58-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7d58-120">See also</span></span>

- [<span data-ttu-id="d7d58-121">Globalizando aplicativos dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7d58-121">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
- [<span data-ttu-id="d7d58-122">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="d7d58-122">Using Fonts and Text</span></span>](using-fonts-and-text.md)
