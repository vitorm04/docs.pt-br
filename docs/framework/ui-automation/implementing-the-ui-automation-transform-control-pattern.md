---
title: Implementando o Padrão de Controle de Transformação de Automação de IU
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: 5643bc85972ea33cc31b1a83ecf7615dbb275bc2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180048"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>Implementando o Padrão de Controle de Transformação de Automação de IU
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.ITransformProvider>convenções para a implementação, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listados no final do tópico.  
  
 O <xref:System.Windows.Automation.TransformPattern> padrão de controle é usado para suportar controles que podem ser movidos, redimensionados ou girados dentro de um espaço bidimensional. Para exemplos de controles que implementam esse padrão de controle, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
 Ao implementar o padrão de controle Transformar, observe as seguintes diretrizes e convenções:  
  
- O suporte para este padrão de controle não se limita a objetos na área de trabalho. Este padrão de controle também deve ser suportado pelas crianças de um objeto de contêiner se as crianças podem ser movidas, redimensionadas ou giradas livremente dentro dos limites do recipiente.  
  
- Um objeto não pode ser movido, redimensionado ou girado de tal forma que sua localização de tela resultante estaria completamente fora das coordenadas de seu contêiner e, portanto, inacessível para o teclado ou mouse (por exemplo, quando uma janela de nível superior é movida para fora da tela ou uma objeto criança é movido para fora dos limites do viewport do contêiner). Nesses casos, o objeto é colocado o mais próximo possível das coordenadas de tela solicitadas com as coordenadas superior ou esquerda substituídas para estar dentro dos limites do contêiner.  
  
- Para sistemas de vários monitores, se um objeto for movido, redimensionado ou girado completamente fora das coordenadas combinadas da tela da área de trabalho, o objeto será colocado no monitor principal o mais próximo possível das coordenadas solicitadas.  
  
- Todos os parâmetros e valores de propriedade são absolutos e independentes da localidade.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-itransformprovider"></a>Membros obrigatórios para ITransformProvider  
 As seguintes propriedades e métodos <xref:System.Windows.Automation.Provider.ITransformProvider>são necessários para a implementação.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Método|Nenhum|  
  
 Este padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceções  
 Os provedores devem lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> - Se <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> o é falso.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> - Se <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> o é falso.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> - Se <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> o é falso.|  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
