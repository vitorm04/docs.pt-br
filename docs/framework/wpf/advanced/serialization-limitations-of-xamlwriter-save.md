---
title: Limitações de serialização de XamlWriter.Save
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 0416b92a6264e6a8261355197b4ab2fa61f80ef2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582588"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>Limitações de serialização de XamlWriter.Save
O <xref:System.Windows.Markup.XamlWriter.Save%2A> de API pode ser usado para serializar o conteúdo de um aplicativo de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] como um arquivo de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. No entanto, existem algumas limitações importantes em exatamente o que é serializado. Essas limitações e algumas considerações gerais são documentadas neste tópico.  

<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>Representação de tempo de execução, não em tempo de design  
 A filosofia básica do que é serializado por uma chamada para <xref:System.Windows.Markup.XamlWriter.Save%2A> é que o resultado será uma representação do objeto que está sendo serializado, em tempo de execução. Muitas propriedades de tempo de design do arquivo de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] original já podem ser otimizadas ou perdidas quando o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é carregado como objetos na memória e não são preservados quando você chama <xref:System.Windows.Markup.XamlWriter.Save%2A> para serializar. O resultado serializado é uma representação efetiva da árvore lógica construída do aplicativo, mas não necessariamente do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] original que a produziu. Esses problemas tornam extremamente difícil usar a serialização de <xref:System.Windows.Markup.XamlWriter.Save%2A> como parte de uma ampla superfície de design de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>A serialização é independente  
 A saída serializada de <xref:System.Windows.Markup.XamlWriter.Save%2A> é independente; Tudo o que é serializado está contido em uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] única página, com um único elemento raiz, e sem referências externas além de URIs. Por exemplo, se sua página tiver referenciado recursos de recursos do aplicativo, eles aparecerão como se fossem um componente da página que está sendo serializada.  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>Referências de extensão são desreferenciadas  
 Referências comuns a objetos feitas por vários formatos de extensão de marcação, como `StaticResource` ou `Binding`, serão desreferenciadas pelo processo de serialização. Eles já foram desreferenciados no momento em que os objetos na memória foram criados pelo tempo de execução do aplicativo e a lógica de <xref:System.Windows.Markup.XamlWriter.Save%2A> não revisita o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] original para restaurar essas referências à saída serializada. Isso potencialmente congela qualquer valor obtido de associação de dados ou recurso como sendo o valor usado pela última vez pela representação de tempo de execução, com capacidade apenas limitada ou indireta para distinguir esse valor de qualquer outro valor definido localmente. As imagens também são serializadas como referências de objeto para imagens conforme elas existem no projeto, em vez de como referências de origem originais, perdendo qualquer nome de arquivo ou URI originalmente referenciado. Até mesmo recursos declarados na mesma página são vistos serializados no ponto em que foram referenciados, em vez de serem preservados como uma chave de uma coleção de recursos.  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>A manipulação de eventos não é preservada  
 Quando os manipuladores de eventos que são adicionados por meio de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] são serializados, eles não são preservados. O [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sem code-behind (e também sem o mecanismo x:Code relacionado) não tem como serializar a lógica de procedimento de tempo de execução. Uma vez que a serialização é independente e limitada à árvore lógica, não há recurso para armazenar os manipuladores de eventos. Como resultado, os atributos de manipulador de eventos, tanto o atributo em si quanto o valor de cadeia de caracteres que nomeia o manipulador, são removidos da saída [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>Cenários realistas para uso de XAMLWriter.Save  
 Embora as limitações listadas aqui sejam bastante substanciais, ainda há vários cenários apropriados para usar <xref:System.Windows.Markup.XamlWriter.Save%2A> para serialização.  
  
- Saída vetorial ou gráfica: a saída da área de dados renderizados pode ser usada para reproduzir os mesmos vetores ou gráficos quando recarregada.  
  
- Documentos de fluxo e rich text: texto e toda a formação e confinamento de elementos dentro dele são preservados na saída. Isso pode ser útil para mecanismos que se aproximam de uma funcionalidade de área de transferência.  
  
- Preservando dados de objeto comercial: se você tiver dados armazenados em elementos personalizados, como dados [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], desde que seus objetos comerciais sigam regras [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] básicas, como fornecer construtores personalizados e conversão de valores de propriedade por referência, esses objetos comerciais poderão ser perpetuados por serialização.
