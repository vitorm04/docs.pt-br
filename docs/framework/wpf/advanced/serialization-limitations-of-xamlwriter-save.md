---
title: Limitações de serialização de XamlWriter.Save
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 89cb36dba63dccdf7e52b7fcafbe3d9fc2fea1e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113276"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>Limitações de serialização de XamlWriter.Save
O [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] <xref:System.Windows.Markup.XamlWriter.Save%2A> pode ser usado para serializar o conteúdo de um [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativo como um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo. No entanto, existem algumas limitações importantes em exatamente o que é serializado. Essas limitações e algumas considerações gerais são documentadas neste tópico.  

<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>Representação de tempo de execução, não em tempo de design  
 A filosofia básica do que é serializado por uma chamada para <xref:System.Windows.Markup.XamlWriter.Save%2A> é que o resultado será uma representação do objeto serializado, em tempo de execução. Muitas propriedades de tempo de design do original [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo já pode ser otimizado ou perdido no momento que o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é carregado como objetos na memória e não são preservadas quando você chama <xref:System.Windows.Markup.XamlWriter.Save%2A> para serializar. O resultado serializado é uma representação efetiva da árvore lógica construída do aplicativo, mas não necessariamente do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] original que a produziu. Esses problemas tornam extremamente difícil de usar o <xref:System.Windows.Markup.XamlWriter.Save%2A> serialização como parte de uma ampla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] superfície de design.  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>A serialização é independente  
 A saída serializada <xref:System.Windows.Markup.XamlWriter.Save%2A> é autônomo; tudo o que é serializado está contido dentro de uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] única página, com um único elemento raiz e nenhuma referência externa que [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]. Por exemplo, se sua página tiver referenciado recursos de recursos do aplicativo, eles aparecerão como se fossem um componente da página que está sendo serializada.  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>Referências de extensão são desreferenciadas  
 Referências comuns a objetos feitas por vários formatos de extensão de marcação, como `StaticResource` ou `Binding`, serão desreferenciadas pelo processo de serialização. Eles já foram desreferenciados no momento em que os objetos na memória foram criados pelo tempo de execução do aplicativo, e o <xref:System.Windows.Markup.XamlWriter.Save%2A> lógica não revisita original [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para restaurar essas referências para a saída serializada. Isso potencialmente congela qualquer valor obtido de associação de dados ou recurso como sendo o valor usado pela última vez pela representação de tempo de execução, com capacidade apenas limitada ou indireta para distinguir esse valor de qualquer outro valor definido localmente. As imagens também são serializadas como referências de objeto para imagens como elas existem no projeto e não como referências de fonte originais, perdendo qualquer nome de arquivo ou [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] originalmente referenciado. Até mesmo recursos declarados na mesma página são vistos serializados no ponto em que foram referenciados, em vez de serem preservados como uma chave de uma coleção de recursos.  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>A manipulação de eventos não é preservada  
 Quando os manipuladores de eventos que são adicionados por meio de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] são serializados, eles não são preservados. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sem code-behind (e também sem o mecanismo X:Code relacionado) não tem nenhuma maneira de serializar a lógica de procedimento de tempo de execução. Uma vez que a serialização é independente e limitada à árvore lógica, não há recurso para armazenar os manipuladores de eventos. Como resultado, os atributos de manipulador de eventos, tanto o atributo em si quanto o valor de cadeia de caracteres que nomeia o manipulador, são removidos da saída [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>Cenários realistas para uso de XAMLWriter.Save  
 Embora as limitações listadas aqui sejam bastante significativas, ainda há vários cenários apropriados para usar <xref:System.Windows.Markup.XamlWriter.Save%2A> para serialização.  
  
-   Saída vetorial ou gráfica: A saída da área de dados renderizados pode ser usada para reproduzir os mesmos vetores ou gráficos quando recarregada.  
  
-   Documentos de fluxo e de texto avançados: Texto e todos os confinamento de formatação e o elemento do elemento dentro dele é preservado na saída. Isso pode ser útil para mecanismos que se aproximam de uma funcionalidade de área de transferência.  
  
-   Preservando dados de objeto comercial: Se você tiver dados armazenados em elementos personalizados, como [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados, desde que seus objetos comerciais sigam básico [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] regras, como fornecer construtores personalizados e conversão para valores de propriedade por referência, esses objetos comerciais podem ser perpetuados por serialização.
