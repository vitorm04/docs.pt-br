---
title: Limitações de serialização de XamlWriter.Save
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 96e917898320fb5d49f4e7dfc27daa7750af9d41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174362"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>Limitações de serialização de XamlWriter.Save
A API <xref:System.Windows.Markup.XamlWriter.Save%2A> pode ser usada para [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] serializar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] o conteúdo de um aplicativo como um arquivo. No entanto, existem algumas limitações importantes em exatamente o que é serializado. Essas limitações e algumas considerações gerais são documentadas neste tópico.  

<a name="Run_Time__Not_Design_Time_Representation"></a>
## <a name="run-time-not-design-time-representation"></a>Representação de tempo de execução, não em tempo de design  
 A filosofia básica do que é <xref:System.Windows.Markup.XamlWriter.Save%2A> serializado por uma chamada é que o resultado será uma representação do objeto que está sendo serializado, em tempo de execução. Muitas propriedades de tempo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de projeto do arquivo original podem já [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ser otimizadas ou perdidas no momento em <xref:System.Windows.Markup.XamlWriter.Save%2A> que o é carregado como objetos na memória, e não são preservados quando você chama para serializar. O resultado serializado é uma representação efetiva da árvore lógica construída do aplicativo, mas não necessariamente do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] original que a produziu. Essas questões tornam extremamente <xref:System.Windows.Markup.XamlWriter.Save%2A> difícil usar a serialização como parte de uma extensa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] superfície de design.  
  
<a name="Serialization_is_Self_Contained"></a>
## <a name="serialization-is-self-contained"></a>A serialização é independente  
 A saída serializada de <xref:System.Windows.Markup.XamlWriter.Save%2A> é independente; tudo o que é serializado está contido dentro de uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] única página, com um único elemento raiz, e sem referências externas além de URIs. Por exemplo, se sua página tiver referenciado recursos de recursos do aplicativo, eles aparecerão como se fossem um componente da página que está sendo serializada.  
  
<a name="Extension_References_are_Dereferenced"></a>
## <a name="extension-references-are-dereferenced"></a>Referências de extensão são desreferenciadas  
 Referências comuns a objetos feitas por vários formatos de extensão de marcação, como `StaticResource` ou `Binding`, serão desreferenciadas pelo processo de serialização. Estes já foram desreferenciados no momento em que objetos na <xref:System.Windows.Markup.XamlWriter.Save%2A> memória foram criados [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pelo tempo de execução do aplicativo, e a lógica não revisita o original para restaurar tais referências à saída serializada. Isso potencialmente congela qualquer valor obtido de associação de dados ou recurso como sendo o valor usado pela última vez pela representação de tempo de execução, com capacidade apenas limitada ou indireta para distinguir esse valor de qualquer outro valor definido localmente. As imagens também são serializadas como referências de objeto a imagens como elas existem no projeto, em vez de como referências originais de origem, perdendo qualquer nome de arquivo ou URI foi originalmente referenciado. Até mesmo recursos declarados na mesma página são vistos serializados no ponto em que foram referenciados, em vez de serem preservados como uma chave de uma coleção de recursos.  
  
<a name="Event_Handling_is_Not_Preserved"></a>
## <a name="event-handling-is-not-preserved"></a>A manipulação de eventos não é preservada  
 Quando os manipuladores de eventos que são adicionados por meio de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] são serializados, eles não são preservados. O [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sem code-behind (e também sem o mecanismo x:Code relacionado) não tem como serializar a lógica de procedimento de runtime. Uma vez que a serialização é independente e limitada à árvore lógica, não há recurso para armazenar os manipuladores de eventos. Como resultado, os atributos de manipulador de eventos, tanto o atributo em si quanto o valor de cadeia de caracteres que nomeia o manipulador, são removidos da saída [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>Cenários realistas para uso de XAMLWriter.Save  
 Embora as limitações aqui listadas sejam bastante substanciais, <xref:System.Windows.Markup.XamlWriter.Save%2A> ainda existem vários cenários apropriados para uso para serialização.  
  
- Saída vetorial ou gráfica: a saída da área de dados renderizados pode ser usada para reproduzir os mesmos vetores ou gráficos quando recarregada.  
  
- Documentos de fluxo e rich text: texto e toda a formação e confinamento de elementos dentro dele são preservados na saída. Isso pode ser útil para mecanismos que se aproximam de uma funcionalidade de área de transferência.  
  
- Preservando dados de objetos de negócios: Se você tiver armazenado dados em elementos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] personalizados, como dados XML, desde que seus objetos de negócios sigam regras básicas, como fornecer construtores personalizados e conversão para valores de propriedade por referência, esses objetos de negócios podem ser perpetuados através da serialização.
