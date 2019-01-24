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
ms.openlocfilehash: 3bcf78ce6fe0e56e027b2d473a95d6663971744d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588217"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>Conversores de tipo e extensões de marcação para XAML
Conversores de tipo e extensões de marcação são duas técnicas que os sistemas de tipos XAML e gravadores XAML usam para gerar os componentes do grafo de objeto. Embora eles compartilham algumas características, conversores de tipo e extensões de marcação são representadas de forma diferente em um fluxo de nó XAML. Nesta documentação conjunto, conversores de tipo, extensões de marcação e construções semelhantes são, às vezes, coletivamente denominadas conversores de valor.  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>Conversores de valor  
 No XAML, conversores de valor são usadas para vários cenários. A lista a seguir mostra os diferentes tipos de conversores de valor em XAML:  
  
-   Conversor de tipo  
  
-   Extensão de marcação  
  
-   Serializador de valor  
  
-   Classe relacionada ou classe de suporte que fornece a lógica para uma sintaxe de texto XAML  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Conversores de tipo  
 Na definição de serviços de XAML do .NET Framework, conversores de tipo são classes que derivam de CLR <xref:System.ComponentModel.TypeConverter> classe. <xref:System.ComponentModel.TypeConverter> é uma classe que estava no Microsoft .NET Framework antes de que existiu XAML. Seu propósito original era oferecer suporte a janelas de propriedade e semelhante com base em texto edição metáforas para [!INCLUDE[TLA2#tla_ide](../../../includes/tla2sharptla-ide-md.md)] propriedades. A introdução de XAML do .NET Framework usa <xref:System.ComponentModel.TypeConverter> para converter uma sintaxe de texto (como encontrado em um valor de atributo ou um nó de valor XAML) em um objeto. <xref:System.ComponentModel.TypeConverter> também pode ser usado para serializar um valor de objeto para a sintaxe de texto. <xref:System.ComponentModel.TypeConverter> também foi usada nas implementações de XAML específicos de estrutura anteriores no Windows Presentation Foundation (WPF) e o Windows Communication Foundation (WCF). Para obter mais informações sobre o <xref:System.ComponentModel.TypeConverter> em XAML, consulte [conversores de tipo para visão geral de XAML](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Extensões de marcação  
 Na implementação de serviços de XAML do .NET Framework, extensões de marcação são classes que derivam de <xref:System.Windows.Markup.MarkupExtension> classe. Extensões de marcação são um conceito que é originado de linguagem XAML nesse formulário. Você pode considerar uma extensão de marcação como sendo algo parecido com uma sequência de escape extensível que chama uma classe de serviço para fornecer sua lógica. Em termos de marcação, os processadores XAML universalmente reconhecem uma extensão de marcação por uma sequência de texto que começa com uma chave de abertura ({}) em uma cadeia de caracteres de texto.  
  
 Extensões de marcação diferem dos conversores de tipo. Conversores de tipo são geralmente associados a tipos ou membros. Eles são chamados quando a criação de um gráfico de objeto ou uma serialização encontra a sintaxe de texto que está associado essas entidades.  
  
 Extensões de marcação estão associadas com uma única classe de serviço de suporte, mas podem ser aplicadas para qualquer valor de membro. (No entanto, você pode implementar sua extensão de marcação para restringir o seu uso deliberadamente a certos membros ou tipos de destino, usando o contexto de serviço). Extensões de marcação podem substituir uma associação de conversor de tipo. Ou você pode usá-los para especificar um valor de atributo para os membros que não seriam compatíveis caso contrário, uma sintaxe de texto.  
  
 Para obter mais informações sobre o padrão de implementação de extensão de marcação para XAML, consulte [extensões de marcação para visão geral de XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
> [!NOTE]
>  O <xref:System.Windows.Markup.MarkupExtension> e <xref:System.Windows.Markup.ValueSerializer> tipos estão na <xref:System.Windows.Markup> namespace e não no <xref:System.Xaml> namespace. Isso não significa que esses tipos são específicos para o Windows Forms ou WPF tecnologias que preenchem caso contrário, os namespaces CLR que contêm a cadeia de caracteres `Windows`. <xref:System.Windows.Markup.MarkupExtension> e <xref:System.Windows.Markup.ValueSerializer> estão no assembly System. XAML e não têm nenhuma dependência de estrutura específica. Esses tipos existiam no namespace CLR para [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] e permanecem no namespace CLR em [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] para evitar a interrupção de referências em projetos existentes do WPF. Para obter mais informações, consulte [tipos migrados do WPF para System. XAML](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md).  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>Serializadores de valor  
 Um <xref:System.Windows.Markup.ValueSerializer> é um conversor de tipo especializado que é otimizado para converter um objeto em uma cadeia de caracteres. Um <xref:System.Windows.Markup.ValueSerializer> para XAML não pode implementar o `ConvertFrom` método nada. Um <xref:System.Windows.Markup.ValueSerializer> implementação obtém serviços de maneira semelhante a um <xref:System.ComponentModel.TypeConverter> implementação. Os métodos virtuais fornecem uma entrada `context` parâmetro. O `context` parâmetro é do tipo <xref:System.Windows.Markup.IValueSerializerContext>, que herda da <xref:System.IServiceProvider> interface e tem um <xref:System.IServiceProvider.GetService%2A> método.  
  
 No sistema de tipos XAML e implementações de gravador XAML que utilizam o processamento de loop de nó XAML para serialização, um conversor de valor que está associado um tipo ou membro é reportado pelo seu próprio <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> propriedade. O significado para gravadores XAML que realizam serialização é que, se um <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> e <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> existir, o conversor de tipo deve ser usado para o caminho de carregamento e o serializador de valor deve ser usado para salvar caminho. Se <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> existe, mas <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> é `null`, o conversor de tipo também é usado para salvar caminho.  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>Outros conversores de valor  
 Um conversor de valor é extensível além de padrões específicos de um conversor de tipo ou uma extensão de marcação. No entanto, essa personalização também exigiria a redefinição do sistema de tipo XAML conforme fornecidas pelos serviços XAML do .NET Framework. O sistema de tipo XAML existente tem representações e os sistemas de relatórios para os serializadores de valor, extensões de marcação e conversores de tipo, mas não para os formulários personalizados de conversão do valor. Se você quiser criar conversores de valor personalizado, use o <xref:System.Xaml.Schema.XamlValueConverter%601> tipo.  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>Conversores de tipo e extensões de marcação em combinação  
 Conversores de tipo e de extensões de marcação são usados para diferentes situações no XAML. Embora o contexto esteja disponível para usos de extensão de marcação, o comportamento de conversão de tipos de propriedades em que uma extensão de marcação fornece um valor geralmente não é verificado em implementações de extensão de marcação. Em outras palavras, mesmo se uma extensão de marcação retorna uma cadeia de caracteres de texto como seu `ProvideValue` de saída, o comportamento de conversão de tipo dessa cadeia de caracteres conforme aplicado a uma propriedade específica ou um tipo de valor de propriedade não é invocado. Em geral, a finalidade de uma extensão de marcação é processar uma cadeia de caracteres e retornar um objeto sem nenhum conversor de tipo envolvido.  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>Contexto de serviço para um conversor de valor  
 Quando você implementa um conversor de valor, você geralmente precisa de acesso a um contexto em que o conversor de valor é aplicado. Nesse contexto é conhecido como o contexto de serviço. O contexto de serviço podem incluir informações como o contexto de esquema XAML ativo, acesso ao sistema de mapeamento de tipo que o contexto de esquema XAML e o gravador de XAML do objeto forneçam e assim por diante. Para obter mais informações sobre os contextos de serviço disponíveis para um conversor de valor e como acessar os serviços que pode ser fornecer um contexto de serviço, consulte [contextos de serviço disponíveis para conversores de tipo e extensões de marcação](../../../docs/framework/xaml-services/service-contexts-available-to-type-converters-and-markup-extensions.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Visão geral das extensões de marcação para XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)
- [Visão geral de conversores de tipo para XAML](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md)
- [Contextos de serviço disponíveis para conversores de tipo e extensões de marcação](../../../docs/framework/xaml-services/service-contexts-available-to-type-converters-and-markup-extensions.md)
