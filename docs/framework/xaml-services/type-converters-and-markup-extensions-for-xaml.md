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
ms.openlocfilehash: d31d970e8e95726aa789f853ac12c4830498a743
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796834"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>Conversores de tipo e extensões de marcação para XAML
Conversores de tipo e extensões de marcação são duas técnicas que os sistemas de tipos XAML e gravadores XAML usam para gerar componentes de gráfico de objeto. Embora eles compartilhem algumas características, os conversores de tipo e as extensões de marcação são representados de forma diferente em um fluxo de nó XAML. Neste conjunto de documentação, conversores de tipo, extensões de marcação e construções semelhantes são, às vezes, chamados coletivamente de conversores de valor.  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>Conversores de valor  
 Em XAML, os conversores de valor são usados para vários cenários. A lista a seguir mostra os diferentes tipos de conversores de valor em XAML:  
  
- Conversor de tipo  
  
- Extensão de marcação  
  
- Serializador de valor  
  
- Classe relacionada ou classe de suporte que fornece a lógica para uma sintaxe de texto XAML  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>Conversores de tipo  
 Na definição de serviços XAML .NET Framework, os conversores de tipo são classes que derivam <xref:System.ComponentModel.TypeConverter> da classe CLR. <xref:System.ComponentModel.TypeConverter>é uma classe que estava na estrutura de Microsoft .NET antes que o XAML existisse. Sua finalidade original era oferecer suporte a janelas de propriedades e metáforas de edição baseadas em texto semelhantes para propriedades do IDE. A introdução do XAML para .NET Framework usa <xref:System.ComponentModel.TypeConverter> o para converter uma sintaxe de texto (conforme encontrado em um valor de atributo ou um nó de valor XAML) em um objeto. <xref:System.ComponentModel.TypeConverter>também pode ser usado para serializar um valor de objeto para sintaxe de texto. <xref:System.ComponentModel.TypeConverter>também foi usado em implementações XAML específicas da estrutura anteriores no Windows Presentation Foundation (WPF) e no Windows Communication Foundation (WCF). Para obter mais informações sobre <xref:System.ComponentModel.TypeConverter> o em XAML, consulte [conversão de tipos para visão geral do XAML](type-converters-for-xaml-overview.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>Extensões de marcação  
 Na implementação de serviços XAML .NET Framework, as extensões de marcação são classes que derivam da <xref:System.Windows.Markup.MarkupExtension> classe. As extensões de marcação são um conceito que neste formulário é originado pela linguagem XAML. Você pode considerar uma extensão de marcação como algo como uma sequência de escape extensível que chama uma classe de serviço para fornecer sua lógica. Em termos de marcação, os processadores XAML reconhecem universalmente uma extensão de marcação por uma sequência de texto que começa com uma chave de abertura ({) em uma cadeia de texto.  
  
 As extensões de marcação diferem dos conversores de tipo. Os conversores de tipo normalmente são associados a tipos ou membros. Elas são invocadas quando uma criação de grafo de objeto ou uma serialização encontra a sintaxe de texto associada a essas entidades.  
  
 As extensões de marcação são associadas a uma única classe de serviço de suporte, mas podem ser aplicadas a qualquer valor de membro. (No entanto, você pode implementar sua extensão de marcação para restringir deliberadamente seu uso a determinados membros ou tipos de destino usando o contexto de serviço.) As extensões de marcação podem substituir uma associação de conversor de tipo. Ou você pode usá-los para especificar um valor de atributo para membros que, de outra forma, não ofereceriam suporte a uma sintaxe de texto.  
  
 Para obter mais informações sobre o padrão de implementação de extensão de marcação para XAML, consulte [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md).  
  
> [!NOTE]
>  Os <xref:System.Windows.Markup.MarkupExtension> <xref:System.Windows.Markup.ValueSerializer>tipose estão no <xref:System.Xaml> namespace e não no namespace. <xref:System.Windows.Markup> Isso não significa que esses tipos são específicos para as tecnologias WPF ou Windows Forms que, de outra forma, populam os namespaces `Windows`CLR que contêm a cadeia de caracteres. <xref:System.Windows.Markup.MarkupExtension>e <xref:System.Windows.Markup.ValueSerializer> estão no assembly System. XAML e não têm nenhuma dependência de estrutura específica. Esses tipos existiam no namespace CLR para .NET Framework 3,0 e permanecem no namespace CLR no .NET Framework 4 para evitar a quebra de referências em projetos existentes do WPF. Para obter mais informações, consulte [tipos migrados do WPF para System. XAML](types-migrated-from-wpf-to-system-xaml.md).  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>Serializadores de valor  
 Um <xref:System.Windows.Markup.ValueSerializer> é um conversor de tipo especializado que é otimizado para converter um objeto em uma cadeia de caracteres. Um <xref:System.Windows.Markup.ValueSerializer> for XAML pode não implementar o `ConvertFrom` método. Uma <xref:System.Windows.Markup.ValueSerializer> implementação obtém serviços de maneira semelhante a uma <xref:System.ComponentModel.TypeConverter> implementação. Os métodos virtuais fornecem um parâmetro `context` de entrada. O `context` parâmetro é do tipo <xref:System.Windows.Markup.IValueSerializerContext> <xref:System.IServiceProvider> , que é herdado da interface e tem <xref:System.IServiceProvider.GetService%2A> um método.  
  
 No sistema de tipos XAML e para implementações de gravador XAML que usam o processamento de loop de nó XAML para serialização, um conversor de valor associado a um tipo ou membro é <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> relatado por sua própria propriedade. O significado para os gravadores XAML que executam a serialização <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> é <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> que, se houver, o conversor de tipo deve ser usado para o caminho de carga e o valor do serializador deve ser usado para o caminho de salvamento. Se <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> existir, <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> mas `null`for, o conversor de tipo também será usado para o caminho de salvamento.  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>Outros conversores de valor  
 Um conversor de valor é extensível além dos padrões específicos de um conversor de tipo ou uma extensão de marcação. No entanto, essa personalização também exigiria a redefinição do sistema de tipos XAML, conforme fornecido pelo .NET Framework serviços XAML. O sistema de tipos XAML existente tem representações e sistemas de relatórios para conversores de tipo, extensões de marcação e serializadores de valor, mas não para formulários personalizados de conversão de valor. Se você quiser criar conversores de valor personalizado, use o <xref:System.Xaml.Schema.XamlValueConverter%601> tipo.  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>Conversores de tipo e extensões de marcação em combinação  
 As extensões de marcação e os conversores de tipo são usados para situações diferentes em XAML. Embora o contexto esteja disponível para usos de extensão de marcação, o comportamento de conversão de tipos de propriedades em que uma extensão de marcação fornece um valor geralmente não é verificado em implementações de extensão de marcação. Em outras palavras, mesmo se uma extensão de marcação retornar uma cadeia de caracteres `ProvideValue` de texto como sua saída, o comportamento de conversão de tipo nessa cadeia de caracteres, conforme aplicado a uma propriedade específica ou tipo de valor de propriedade, não será invocado. Em geral, a finalidade de uma extensão de marcação é processar uma cadeia de caracteres e retornar um objeto sem qualquer conversor de tipo envolvido.  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>Contexto de serviço para um conversor de valor  
 Quando você implementa um conversor de valor, geralmente precisa de acesso a um contexto no qual o conversor de valor é aplicado. Esse contexto é conhecido como contexto de serviço. O contexto de serviço pode incluir informações como o contexto de esquema XAML ativo, acesso ao sistema de mapeamento de tipos que o contexto de esquema XAML e o gravador de objeto XAML fornecem, e assim por diante. Para obter mais informações sobre os contextos de serviço disponíveis para um conversor de valor e como acessar os serviços que um contexto de serviço pode fornecer, consulte contextos de [serviço disponíveis para conversores de tipo e extensões de marcação](service-contexts-available-to-type-converters-and-markup-extensions.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Visão geral das extensões de marcação para XAML](markup-extensions-for-xaml-overview.md)
- [Visão geral de conversores de tipo para XAML](type-converters-for-xaml-overview.md)
- [Contextos de serviço disponíveis para conversores de tipo e extensões de marcação](service-contexts-available-to-type-converters-and-markup-extensions.md)
