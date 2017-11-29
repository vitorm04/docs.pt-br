---
title: Como agrupar controles com o controle do painel dos Windows Forms usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1d4a49f36ac294199871075a04b7e682bd5613b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Como agrupar controles com o controle do painel dos Windows Forms usando o designer
Windows Forms <xref:System.Windows.Forms.Panel> controles são usados para agrupar outros controles. Há três razões para agrupar controles. Uma delas é o agrupamento visual de elementos de formulários relacionados para uma interface do usuário clara; a outra é o agrupamento programático dos botões de opção, por exemplo; a última é para mover os controles como uma unidade em tempo de design.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-group-of-controls"></a>Para criar um grupo de controles  
  
1.  Arraste um <xref:System.Windows.Forms.Panel> controlar do **Windows Forms** guia da caixa de ferramentas para um formulário.  
  
2.  Adicione outros controles ao painel desenhando cada um deles dentro do painel.  
  
     Se você tiver controles existentes que você deseja incluir em um painel, você pode selecionar todos os controles, recortá-los para a área de transferência, selecione o <xref:System.Windows.Forms.Panel> de controle e, em seguida, cole-os para o painel. Você também pode arrastá-los para o painel.  
  
3.  (Opcional) Se você deseja adicionar uma borda a um painel, defina seu <xref:System.Windows.Forms.BorderStyle> propriedade. Há três opções: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, e <xref:System.Windows.Forms.BorderStyle.None>.  
  
## <a name="see-also"></a>Consulte também  
 [Controle de painel](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [Visão geral do controle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Como definir a tela de fundo de um painel](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
