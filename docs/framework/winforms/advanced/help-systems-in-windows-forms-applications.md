---
title: Sistemas de Ajuda em aplicativos do Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
ms.openlocfilehash: 1a02271d59a59f0a6e06a652a34922ba5dcdf1f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087256"
---
# <a name="help-systems-in-windows-forms-applications"></a>Sistemas de Ajuda em aplicativos do Windows Forms
Uma das cortesias mais importantes que você, como desenvolvedor de aplicativos, pode fornecer aos seus usuários com é um sistema de Ajuda competente. Esse é o local que eles procuram quando ficam confusos ou desorientados. É fácil fornecer um sistema de Ajuda em um aplicativo baseado no Windows usando o [componente HelpProvider](../controls/helpprovider-component-windows-forms.md).  
  
## <a name="different-types-of-help"></a>Diferentes tipos de ajuda  
 Os formulários do Windows <xref:System.Windows.Forms.HelpProvider> componente é usado para associar um arquivo de ajuda a Ajuda HTML 1.x (um arquivo. chm, produzido com o HTML Help Workshop, ou um arquivo. htm) com seu aplicativo baseado em Windows. O <xref:System.Windows.Forms.HelpProvider> componente pode ser usado para fornecer ajuda contextual para controles nos Windows Forms ou controles específicos. Além disso, o <xref:System.Windows.Forms.HelpProvider> componente pode abrir um arquivo de ajuda para áreas específicas, como a página principal de uma tabela de conteúdo, um índice ou uma função de pesquisa. Para obter informações gerais sobre o <xref:System.Windows.Forms.HelpProvider> componente, consulte [visão geral do componente HelpProvider](../controls/helpprovider-component-overview-windows-forms.md). Para obter informações sobre como usar o <xref:System.Windows.Forms.HelpProvider> componente para exibir ajuda pop-up nos Windows Forms, consulte [como: Exibir Ajuda pop-up](how-to-display-pop-up-help.md). Para obter informações sobre como usar o <xref:System.Windows.Forms.ToolTip> componente para exibir a Ajuda específica do controle, consulte [controle ajuda usando as dicas de ferramenta](control-help-using-tooltips.md).  
  
 Você pode gerar arquivos da Ajuda HTML 1.x com o HTML Help Workshop. Para obter mais informações sobre a Ajuda HTML, veja o "HTML Help Workshop" ou outros tópicos de "Ajuda HTML" no MSDN.  
  
## <a name="see-also"></a>Consulte também

- [Integrando a ajuda do usuário nos Windows Forms](integrating-user-help-in-windows-forms.md)
- [Componente HelpProvider](../controls/helpprovider-component-windows-forms.md)
- [Componente ToolTip](../controls/tooltip-component-windows-forms.md)
- [Visão geral dos Windows Forms](../windows-forms-overview.md)
- [Windows Forms](../index.md)
