---
title: 'Como: Criar um layout do Windows Forms que responda bem à localização'
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
ms.openlocfilehash: c1aa62413e1c9cc29507b7b0ed5cbf1c5fcea26a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928562"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Como: Criar um layout do Windows Forms que responda bem à localização
Criar formulários que estão prontos para serem localizados acelera bastante o desenvolvimento para mercados internacionais. Você pode usar o <xref:System.Windows.Forms.TableLayoutPanel> controle para implementar layouts que respondem normalmente conforme os controles são redimensionados <xref:System.Windows.Forms.Control.Text%2A> devido a alterações em seus valores de propriedade.  
  
## <a name="example"></a>Exemplo  
 Este formulário demonstra como criar um layout que se ajusta proporcionalmente ao converter valores de cadeia de caracteres exibidos em outros idiomas. Esse processo de conversão é chamado de *localização*. Para obter mais informações, consulte [localização](../../../standard/globalization-localization/localization.md).  
  
 Há um suporte abrangente para esta tarefa no Visual Studio.  Consulte também [passo a passos: Criando um layout que ajusta a proporção para localização](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a>Recursos adicionais

1. [Como: Alinhar e alongar um controle em um controle TableLayoutPanel](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [Passo a passo: Organizando controles em Windows Forms usando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [Como: Abranger linhas e colunas em um controle TableLayoutPanel](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [Como: Editar colunas e linhas em um controle TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [Passo a passo: Executando tarefas comuns usando marcas inteligentes em controles de Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [Passo a passo: Organizando controles em Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [Passo a passo: Dispor Windows Forms controles com preenchimento, margens e a propriedade AutoSize](windows-forms-controls-padding-autosize.md)  
  
8. [Como: Suporte à localização em Windows Forms usando AutoSize e o controle TableLayoutPanel](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [Passo a passo: Criando um formulário redimensionável do Windows para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Localização](../../../standard/globalization-localization/localization.md)
