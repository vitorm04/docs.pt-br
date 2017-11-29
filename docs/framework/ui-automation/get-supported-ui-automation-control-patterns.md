---
title: "Obter Padrões de Controle de Automação de IU Suportados"
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
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
caps.latest.revision: "10"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 8917890d86f059d85ad9b6a0bcf6d9a41d65585a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="get-supported-ui-automation-control-patterns"></a>Obter Padrões de Controle de Automação de IU Suportados
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico mostra como recuperar objetos de padrão de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementos.  
  
### <a name="obtain-all-control-patterns"></a>Obter todos os padrões de controle  
  
1.  Obter o <xref:System.Windows.Automation.AutomationElement> cujos padrões de controle você está interessado.  
  
2.  Chamar <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> para obter todos os padrões de controle do elemento.  
  
> [!CAUTION]
>  É altamente recomendável que um cliente não usar <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Desempenho pode ser gravemente afetado, este método chama <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internamente para cada padrão de controle existente. Se possível, um cliente deve chamar <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> para os padrões-chave de interesse.  
  
### <a name="obtain-a-specific-control-pattern"></a>Obter um padrão de controle específicos  
  
1.  Obter o <xref:System.Windows.Automation.AutomationElement> cujos padrões de controle você está interessado.  
  
2.  Chamar <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> para consultar um padrão específico. Esses métodos são semelhantes, mas se o padrão não for encontrado, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> gera uma exceção, e <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> retorna `false`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir recupera um <xref:System.Windows.Automation.AutomationElement> para um item de lista e obtém um <xref:System.Windows.Automation.SelectionItemPattern> desse elemento.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Consulte também  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
