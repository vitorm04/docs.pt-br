---
title: Responder a alterações de esquema de fonte em um aplicativo Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: e3b96139a7cfd4b268d81b1da58229527e2beb87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739232"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>Como responder a alterações no esquema de fontes em um aplicativo do Windows Forms
Nos sistemas operacionais Windows, um usuário pode alterar as configurações de fonte de todo o sistema para tornar a fonte padrão maior ou menor. A alteração dessas configurações de fonte é essencial para usuários com deficiência visual, que requerem letras maiores para ler o texto em suas telas. É possível ajustar seu aplicativo do Windows Forms para reagir a essas alterações aumentando ou diminuindo o tamanho do formulário e todo o texto contido nele sempre que o esquema de fontes for alterado. Se desejar que seu formulário acomode as alterações em tamanhos de fonte dinamicamente, será possível adicionar código a ele.  
  
 Normalmente, a fonte padrão usada pelo Windows Forms é a fonte retornada pela chamada de namespace de <xref:Microsoft.Win32> para `GetStockObject(DEFAULT_GUI_FONT)`. A fonte retornada por essa chamada muda apenas quando a resolução da tela é alterada. Conforme mostrado no procedimento a seguir, seu código deve alterar a fonte padrão para <xref:System.Drawing.SystemFonts.IconTitleFont%2A> para responder às alterações no tamanho da fonte.  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>Utilizar a fonte da área de trabalho e responder a alterações no esquema de fontes  
  
1. Crie seu formulário e adicione os controles desejados a ele. Para obter mais informações, consulte [Como criar um aplicativo do Windows Forms na linha de comando](how-to-create-a-windows-forms-application-from-the-command-line.md) e [Controles para Uso no Windows Forms](./controls/controls-to-use-on-windows-forms.md).  
  
2. Adicione uma referência ao namespace <xref:Microsoft.Win32> ao seu código.  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. Adicione o seguinte código ao construtor do formulário para ligar manipuladores de eventos necessários e para alterar a fonte padrão em uso do formulário.  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. Implemente um manipulador para o evento <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> que faz com que o formulário seja dimensionado automaticamente quando a categoria de <xref:Microsoft.Win32.UserPreferenceCategory.Window> é alterada.  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. Por fim, implemente um manipulador para o evento <xref:System.Windows.Forms.Form.FormClosing> que desanexa o manipulador de eventos <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.  
  
     > [!IMPORTANT]
     > Uma falha na inclusão desse código fará com que ocorra vazamento de memória no aplicativo.  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. Compile e execute o código.  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>Alterar manualmente o esquema de fontes no Windows XP  
  
1. Enquanto o Aplicativo do Windows Forms está em execução, clique com o botão direito do mouse na área de trabalho do Windows e escolha **Propriedades** no menu de atalho.  
  
2. Na caixa de diálogo **Propriedades de Exibição**, clique na guia **Aparência**.  
  
3. Na caixa de listagem suspensa **Tamanho da Fonte**, selecione um novo tamanho da fonte.  
  
     Você observará que o formulário agora reage às alterações de tempo de execução no esquema de fontes da área de trabalho. Quando o usuário altera entre **Normal**, **Fontes Grandes** e **Fontes Extra Grandes**, o formulário muda a fonte e ajusta a escala corretamente.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 O Construtor neste exemplo de código contém uma chamada para `InitializeComponent`, que é definida quando você cria um novo projeto de Windows Forms no Visual Studio. Remova essa linha de código se estiver compilando um aplicativo na linha de comando.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [Dimensionamento automático no Windows Forms](automatic-scaling-in-windows-forms.md)
