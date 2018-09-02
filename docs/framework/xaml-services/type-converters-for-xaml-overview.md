---
title: Visão geral de conversores de tipo para XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: 25705b573be74ea5a2d71537b0c165a6f619d1d9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399577"
---
# <a name="type-converters-for-xaml-overview"></a>Visão geral de conversores de tipo para XAML
Lógica de fornecimento de conversores de tipo para um gravador de objeto que converte uma cadeia de caracteres na marcação XAML em objetos específicos em um grafo de objeto. Nos serviços de XAML do .NET Framework, o conversor de tipo deve ser uma classe que deriva de <xref:System.ComponentModel.TypeConverter>. Além disso, alguns conversores dão suporte a XAML caminho de salvamento e podem ser usados para serializar um objeto em um formulário de cadeia de caracteres na marcação de serialização. Este tópico descreve como e quando são invocados conversores de tipo em XAML e fornece conselhos de implementação para o método substituições de <xref:System.ComponentModel.TypeConverter>.  
  
<a name="type_conversion_concepts"></a>   
## <a name="type-conversion-concepts"></a>Conceitos de conversão de tipos  
 As seções a seguir explicam os conceitos básicos sobre como o XAML usa cadeias de caracteres e, como gravadores de objeto em serviços de XAML do .NET Framework usam conversores de tipo para processar alguns dos valores de cadeia de caracteres que são encontrados em uma fonte XAML.  
  
### <a name="xaml-and-string-values"></a>XAML e valores de cadeia de caracteres  
 Quando você define um valor de atributo em um arquivo XAML, o tipo inicial desse valor é uma cadeia de caracteres em um sentido geral e um valor de atributo de cadeia de caracteres em um sentido XML. Até mesmo outros primitivos, como <xref:System.Double> inicialmente são cadeias de caracteres para um processador XAML.  
  
 Na maioria dos casos, um processador XAML precisa de duas informações para processar um valor de atributo. A primeira informação é o tipo de valor da propriedade que está sendo definido. Qualquer cadeia de caracteres que define um valor de atributo e que é processada em XAML deve, por fim, ser convertida ou resolvida para um valor desse tipo. Caso o valor seja um primitivo compreendido pelo analisador XAML (como um valor numérico), será tentada uma conversão direta da cadeia de caracteres. Se o valor para o atributo faz referência a uma enumeração, a cadeia de caracteres fornecida é verificada para uma correspondência de nome para uma constante nomeada na enumeração. Se o valor não é um primitivo compreendido pelo analisador nem um nome de constante de uma enumeração, o tipo aplicável deve ser capaz de fornecer um valor ou referência se baseia em uma cadeia de caracteres convertida.  
  
> [!NOTE]
>  Diretivas de linguagem XAML não usa conversores de tipo.  
  
