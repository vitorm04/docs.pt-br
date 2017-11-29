---
title: "Visão geral do componente HelpProvider (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42a788e44fde80662748e19a7244ce77bb26118f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="helpprovider-component-overview-windows-forms"></a>Visão geral do componente HelpProvider (Windows Forms)
O componente [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) dos Windows Forms é usado para associar um arquivo da Ajuda HTML 1.x (um arquivo .chm, produzido com o Workshop de Ajuda HTML ou um arquivo .htm) ao seu aplicativo do Windows. É possível fornecer ajuda de várias maneiras:  
  
-   Fornece Ajuda contextual para controles nos Windows Forms.  
  
-   Fornece Ajuda contextual em uma caixa de diálogo específica ou controles específicos em uma caixa de diálogo.  
  
-   Abra um arquivo de Ajuda para áreas específicas, como a página principal de um sumário, índice ou uma função de pesquisa.  
  
## <a name="using-the-help-provider"></a>Usando o provedor de ajuda  
 Adicionando um <xref:System.Windows.Forms.HelpProvider> componente para o formulário do Windows permite que os outros controles no formulário para expor as propriedades de Ajuda do <xref:System.Windows.Forms.HelpProvider> componente. Isso habilita você a fornecer ajuda para os controles no seu Windows Form. Você pode associar um arquivo de ajuda com o <xref:System.Windows.Forms.HelpProvider> componente usando o <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriedade. Especifique o tipo de ajuda fornecidos chamando <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> e fornecendo um valor da <xref:System.Windows.Forms.HelpNavigator> enumeração para o controle especificado. Forneça a palavra-chave ou um tópico para obter ajuda ao chamar o <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> método.  
  
 Opcionalmente, para associar uma cadeia de caracteres de ajuda específica com outro controle, use o <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> método. A cadeia de caracteres associada a um controle usando esse método é exibida em uma janela pop-up quando o usuário pressiona a tecla F1 enquanto o controle tem o foco.  
  
 Se <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> não tiver sido definido, você deve usar <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> para fornecer o texto de Ajuda. Se você tiver definido as <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> e a cadeia de caracteres de Ajuda, ajuda baseada em <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> terá precedência.  
  
> [!NOTE]
>  Você pode encontrar problemas ao usar o caminho relativo ao especificar o caminho para o arquivo de Ajuda no <xref:System.Windows.Forms.Help.ShowHelp%2A> método ou <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriedade do <xref:System.Windows.Forms.HelpProvider> controle. Por isso, verifique se você usou o caminho de arquivo absoluto para especificar o arquivo de Ajuda.  
  
## <a name="see-also"></a>Consulte também  
 [Sistemas de Ajuda em Aplicativos dos Windows Forms](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)
