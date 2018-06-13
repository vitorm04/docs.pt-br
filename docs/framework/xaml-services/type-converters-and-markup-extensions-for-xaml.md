---
title: Conversores de tipo e extensões de marcação para XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services
- XAML [XAML Services], value converters
- XAML [XAML Services], markup extension services
- value converters for XAML [XAML Services]
- XAML [XAML Services], service context
ms.assetid: db07a952-05ce-4aa4-b6f9-aac7397d0326
ms.openlocfilehash: 0c9cb7e87416860dda98df0da967ffbc070bc270
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565857"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>Conversores de tipo e extensões de marcação para XAML
Conversores de tipo e extensões de marcação são duas técnicas que sistemas de tipo XAML e gravadores XAML usam para gerar os componentes de gráfico de objeto. Embora eles compartilham algumas características, conversores de tipo e extensões de marcação são representadas diferentemente em um fluxo do nó XAML. Nesta documentação conjunto, conversores de tipo, extensões de marcação e construções semelhantes são às vezes chamadas, coletivamente como conversores de valor.  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>Conversores de valor  
 Em XAML, conversores de valor são usadas para vários cenários. A lista a seguir mostra os diferentes tipos de conversores de valor em XAML:  
  
-   Conversor de tipo  
  
-   Extensão de marcação  
  
-   Serializador de valor  
  
