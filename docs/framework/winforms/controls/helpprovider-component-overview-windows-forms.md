---
title: Visão geral do componente HelpProvider (Windows Forms)
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
ms.openlocfilehash: 177b61cab99d21a844298632020244fa424d8d2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971217"
---
# <a name="helpprovider-component-overview-windows-forms"></a>Visão geral do componente HelpProvider (Windows Forms)
O componente [HelpProvider](helpprovider-component-windows-forms.md) dos Windows Forms é usado para associar um arquivo da Ajuda HTML 1.x (um arquivo .chm, produzido com o Workshop de Ajuda HTML ou um arquivo .htm) ao seu aplicativo do Windows. É possível fornecer ajuda de várias maneiras:  
  
- Fornece Ajuda contextual para controles nos Windows Forms.  
  
- Fornece Ajuda contextual em uma caixa de diálogo específica ou controles específicos em uma caixa de diálogo.  
  
- Abra um arquivo de Ajuda para áreas específicas, como a página principal de um sumário, índice ou uma função de pesquisa.  
  
## <a name="using-the-help-provider"></a>Usando o provedor de ajuda  
 Adicionando um <xref:System.Windows.Forms.HelpProvider> componente ao seu formulário do Windows permite que os outros controles no formulário para expor as propriedades de Ajuda do <xref:System.Windows.Forms.HelpProvider> componente. Isso habilita você a fornecer ajuda para os controles no seu Windows Form. Você pode associar um arquivo de ajuda com o <xref:System.Windows.Forms.HelpProvider> componente usando o <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriedade. Você especifica o tipo de ajuda oferecida chamando <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> e fornecendo um valor da <xref:System.Windows.Forms.HelpNavigator> enumeração para o controle especificado. Forneça a palavra-chave ou o tópico para obter ajuda ao chamar o <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> método.  
  
 Opcionalmente, para associar uma cadeia de caracteres de ajuda específica com outro controle, use o <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> método. A cadeia de caracteres associada a um controle usando esse método é exibida em uma janela pop-up quando o usuário pressiona a tecla F1 enquanto o controle tem o foco.  
  
 Se <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> não tiver sido definida, você deve usar <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> para fornecer o texto de Ajuda. Se você tiver definido os dois <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> e a cadeia de caracteres de Ajuda, ajuda com base em <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> terá precedência.  
  
> [!NOTE]
>  Você pode encontrar problemas ao usar o caminho relativo ao especificar o caminho para o arquivo de ajuda na <xref:System.Windows.Forms.Help.ShowHelp%2A> método ou <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriedade do <xref:System.Windows.Forms.HelpProvider> controle. Por isso, verifique se você usou o caminho de arquivo absoluto para especificar o arquivo de Ajuda.  
  
## <a name="see-also"></a>Consulte também

- [Sistemas de Ajuda em Aplicativos dos Windows Forms](../advanced/help-systems-in-windows-forms-applications.md)
