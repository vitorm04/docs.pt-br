---
title: 'Como: Agrupar controles com o controle de painel do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 1a3fcac56df1328c12d7a5dcb542138afdb486f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214826"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Como: Agrupar controles com o controle de painel do Windows Forms usando o Designer
Windows Forms <xref:System.Windows.Forms.Panel> controles são usados para agrupar outros controles. Há três razões para agrupar controles. Uma delas é o agrupamento visual de elementos de formulários relacionados para uma interface do usuário clara; a outra é o agrupamento programático dos botões de opção, por exemplo; a última é para mover os controles como uma unidade em tempo de design.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-group-of-controls"></a>Para criar um grupo de controles  
  
1.  Arraste uma <xref:System.Windows.Forms.Panel> controlar do **Windows Forms** guia da caixa de ferramentas para um formulário.  
  
2.  Adicione outros controles ao painel desenhando cada um deles dentro do painel.  
  
     Se você tiver controles existentes que você deseja incluir em um painel, você pode selecionar todos os controles, recortá-los para a área de transferência, selecione o <xref:System.Windows.Forms.Panel> controlar e, em seguida, cole-os para o painel. Você também pode arrastá-los para o painel.  
  
3.  (Opcional) Se você quiser adicionar uma borda a um painel, defina seu <xref:System.Windows.Forms.BorderStyle> propriedade. Há três opções: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, e <xref:System.Windows.Forms.BorderStyle.None>.  
  
## <a name="see-also"></a>Consulte também

- [Controle de painel](panel-control-windows-forms.md)
- [Visão geral do controle de painel](panel-control-overview-windows-forms.md)
- [Como: Definir a tela de fundo de um painel](how-to-set-the-background-of-a-windows-forms-panel.md)
