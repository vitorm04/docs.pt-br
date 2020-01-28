---
title: Criar um layout amigável à localização
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
ms.openlocfilehash: 36ffd532b9f539107307144d25c8d9d5f8ba634a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743286"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Como criar um layout dos Windows Forms que responda bem à localização
Criar formulários que estão prontos para serem localizados acelera bastante o desenvolvimento para mercados internacionais. Você pode usar o controle de <xref:System.Windows.Forms.TableLayoutPanel> para implementar layouts que respondem normalmente à medida que os controles são redimensionados devido a alterações em seus valores de propriedade <xref:System.Windows.Forms.Control.Text%2A>.  
  
## <a name="example"></a>Exemplo  
 Este formulário demonstra como criar um layout que se ajusta proporcionalmente ao converter valores de cadeia de caracteres exibidos em outros idiomas. Esse processo de conversão é chamado de *localização*. Para obter mais informações, consulte [localização](../../../standard/globalization-localization/localization.md).  
  
 Há um suporte abrangente para esta tarefa no Visual Studio.  Consulte também [Walkthrough: Criando um layout que ajusta a proporção para localização](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a>Recursos adicionais

1. [Como alinhar e alongar um controle em um controle TableLayoutPanel](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [Como abranger linhas e colunas em um controle TableLayoutPanel](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [Como editar colunas e linhas em um controle TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [Passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](windows-forms-controls-padding-autosize.md)  
  
8. [Como: dar suporte à localização em Windows Forms usando AutoSize e o controle TableLayoutPanel](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [Walkthrough: Criando um formulário redimensionável do Windows para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Localização](../../../standard/globalization-localization/localization.md)
