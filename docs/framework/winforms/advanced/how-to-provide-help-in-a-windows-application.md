---
title: Como fornecer ajuda em um aplicativo do Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d23e5d5d19e17aedd37d4d5f6cbc41429463ddfb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Como fornecer ajuda em um aplicativo do Windows
Você pode usar o <xref:System.Windows.Forms.HelpProvider> componente anexar tópicos da Ajuda em um arquivo de ajuda a controles específicos em formulários do Windows. O arquivo de Ajuda pode ser HTML ou HTMLHelp 1.x ou formato maior.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-provide-help"></a>Para fornecer Ajuda  
  
1.  Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.HelpProvider> componente para seu formulário.  
  
     O componente ficará na bandeja na parte inferior do Designer de Formulários do Windows.  
  
2.  No **propriedades** janela, defina o <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriedade para o arquivo de Ajuda. chm,. col ou. htm.  
  
3.  Selecione outro controle que você tem em seu formulário e, no **propriedades** janela, defina o <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> propriedade.  
  
     Isso é a cadeia de caracteres passada a <xref:System.Windows.Forms.HelpProvider> componente ao seu arquivo de ajuda para chamar o tópico de Ajuda apropriado.  
  
4.  No **propriedades** janela, defina o <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> propriedade com um valor da <xref:System.Windows.Forms.HelpNavigator> enumeração.  
  
     Isso determina o modo como a propriedade **HelpKeyword** é passada para o sistema de Ajuda. A tabela a seguir mostra as possíveis configurações e suas descrições.  
  
    |Nome do Membro|Descrição|  
    |-----------------|-----------------|  
    |AssociateIndex|Especifica que o índice para um tópico especificado é realizado na URL especificada.|  
    |Localizar|Especifica que a página de pesquisa de uma URL especificada é exibida.|  
    |Índice|Especifica que o índice de uma URL especificada é exibido.|  
    |KeywordIndex|Especifica uma palavra-chave para pesquisar e a ação a ser tomada na URL especificada.|  
    |TableOfContents|Especifica que o sumário do arquivo de Ajuda HTML 1.0 é exibido.|  
    |Tópico|Especifica que o tópico referenciado por uma URL especificada é exibido.|  
  
 Em tempo de execução, pressionando F1 quando o controle — para que você tenha definido a **HelpKeyword** e **HelpNavigator** propriedades — tem foco irá abrir o arquivo de ajuda associado que <xref:System.Windows.Forms.HelpProvider> componente.  
  
 Atualmente, a propriedade **HelpNamespace** dá suporte a arquivos de Ajuda nos três formatos a seguir: HTMLHelp 1.x, HTMLHelp 2.0 e HTML. Assim, você pode definir a propriedade **HelpNamespace** para um endereço http://, como uma página da Web. Se isso for feito, abrirá o navegador padrão para a página da Web com a cadeia de caracteres especificada na propriedade **HelpKeyword** usada como âncora. A âncora é usada para ir para uma parte específica de uma página HTML.  
  
> [!IMPORTANT]
>  Tenha cuidado para verificar as informações que são enviadas de um cliente antes de usá-las em seu aplicativo. Usuários mal-intencionados podem tentar enviar ou injetar script executável, instruções SQL ou outro código. Antes de exibir a entrada do usuário, armazená-la em um banco de dados ou trabalhar com ela, verifique se ela não contém informações potencialmente não seguras. Uma maneira comum de verificar é usar uma expressão regular para procurar palavras-chave como "SCRIPT" ao receber entrada de um usuário.  
  
 Você também pode usar o <xref:System.Windows.Forms.HelpProvider> componente para exibir ajuda pop-up, mesmo se você tiver configurado para exibir arquivos de ajuda para os controles em seus formulários do Windows. Para obter mais informações, consulte [Como exibir Ajuda em pop-up](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como Exibir Ajuda Pop-up](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 [Ajuda de Controle Usando ToolTips](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [Integrando a Ajuda do Usuário nos Windows Forms](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
