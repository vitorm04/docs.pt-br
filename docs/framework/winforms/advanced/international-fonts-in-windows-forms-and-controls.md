---
title: "Fontes internacionais em formulários e controles do Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5901113021deffd601b5325ff9a1b8912e74329d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="658f8-102">Fontes internacionais em formulários e controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="658f8-102">International Fonts in Windows Forms and Controls</span></span>
<span data-ttu-id="658f8-103">Em aplicativos internacionais, o método recomendado de selecionar fontes é usar fallback de fonte sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="658f8-103">In International applications the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="658f8-104">Fallback de fonte significa que o sistema determina a qual script o caractere pertence.</span><span class="sxs-lookup"><span data-stu-id="658f8-104">Font fallback means that the system determines what script the character belongs to.</span></span>  
  
## <a name="using-font-fallback"></a><span data-ttu-id="658f8-105">Usando fallback de fonte</span><span class="sxs-lookup"><span data-stu-id="658f8-105">Using Font Fallback</span></span>  
 <span data-ttu-id="658f8-106">Para tirar proveito desse recurso, não defina o <xref:System.Drawing.Font> propriedade seu formulário ou qualquer outro elemento.</span><span class="sxs-lookup"><span data-stu-id="658f8-106">To take advantage of this feature, do not set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="658f8-107">O aplicativo usará automaticamente a fonte padrão do sistema, que difere de um idioma localizado do sistema operacional para outro.</span><span class="sxs-lookup"><span data-stu-id="658f8-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="658f8-108">Quando o aplicativo é executado, o sistema fornecerá automaticamente a fonte correta para a cultura selecionada no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="658f8-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>  
  
 <span data-ttu-id="658f8-109">Há uma exceção à regra de não definir a fonte, a qual refere-se à alteração do estilo da fonte.</span><span class="sxs-lookup"><span data-stu-id="658f8-109">There is an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="658f8-110">Isso pode ser importante para um aplicativo no qual o usuário clica em um botão para exibir texto em uma caixa de texto em negrito.</span><span class="sxs-lookup"><span data-stu-id="658f8-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="658f8-111">Para fazer isso, crie uma função para alterar o estilo da fonte da caixa de texto para negrito, tendo como base qualquer fonte usada pelo formulário.</span><span class="sxs-lookup"><span data-stu-id="658f8-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="658f8-112">É importante chamar essa função em dois lugares: o botão <xref:System.Windows.Forms.Control.Click> manipulador de eventos e no <xref:System.Windows.Forms.Control.FontChanged> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="658f8-112">It is important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="658f8-113">Se a função é chamada apenas no <xref:System.Windows.Forms.Control.Click> manipulador de eventos e alguma outra parte do código altera a família de fonte de todo o formulário, a caixa de texto não será alterada com o restante do formulário.</span><span class="sxs-lookup"><span data-stu-id="658f8-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box will not change with the rest of the form.</span></span>  
  
```  
' Visual Basic  
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
  
// C#  
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
  
 <span data-ttu-id="658f8-114">No entanto, quando você localiza o aplicativo, a fonte em negrito pode ser exibida incorretamente para determinados idiomas.</span><span class="sxs-lookup"><span data-stu-id="658f8-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="658f8-115">Se isso for uma preocupação, será recomendável proporcionar aos localizadores a opção de alternar a fonte de negrito para texto normal.</span><span class="sxs-lookup"><span data-stu-id="658f8-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="658f8-116">Como os localizadores normalmente não são desenvolvedores e não têm acesso ao código-fonte, somente aos arquivos de recurso, essa opção precisa ser definida nos arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="658f8-116">Since localizers are typically not developers and do not have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="658f8-117">Para fazer isso, defina o <xref:System.Drawing.Font.Bold%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="658f8-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="658f8-118">Isso resulta na configuração de fonte nos arquivos de recurso, nos quais os localizadores podem editá-la.</span><span class="sxs-lookup"><span data-stu-id="658f8-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="658f8-119">Você escreverá então código após o método `InitializeComponent` para redefinir a fonte com base em qualquer fonte usada, porém utilizando o estilo da fonte especificado no arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="658f8-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>  
  
```  
' Visual Basic  
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)  
  
// C#  
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);  
```  
  
## <a name="see-also"></a><span data-ttu-id="658f8-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="658f8-120">See Also</span></span>  
 [<span data-ttu-id="658f8-121">Globalizando o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="658f8-121">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)  
 [<span data-ttu-id="658f8-122">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="658f8-122">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
