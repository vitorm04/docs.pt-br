---
title: Como criar um layout dos Windows Forms que responda bem à localização
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
ms.openlocfilehash: aa141319e902ff96ecfb9e9a70ca66528705418d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Como criar um layout dos Windows Forms que responda bem à localização
Criação de formulários que estão prontos para ser localizados aumenta a velocidade de desenvolvimento para mercados internacionais. Você pode usar o <xref:System.Windows.Forms.TableLayoutPanel> controle para implementar layouts respondem normalmente como redimensionam controles devido a alterações em seus <xref:System.Windows.Forms.Control.Text%2A> valores de propriedade.  
  
## <a name="example"></a>Exemplo  
 Este formulário demonstra como criar um layout que proporcionalmente se ajusta ao converter valores de cadeia de caracteres exibidos em outros idiomas. Esse processo de conversão é chamado *localização*. Para obter mais informações, consulte [localização](../../../../docs/standard/globalization-localization/localization.md).  
  
 Há um suporte abrangente para esta tarefa no Visual Studio.  Consulte também [passo a passo: Criando um Layout que ajusta proporção para localização](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  [Como alinhar e alongar um controle em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))  
  
3.  [Como abranger linhas e colunas em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
4.  [Como editar colunas e linhas em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
5.  [Passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))  
  
6.  [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
7.  [Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))  
  
8.  [Como: oferecer suporte à localização no Windows Forms usando AutoSize e o controle TableLayoutPanel](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))  
  
9. [Passo a passo: Criando um Windows Form redimensionável para entrada de dados](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [Localização](../../../../docs/standard/globalization-localization/localization.md)
