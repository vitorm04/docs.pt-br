---
title: Agrupar controles com controle de painel usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 927aeb5b51bc1ac4e22a45e487b49424b4e67b71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745644"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Como agrupar controles com o controle do painel dos Windows Forms usando o designer
Windows Forms <xref:System.Windows.Forms.Panel> controles são usados para agrupar outros controles. Há três razões para agrupar controles. Uma delas é o agrupamento visual de elementos de formulários relacionados para uma interface do usuário clara; a outra é o agrupamento programático dos botões de opção, por exemplo; a última é para mover os controles como uma unidade em tempo de design.

## <a name="to-create-a-group-of-controls"></a>Para criar um grupo de controles

1. Arraste um controle de <xref:System.Windows.Forms.Panel> da guia **Windows Forms** da caixa de ferramentas para um formulário.

2. Adicione outros controles ao painel desenhando cada um deles dentro do painel.

     Se você tiver controles existentes que deseja incluir em um painel, poderá selecionar todos os controles, recortá-los para a área de transferência, selecionar o controle de <xref:System.Windows.Forms.Panel> e, em seguida, colá-los no painel. Você também pode arrastá-los para o painel.

3. Adicional Se você quiser adicionar uma borda a um painel, defina sua propriedade <xref:System.Windows.Forms.BorderStyle>. Há três opções: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>e <xref:System.Windows.Forms.BorderStyle.None>.

## <a name="see-also"></a>Consulte também

- [Controle de painel](panel-control-windows-forms.md)
- [Visão geral do controle Panel](panel-control-overview-windows-forms.md)
- [Como definir a tela de fundo de um painel](how-to-set-the-background-of-a-windows-forms-panel.md)
