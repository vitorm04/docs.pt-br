---
title: Visão geral do componente HelpProvider
ms.date: 03/30/2017
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
ms.openlocfilehash: 74d35dfa39a605cb1e1e85cc3aeda834e1c60669
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738715"
---
# <a name="helpprovider-component-overview-windows-forms"></a>Visão geral do componente HelpProvider (Windows Forms)
O componente [HelpProvider](helpprovider-component-windows-forms.md) dos Windows Forms é usado para associar um arquivo da Ajuda HTML 1.x (um arquivo .chm, produzido com o Workshop de Ajuda HTML ou um arquivo .htm) ao seu aplicativo do Windows. É possível fornecer ajuda de várias maneiras:  
  
- Fornece Ajuda contextual para controles nos Windows Forms.  
  
- Fornece Ajuda contextual em uma caixa de diálogo específica ou controles específicos em uma caixa de diálogo.  
  
- Abra um arquivo de Ajuda para áreas específicas, como a página principal de um sumário, índice ou uma função de pesquisa.  
  
## <a name="using-the-help-provider"></a>Usando o provedor de ajuda  
 Adicionar um componente <xref:System.Windows.Forms.HelpProvider> ao seu formulário do Windows permite que os outros controles no formulário exponham as propriedades da ajuda do componente <xref:System.Windows.Forms.HelpProvider>. Isso habilita você a fornecer ajuda para os controles no seu Windows Form. Você pode associar um arquivo de ajuda com o componente <xref:System.Windows.Forms.HelpProvider> usando a propriedade <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>. Você especifica o tipo de ajuda fornecido chamando <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> e fornecendo um valor da enumeração <xref:System.Windows.Forms.HelpNavigator> para o controle especificado. Você fornece a palavra-chave ou o tópico para obter ajuda chamando o método <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>.  
  
 Opcionalmente, para associar uma cadeia de caracteres de ajuda específica a outro controle, use o método <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>. A cadeia de caracteres associada a um controle usando esse método é exibida em uma janela pop-up quando o usuário pressiona a tecla F1 enquanto o controle tem o foco.  
  
 Se <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> não tiver sido definido, você deverá usar <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> para fornecer o texto de ajuda. Se você definiu <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> e a cadeia de caracteres de ajuda, a ajuda baseada em <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> terá precedência.  
  
> [!NOTE]
> Você pode encontrar problemas ao usar o caminho relativo ao especificar o caminho para o arquivo de ajuda no método <xref:System.Windows.Forms.Help.ShowHelp%2A> ou <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> Propriedade do controle de <xref:System.Windows.Forms.HelpProvider>. Por isso, verifique se você usou o caminho de arquivo absoluto para especificar o arquivo de Ajuda.  
  
## <a name="see-also"></a>Consulte também

- [Sistemas de Ajuda em Aplicativos dos Windows Forms](../advanced/help-systems-in-windows-forms-applications.md)
