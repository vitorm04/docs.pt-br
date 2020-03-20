---
title: 'Implementando o padrão de controle MultipleView de interface de usuário '
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 9decb617e30a340d3e73e911f7848110de5599e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180164"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>Implementando o padrão de controle MultipleView de interface de usuário 
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.IMultipleViewProvider>convenções para a implementação, incluindo informações sobre eventos e propriedades. Links para referências adicionais são listados no final do tópico.  
  
 O <xref:System.Windows.Automation.MultipleViewPattern> padrão de controle é usado para suportar controles que fornecem, e são capazes de alternar entre múltiplas representações do mesmo conjunto de informações ou controles de crianças.  
  
 Exemplos de controles que podem apresentar várias visualizações incluem a exibição da lista (que pode mostrar seu conteúdo como miniaturas, telhas, ícones ou detalhes), gráficos do Microsoft Excel (torta, linha, barra, valor de celular com uma fórmula), documentos do Microsoft Word (normal, layout da Web, impressão layout, layout de leitura, contorno), calendário do Microsoft Outlook (ano, mês, semana, dia) e skins do Microsoft Windows Media Player. As visualizações suportadas são determinadas pelo desenvolvedor de controle e são específicas para cada controle.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
 Ao implementar o padrão de controle de exibição múltipla, observe as seguintes diretrizes e convenções:  
  
- <xref:System.Windows.Automation.Provider.IMultipleViewProvider>também deve ser implementado em um contêiner que gerencia a visualização atual se for diferente de um controle que fornece a visão atual. Por exemplo, o Windows Explorer contém um controle de lista para o conteúdo atual da pasta, enquanto a exibição do controle é gerenciada a partir do aplicativo Windows Explorer.  
  
- Um controle capaz de classificar seu conteúdo não é considerado para suportar múltiplas visualizações.  
  
- A coleção de visualizações deve ser idêntica entre as instâncias.  
  
- Os nomes de exibição devem ser adequados para uso em Texto para Fala, Braille e outras aplicações legíveis por humanos.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>
## <a name="required-members-for-imultipleviewprovider"></a>Membros necessários para IMultipleViewProvider  
 As seguintes propriedades e métodos são necessários para implementar o IMultipleViewProvider.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Método|Nenhum|  
  
 Não há eventos associados a este padrão de controle.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceções  
 O provedor deve lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Quando <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> ou <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> é chamado com um parâmetro que não é um membro da coleção de visualizações suportadas.|  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
