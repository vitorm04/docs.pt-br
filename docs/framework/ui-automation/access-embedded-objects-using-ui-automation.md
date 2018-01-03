---
title: "Acessar objetos inseridos usando automação de interface de usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
caps.latest.revision: "17"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 37110708efa49912d0ed9c81746d125167e17985
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="access-embedded-objects-using-ui-automation"></a>Acessar objetos inseridos usando automação de interface de usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico mostra como [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pode ser usada para expor objetos inseridos dentro do conteúdo de um controle de texto.  
  
> [!NOTE]
>  Objetos inseridos podem incluir imagens, hiperlinks, botões, tabelas ou controles ActiveX.  
  
 Objetos inseridos são considerados filhos do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] provedor de texto. Isso permite que eles sejam expostos pela estrutura de árvore de automação de interface do usuário como todos os outros [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementos. Funcionalidade, por sua vez, é exposta através de padrões de controle normalmente pelo tipo de controle de objetos inseridos (por exemplo, como os hiperlinks são baseados em texto, suportarão <xref:System.Windows.Automation.TextPattern>).  
  
 ![Objetos inseridos em um contêiner de texto. ] (../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
Um documento de exemplo com conteúdo textual ("Você sabia?" ...) e dois objetos inseridos (uma imagem de um baleia e um hiperlink de texto), usados como um destino para os exemplos de código.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como recuperar uma coleção de objetos inseridos de dentro um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] provedor de texto. O documento de exemplo fornecido na introdução, dois objetos seriam retornados (um elemento de imagem e um elemento de texto).  
  
> [!NOTE]
>  O elemento de imagem deve ter algum texto intrínseco associado a ele que descreva a imagem, normalmente em seu <xref:System.Windows.Automation.AutomationElement.NameProperty> (por exemplo, "Uma baleia azul."). No entanto, quando um intervalo de texto abrangendo o objeto de imagem é obtido, nem a imagem nem esse texto descritivo é retornado no fluxo de texto.  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como obter um intervalo de texto de um objeto inserido em um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] provedor de texto. O intervalo de texto recuperado é um intervalo vazio onde o ponto de extremidade inicial segue "... oceano. (espaço) "e o ponto de extremidade final precede o". "que representa o hiperlink inserido (como mostrado pela imagem exibida na Introdução). Embora esse seja um intervalo vazio, ele não é considerado um intervalo degenerado porque ele tem uma extensão diferente de zero.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.TextPattern>pode recuperar um objeto inserido baseado em texto, como um hiperlink; No entanto, um secundário <xref:System.Windows.Automation.TextPattern> terá que ser obtido a partir do objeto inserido para expor sua funcionalidade completa.  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de TextPattern de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Adicionar conteúdo a uma caixa de texto utilizando automação da interface do usuário](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [Localizar e destacar texto usando automação de interface do usuário](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