### <a name="type-converters-and-markup-extensions"></a>Conversores de tipo e extensões de marcação  
 Usos de extensão de marcação devem ser tratados por um processador XAML antes de verificar o tipo de propriedade e outras considerações. Por exemplo, se uma propriedade que está sendo definida como um atributo normalmente tem uma conversão de tipo, mas um caso específico é definida por um uso de extensão de marcação, em seguida, o comportamento de extensão de marcação processa pela primeira vez. É uma situação comum em que uma extensão de marcação é necessária fazer uma referência a um objeto que já existe. Para este cenário, um conversor de tipo sem monitoração de estado só pode gerar uma nova instância, que pode não ser desejável. Para obter mais informações sobre extensões de marcação, consulte [extensões de marcação para visão geral de XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### <a name="native-type-converters"></a>Conversores de tipos nativos  
 As implementações de serviços do WPF e XAML do .NET, há determinados tipos CLR que têm manipulação de conversão de tipo nativo, no entanto, esses tipos CLR não são convencionalmente pensados como primitivos. Um exemplo desse tipo é <xref:System.DateTime>. Um motivo para isso é como a arquitetura do .NET Framework funciona: o tipo <xref:System.DateTime> é definido em mscorlib, a biblioteca mais básica no .NET. <xref:System.DateTime> não é permitida para ser atribuído com um atributo que vem de outro assembly que introduz uma dependência (<xref:System.ComponentModel.TypeConverterAttribute> é do sistema); portanto, o mecanismo de descoberta de conversor de tipos usual por atribuição não têm suporte. Em vez disso, o analisador XAML tem uma lista de tipos que precisam de processamento nativo e processa esses tipos semelhantes a como os primitivos verdadeiros são processados. No caso de <xref:System.DateTime>, esse processamento envolve uma chamada para <xref:System.DateTime.Parse%2A>.  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementando um conversor de tipos  
 As seções a seguir discutem a API da <xref:System.ComponentModel.TypeConverter> classe.  
  
### <a name="typeconverter"></a>TypeConverter  
 Em serviços de XAML do .NET Framework, todos os conversores de tipo que são usados para fins XAML são classes que derivam da classe base <xref:System.ComponentModel.TypeConverter>. O <xref:System.ComponentModel.TypeConverter> classe existia em versões do .NET Framework antes de que existiu XAML; um dos original <xref:System.ComponentModel.TypeConverter> cenários era fornecer conversão de cadeia de caracteres para os editores de propriedade em designers visuais.  
  
 Para XAML, a função de <xref:System.ComponentModel.TypeConverter> é expandido. Para fins XAML, <xref:System.ComponentModel.TypeConverter> é a classe base para fornecer suporte para a cadeia de caracteres e de cadeia de caracteres conversões certas. De cadeia de caracteres permite a análise de um valor de atributo de cadeia de caracteres de XAML. A cadeia de caracteres pode permitir que um valor de tempo de execução de uma propriedade de objeto específico de processamento volta para um atributo em XAML para serialização.  
  
 <xref:System.ComponentModel.TypeConverter> define quatro membros que são relevantes para converter a cadeia de caracteres e de cadeia de caracteres para fins de processamento de XAML:  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Esses membros, o método mais importante é <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>, que converte a cadeia de caracteres de entrada para o tipo de objeto necessário. O <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> método pode ser implementado para converter uma maior variedade de tipos para o tipo de destino pretendido do conversor. Portanto, ele pode servir finalidades que vão além do XAML, como oferecer suporte a conversões de tempo de execução. No entanto, para uso em XAML, apenas o caminho do código que pode processar um <xref:System.String> entrada é importante.  
  
 O método segundo o mais importante é <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Se um aplicativo é convertido em uma representação de marcação (por exemplo, se ele é salvo em XAML como um arquivo), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> está envolvido no cenário maior de uma produção de gravadores de texto uma representação de marcação XAML. Nesse caso, o caminho de código importantes para o XAML é quando o chamador passa uma `destinationType` de <xref:System.String>.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> e <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> são os métodos de suporte que são usados quando um serviço consulta as capacidades do <xref:System.ComponentModel.TypeConverter> implementação. Esses métodos devem ser implementados para retornar o `true` para casos específicos de tipo aos quais os métodos de conversão equivalentes do seu conversor dão suporte. Para fins XAML, isso geralmente significa o <xref:System.String> tipo.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informações de cultura e conversores de tipos para XAML  
 Cada <xref:System.ComponentModel.TypeConverter> implementação exclusivamente pode interpretar o que é uma cadeia de caracteres válida para uma conversão e também pode usar ou ignorar a descrição do tipo que é passada como parâmetros. Uma consideração importante para a conversão de tipo de cultura e o XAML é o seguinte: Embora usar cadeias de caracteres localizáveis como valores de atributo for compatível com XAML, é possível usar essas cadeias de caracteres localizáveis como entrada do conversor de tipo com exigências específicas de cultura. Essa limitação existe porque os conversores de tipo para valores de atributo XAML envolvem um comportamento de processamento de XAML de linguagem necessariamente fixo usa `en-US` cultura. Para obter mais informações sobre os motivos de design para essa restrição, consulte a especificação da linguagem XAML ([\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)) ou [VisãogeraldelocalizaçãoeglobalizaçãodoWPF](../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
 Como um exemplo em que a cultura pode ser um problema, algumas culturas usam vírgula em vez de um período como o delimitador de vírgula decimal para números em formato de cadeia de caracteres. Esse uso entra em conflito com o comportamento que têm muitos conversores de tipo existente, que é usar uma vírgula como delimitador. Passando uma cultura por meio de `xml:lang` no XAML ao redor não resolver o problema.  
  
### <a name="implementing-convertfrom"></a>Implementando ConvertFrom  
 Para ser usado como um <xref:System.ComponentModel.TypeConverter> implementação que dá suporte a XAML, o <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> método para tal conversor deve aceitar uma cadeia de caracteres como o `value` parâmetro. Se a cadeia de caracteres está em um formato válido e pode ser convertida pelo <xref:System.ComponentModel.TypeConverter> implementação, o objeto retornado deve dar suporte a uma conversão para o tipo esperado pela propriedade. Caso contrário, o <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementação deve retornar `null`.  
  
 Cada <xref:System.ComponentModel.TypeConverter> implementação exclusivamente pode interpretar o que constitui uma cadeia de caracteres válida para uma conversão e também pode usar ou ignorar os contextos de cultura ou a descrição de tipo que são passados como parâmetros. No entanto, o XAML WPF de processamento não pode passar valores para o contexto de descrição de tipo em todos os casos e também pode passar a cultura com base em `xml:lang`.  
  
> [!NOTE]
>  Não use as chaves ({}), especificamente a chave de abertura ({), como um elemento de seu formato de cadeia de caracteres. Esses caracteres são reservados como entrada e saída para uma sequência de extensão de marcação.  
  
 Ele é apropriado lançar uma exceção quando seu conversor de tipo deve ter acesso a um serviço XAML do gravador de objeto de serviços de XAML do .NET Framework, mas o <xref:System.IServiceProvider.GetService%2A> chamada é feita no contexto desse serviço não retorna.  
  
### <a name="implementing-convertto"></a>Implementando ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> potencialmente é usado para suporte à serialização. Suporte de serialização por meio de <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> para seu tipo personalizado e seu tipo de conversor não é um requisito absoluto. No entanto, se você estiver implementando um controle ou usando a serialização como parte dos recursos ou o design da sua classe, você deve implementar <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Para ser usado como um <xref:System.ComponentModel.TypeConverter> implementação que dá suporte a XAML, o <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> método para tal conversor deve aceitar uma instância do tipo (ou um valor) que tem suporte como o `value` parâmetro. Quando o `destinationType` parâmetro é do tipo <xref:System.String>, o objeto retornado deve ser capaz de ser convertido como <xref:System.String>. A cadeia de caracteres retornada deve representar um valor serializado de `value`. O ideal é que o formato de serialização que você escolher deve ser capaz de gerar o mesmo valor como se essa cadeia de caracteres foi passada para o <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementação do mesmo conversor, sem perda significativa de informações.  
  
 Se o valor não pode ser serializado ou se o conversor não oferece suporte a serialização, o <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> implementação deve retornar `null` e pode lançar uma exceção. No entanto, se você lançar exceções, reporte a incapacidade de usar a conversão como parte de sua <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementação, de modo que a prática recomendada de verificar com o <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> primeiro evitar exceções é suportado.  
  
 Se o `destinationType` parâmetro não é do tipo <xref:System.String>, você pode escolher sua própria manipulação de conversor. Normalmente, você reverter para implementação de base de tratamento, que, na base de <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> gera uma exceção específica.  
  
 Ele é apropriado lançar uma exceção quando seu conversor de tipo deve ter acesso a um serviço XAML do gravador de objeto de serviços de XAML do .NET Framework, mas o <xref:System.IServiceProvider.GetService%2A> chamada é feita no contexto desse serviço não retorna.  
  
### <a name="implementing-canconvertfrom"></a>Implementando CanConvertFrom  
 Sua <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> implementação deve retornar `true` para `sourceType` do tipo <xref:System.String> caso contrário, adie até a implementação base. Não lance exceções de <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.  
  
### <a name="implementing-canconvertto"></a>Implementando CanConvertTo  
 Sua <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementação deve retornar `true` para `destinationType` do tipo <xref:System.String>, caso contrário, adie até a implementação base. Não lance exceções de <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Aplicando o TypeConverterAttribute  
 Para o conversor de tipo personalizado a ser usado como atuando conversor de tipo para uma classe personalizada por serviços XAML do .NET Framework, você deve aplicar a [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> à sua definição de classe. O <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> que você especifique por meio do atributo deve ser o nome do tipo de conversor de tipos personalizado. Se você aplicar esse atributo, quando um processador XAML manipula valores em que o tipo de propriedade usa o tipo de classe personalizada, ele pode cadeias de caracteres de entrada e retornar as instâncias de objeto.  
  
 Também é possível fornecer um conversor de tipos por propriedade. Em vez de aplicar uma [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> à definição de classe, aplicá-la a uma definição de propriedade (a definição principal, não a `get` / `set` implementações dentro dele). O tipo da propriedade deve corresponder ao tipo que é processado pelo conversor de tipos personalizado. Com esse atributo aplicado, quando um processador XAML manipula valores dessa propriedade, ele pode processar cadeias de caracteres de entrada e retornar as instâncias de objeto. A técnica de conversor de tipo por propriedade é particularmente útil se você optar por usar um tipo de propriedade do Microsoft .NET Framework ou de alguma outra biblioteca em que você não pode controlar a definição de classe e não é possível aplicar um <xref:System.ComponentModel.TypeConverterAttribute> lá.  
  
 Para fornecer um comportamento de conversão de tipo de membro anexado personalizado, aplique <xref:System.ComponentModel.TypeConverterAttribute> para o `Get` método do acessador do padrão de implementação para o membro anexado.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Acessando o contexto de provedor de serviço de uma implementação de extensão de marcação  
 Os serviços disponíveis são as mesmas para qualquer conversor de valor. A diferença está em como cada conversor de valor recebe o contexto de serviço. Acesso a serviços e os serviços disponíveis estão documentados no tópico [conversores de tipo e extensões de marcação para XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="type_converters_in_the_xaml_node_stream"></a>   
## <a name="type-converters-in-the-xaml-node-stream"></a>Conversores de tipo em que o Stream de nó XAML  
 Se você estiver trabalhando com um fluxo do nó XAML, o resultado final de um conversor de tipo ou a ação não será executado ainda. Em um caminho de carga, a cadeia de caracteres de atributo que, eventualmente, precisa ser convertido para a carga permanece como um valor de texto dentro de um membro inicial e final. O conversor de tipo que, eventualmente, é necessário para esta operação pode ser determinada usando o <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> propriedade. No entanto, como obter um valor válido de <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> se baseia em ter um contexto de esquema XAML, que pode acessar essas informações por meio de membro subjacente ou o tipo do valor do objeto que usa o membro. Invocar o comportamento de conversão de tipo também requer o contexto do esquema XAML porque que requer o mapeamento de tipo e criar uma instância do conversor.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 [Conversores de tipo e extensões de marcação para XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [Visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