-   Classe relacionada ou classe de suporte que fornece a lógica para uma sintaxe de texto XAML  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Conversores de tipo  
 Na definição de serviços XAML do .NET Framework, conversores de tipo são classes que derivam de CLR <xref:System.ComponentModel.TypeConverter> classe. <xref:System.ComponentModel.TypeConverter> é uma classe que estava no Microsoft .NET Framework antes da existência desse XAML. Sua finalidade original foi oferecer suporte a janelas de propriedade e semelhantes baseado em texto edição metáforas para [!INCLUDE[TLA2#tla_ide](../../../includes/tla2sharptla-ide-md.md)] propriedades. A introdução de XAML do .NET Framework usa <xref:System.ComponentModel.TypeConverter> para converter uma sintaxe de texto (como encontrado em um valor de atributo ou um nó de valor XAML) em um objeto. <xref:System.ComponentModel.TypeConverter> também pode ser usado para serializar um valor de objeto para a sintaxe do texto. <xref:System.ComponentModel.TypeConverter> também foi usado em implementações de XAML específica da estrutura anteriores no Windows Presentation Foundation (WPF) e Windows Communication Foundation (WCF). Para obter mais informações sobre o <xref:System.ComponentModel.TypeConverter> em XAML, consulte [conversores de tipo para XAML Overview](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Extensões de marcação  
 Na implementação de serviços XAML do .NET Framework, extensões de marcação são classes que derivam de <xref:System.Windows.Markup.MarkupExtension> classe. Extensões de marcação são um conceito originadas neste formulário é a linguagem XAML. Você pode pensar em uma extensão de marcação como sendo algo como uma sequência de escape extensível que chama uma classe de serviço para fornecer sua lógica. Em termos de marcação, processadores XAML universalmente reconhecem uma extensão de marcação por uma sequência de texto que começa com uma chave de abertura ({}) em uma cadeia de caracteres de texto.  
  
 Extensões de marcação diferem de conversores de tipo. Conversores de tipo são geralmente associados com tipos ou membros. Eles são chamados quando a criação de um gráfico de objeto ou uma serialização encontra a sintaxe do texto que está associado essas entidades.  
  
 Extensões de marcação estão associadas uma única classe de serviço de suporte, mas podem ser aplicadas a qualquer valor de membro. (No entanto, você pode implementar sua extensão de marcação para impedir que seu uso deliberadamente a certos membros ou tipos de destino, usando o contexto do serviço). Extensões de marcação podem substituir uma associação de conversor de tipo. Ou você pode usá-los para especificar um valor de atributo de membros que do contrário não dará suporte a uma sintaxe de texto.  
  
 Para obter mais informações sobre o padrão de implementação de extensão de marcação XAML, consulte [extensões de marcação para XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
> [!NOTE]
>  O <xref:System.Windows.Markup.MarkupExtension> e <xref:System.Windows.Markup.ValueSerializer> tipos estiverem no <xref:System.Windows.Markup> namespace e não no <xref:System.Xaml> namespace. Isso não significa que esses tipos são específicos para o WPF ou Windows Forms tecnologias que preenchem caso contrário, os namespaces CLR que contém a cadeia de caracteres `Windows`. <xref:System.Windows.Markup.MarkupExtension> e <xref:System.Windows.Markup.ValueSerializer> no assembly System. XAML e não têm nenhuma dependência de estrutura específica. Esses tipos existiam no namespace CLR para [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] e permanecem no namespace CLR em [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] para evitar que as referências em projetos existentes do WPF. Para obter mais informações, consulte [tipos migrados do WPF para System. XAML](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md).  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>Valor serializadores  
 Um <xref:System.Windows.Markup.ValueSerializer> é um conversor de tipo especializado que é otimizado para converter um objeto para uma cadeia de caracteres. Um <xref:System.Windows.Markup.ValueSerializer> para XAML não pode implementar o `ConvertFrom` método todos. Um <xref:System.Windows.Markup.ValueSerializer> implementação obtém de modo semelhante a um <xref:System.ComponentModel.TypeConverter> implementação. Os métodos virtuais fornecem uma entrada `context` parâmetro. O `context` parâmetro é do tipo <xref:System.Windows.Markup.IValueSerializerContext>, que herda do <xref:System.IServiceProvider> interface e tem um <xref:System.IServiceProvider.GetService%2A> método.  
  
 No sistema de tipo XAML e implementações de gravador XAML que usam o processamento de loop de nó XAML para serialização, um conversor de valor que está associado um tipo ou membro é reportado pelo seu próprio <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> propriedade. O significado para gravadores XAML que executar a serialização é que, se um <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> e <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> existir, o conversor de tipo deve ser usado para o caminho de carga e o serializador de valor deve ser usado para salvar caminho. Se <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> existe mas <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> é `null`, o conversor de tipo também é usado para salvar caminho.  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>Outros conversores de valor  
 Um conversor de valor é extensível além de padrões específicos de um conversor de tipo ou uma extensão de marcação. No entanto, essa personalização também requer a redefinição do sistema de tipo XAML conforme fornecido por serviços XAML do .NET Framework. O sistema de tipo XAML existente tem representações e sistemas de relatório para conversores de tipo, extensões de marcação e serializadores de valor, mas não para formas personalizadas de conversão do valor. Se você quiser criar conversores de valor personalizado, use o <xref:System.Xaml.Schema.XamlValueConverter%601> tipo.  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>Conversores de tipo e extensões de marcação em combinação  
 Conversores de tipo e de extensões de marcação são usados para situações diferentes em XAML. Embora o contexto esteja disponível para usos de extensão de marcação, o comportamento de conversão de tipos de propriedades em que uma extensão de marcação fornece um valor geralmente não é verificado em implementações de extensão de marcação. Em outras palavras, mesmo se uma extensão de marcação retorna uma cadeia de caracteres de texto como seu `ProvideValue` de saída, comportamento de conversão de tipo na cadeia de caracteres conforme aplicado a uma propriedade específica ou um tipo de valor de propriedade não é invocado. Em geral, a finalidade de uma extensão de marcação é processar uma cadeia de caracteres e retornam um objeto sem qualquer conversor de tipo envolvidos.  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>Contexto de serviço para um conversor de valor  
 Quando você implementar um conversor de valor, você geralmente precisa acessar um contexto em que o conversor de valor é aplicado. Neste contexto é conhecido como o contexto do serviço. No contexto do serviço podem incluir informações como o contexto do esquema XAML active, acesso ao sistema de mapeamento de tipo que o contexto do esquema XAML e o gravador de objeto XAML forneçam e assim por diante. Para obter mais informações sobre os contextos de serviço disponíveis para um conversor de valor e como acessar os serviços que pode fornecer um contexto de serviço, consulte [contextos de serviço disponíveis para conversores de tipo e extensões de marcação](../../../docs/framework/xaml-services/service-contexts-available-to-type-converters-and-markup-extensions.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Markup.MarkupExtension>  
 <xref:System.Xaml.XamlObjectWriter>  
 [Visão geral das extensões de marcação para XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)  
 [Visão geral de conversores de tipo para XAML](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md)  
 [Contextos de serviço disponíveis para conversores de tipo e extensões de marcação](../../../docs/framework/xaml-services/service-contexts-available-to-type-converters-and-markup-extensions.md)
