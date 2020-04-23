---
title: Visão geral de conversores de tipo para XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: c3c69aebacd140a14e74545d601c0207cb8de681
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071629"
---
# <a name="overview-of-type-converters-for-xaml"></a>Visão geral dos conversores de tipo para XAML

Conversão de tipo fornece lógica para um escritor de objetos que se converte de uma seqüência de string na marcação XAML em objetos específicos em um gráfico de objetos. Em Serviços XAML .NET, o conversor de <xref:System.ComponentModel.TypeConverter>tipo deve ser uma classe derivada de . Alguns conversores também suportam o caminho de salvamento XAML e podem ser usados para serializar um objeto em uma forma de string na marcação de serialização. Este tópico descreve como e quando os conversores de tipo em XAML <xref:System.ComponentModel.TypeConverter>são invocados e fornece conselhos de implementação para as substituições do método de .

## <a name="type-conversion-concepts"></a>Conceitos de conversão de tipos

As seções a seguir explicam conceitos básicos sobre como o XAML usa strings e como os escritores de objetos no .NET XAML Services usam conversores de tipo para processar alguns dos valores de seqüência encontrados em uma fonte XAML.

### <a name="xaml-and-string-values"></a>XAML e valores de cadeia de caracteres

Quando você define um valor de atributo em um arquivo XAML, o tipo inicial desse valor é uma string em um sentido geral, e um valor de atributo de seqüência em um sentido XML. Mesmo outros primitivos, como <xref:System.Double> são inicialmente strings para um processador XAML.

Na maioria dos casos, um processador XAML precisa de duas informações para processar um valor de atributo. A primeira informação é o tipo de valor da propriedade que está sendo definido. Qualquer cadeia de caracteres que define um valor de atributo e que é processada em XAML deve, por fim, ser convertida ou resolvida para um valor desse tipo. Caso o valor seja um primitivo compreendido pelo analisador XAML (como um valor numérico), será tentada uma conversão direta da cadeia de caracteres. Se o valor do atributo fizer referência a uma enumeração, a seqüência fornecida será verificada para uma correspondência de nome com uma constante nomeada nessa enumeração. Se o valor não for um primitivo compreendido por analisador ou um nome constante de uma enumeração, o tipo aplicável deve ser capaz de fornecer um valor ou referência que seja baseado em uma seqüência de string convertida.

> [!NOTE]
> As diretivas de linguagem XAML não usam conversores de tipo.

### <a name="type-converters-and-markup-extensions"></a>Conversores de tipo e extensões de marcação

Os usos de extensão de marcação devem ser tratados por um processador XAML antes de verificar o tipo de propriedade e outras considerações. Por exemplo, se uma propriedade sendo definida como um atributo normalmente tiver uma conversão de tipo, mas em um caso específico é definida por um uso de extensão de marcação, então o comportamento de extensão de marcação é primeiro. Uma situação comum em que uma extensão de marcação é necessária é fazer uma referência a um objeto que já existe. Para este cenário, um conversor de tipo apátrida só pode gerar uma nova instância, o que pode não ser desejável. Para obter mais informações sobre extensões de marcação, consulte [Extensões de marcação para visão geral XAML](markup-extensions-overview.md).

### <a name="native-type-converters"></a>Conversores de tipos nativos

Nas implementações de serviços Do Windows Presentation Foundation (WPF) e .NET XAML, existem certos tipos de CLR que têm tratamento de conversão de tipo nativo. No entanto, esses tipos de CLR não são convencionalmente considerados primitivos. Um exemplo desse tipo <xref:System.DateTime>é . Uma das razões para isso é como <xref:System.DateTime> funciona a arquitetura .NET Framework: o tipo é definido em mscorlib, a biblioteca mais básica do .NET. <xref:System.DateTime>não é permitido ser atribuído com um atributo que vem de<xref:System.ComponentModel.TypeConverterAttribute> outra montagem que introduz uma dependência (é de System). Portanto, o mecanismo usual de detecção do conversor de tipo atribuindo não pode ser suportado. Em vez disso, o analisador XAML tem uma lista de tipos que precisam de processamento nativo, e processa esses tipos semelhantes à forma como os verdadeiros primitivos são processados. No caso <xref:System.DateTime>de , este processamento <xref:System.DateTime.Parse%2A>envolve uma chamada para .

## <a name="implementing-a-type-converter"></a>Implementando um conversor de tipos

As seções a seguir discutem <xref:System.ComponentModel.TypeConverter> a API da classe.

### <a name="typeconverter"></a>TypeConverter

Em Serviços .NET XAML, todos os conversores de tipo usados <xref:System.ComponentModel.TypeConverter>para fins XAML são classes que derivam da classe base . A <xref:System.ComponentModel.TypeConverter> classe existia em versões do .NET Framework antes da xaml existir; um dos <xref:System.ComponentModel.TypeConverter> cenários originais era fornecer conversão de cordas para editores de propriedades em designers visuais.

Para XAML, o <xref:System.ComponentModel.TypeConverter> papel de é expandido. Para fins XAML, <xref:System.ComponentModel.TypeConverter> é a classe base para fornecer suporte para certas conversões de seqüência e de string. A seqüência de string permite analisar um valor de atributo de seqüência de xaml. A seqüência de reinicialização pode permitir o processamento de um valor de tempo de execução de uma propriedade de objeto específico de volta a um atributo em XAML para serialização.

<xref:System.ComponentModel.TypeConverter>define quatro membros relevantes para converter em string e de string para fins de processamento XAML:

- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>

- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>

- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>

- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>

Desses membros, o método <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>mais importante é , que converte a seqüência de entrada para o tipo de objeto necessário. O <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> método pode ser implementado para converter uma gama mais ampla de tipos no tipo de destino pretendido do conversor. Portanto, ele pode servir para propósitos que se estendem além do XAML, como o suporte a conversões de tempo de execução. No entanto, para o uso do XAML, apenas o caminho de código que pode processar uma <xref:System.String> entrada é importante.

O segundo método mais <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>importante é. Se um aplicativo for convertido em uma representação de marcação (por exemplo, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> se ele for salvo em XAML como um arquivo), ele está envolvido no cenário maior de um escritor de texto XAML para produzir uma representação de marcação. Neste caso, o caminho de código importante para XAML é quando o chamador passa a `destinationType` de <xref:System.String>.

<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>e <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> são métodos de suporte que são usados <xref:System.ComponentModel.TypeConverter> quando um serviço consulta os recursos da implementação. Esses métodos devem ser implementados para retornar o `true` para casos específicos de tipo aos quais os métodos de conversão equivalentes do seu conversor dão suporte. Para fins XAML, isso <xref:System.String> geralmente significa o tipo.

### <a name="culture-information-and-type-converters-for-xaml"></a>Informações de cultura e conversores de tipos para XAML

Cada <xref:System.ComponentModel.TypeConverter> implementação pode interpretar exclusivamente o que é uma seqüência válida para uma conversão, e também pode usar ou ignorar a descrição do tipo que é passada como parâmetros. Uma consideração importante para a cultura e a conversão do tipo XAML é a seguinte: embora o uso de strings localizadas como valores de atributo seja suportado por XAML, você não pode usar essas strings localizadas como entrada de conversor de tipo com requisitos específicos de cultura. Essa limitação é porque os conversores de tipo para valores de atributo `en-US` XAML envolvem um comportamento de processamento XAML de linguagem fixa que usa cultura. Para obter mais informações sobre as razões de design para essa restrição, consulte a especificação do idioma XAML[\[(MS-XAML)\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))ou [a visão geral da Globalização e Localização do WPF.](../../framework/wpf/advanced/wpf-globalization-and-localization-overview.md)

Como exemplo, onde a cultura pode ser um problema, algumas culturas usam uma comma em vez de um período como o delimitador de ponto decimal para números em forma de string. Este uso colide com o comportamento que muitos conversores de tipo existentes têm, que é usar uma comma como um delimitador. Passar uma `xml:lang` cultura no entorno da XAML não resolve o problema.

### <a name="implementing-convertfrom"></a>Implementando ConvertFrom

Para ser utilizável <xref:System.ComponentModel.TypeConverter> como uma implementação que <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> suporta XAML, o `value` método para esse conversor deve aceitar uma string como parâmetro. Se a seqüência estiver em um formato <xref:System.ComponentModel.TypeConverter> válido e puder ser convertida pela implementação, o objeto retornado deve suportar um elenco para o tipo esperado pela propriedade. Caso contrário, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> a `null`implementação deve retornar .

Cada <xref:System.ComponentModel.TypeConverter> implementação pode interpretar exclusivamente o que constitui uma seqüência válida para uma conversão, e também pode usar ou ignorar a descrição do tipo ou contextos de cultura que são passados como parâmetros. No entanto, o processamento Do WPF XAML pode não passar valores para `xml:lang`o contexto de descrição do tipo em todos os casos e também pode não passar cultura com base em .

> [!NOTE]
> Não use as chaves{}(), especificamente a chave de abertura ({), como um elemento do seu formato de corda. Esses caracteres são reservados como entrada e saída para uma sequência de extensão de marcação.

É apropriado abrir uma exceção quando o conversor de tipo deve ter acesso a um <xref:System.IServiceProvider.GetService%2A> serviço XAML do escritor de objetos .NET XAML Services, mas a chamada que é feita contra o contexto não retorna esse serviço.

### <a name="implementing-convertto"></a>Implementando ConvertTo

<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>é potencialmente usado para suporte à serialização. O suporte <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> à serialização para o seu tipo personalizado e seu conversor de tipo não é um requisito absoluto. No entanto, se você estiver implementando um controle, ou usando serialização de <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>como parte dos recursos ou design de sua classe, você deve implementar .

Para ser utilizável <xref:System.ComponentModel.TypeConverter> como uma implementação que <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> suporta XAML, o método para esse conversor deve aceitar `value` uma instância do tipo (ou um valor) que é suportada como parâmetro. Quando `destinationType` o parâmetro for <xref:System.String>do tipo, o objeto retornado <xref:System.String>deve ser capaz de ser lançado como . A cadeia de caracteres retornada deve representar um valor serializado de `value`. Idealmente, o formato de serialização que você escolher deve ser capaz de <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> gerar o mesmo valor que se essa string fosse passada para a implementação do mesmo conversor, sem perda significativa de informação.

Se o valor não puder ser serializado ou <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> o conversor não suportar serialização, a implementação deve retornar `null` e pode abrir uma exceção. No entanto, se você lançar exceções, você deve relatar a <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> incapacidade de usar essa conversão <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> como parte de sua implementação para que a melhor prática de verificar com primeiro para evitar exceções seja suportada.

Se `destinationType` o parâmetro não <xref:System.String>for do tipo, você pode escolher o seu próprio manuseio do conversor. Normalmente, você reverte para o manuseio <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> da implementação base, que na base levanta uma exceção específica.

É apropriado abrir uma exceção quando o conversor de tipo deve ter acesso a um <xref:System.IServiceProvider.GetService%2A> serviço XAML do escritor de objetos .NET XAML Services, mas a chamada que é feita contra o contexto não retorna esse serviço.

### <a name="implementing-canconvertfrom"></a>Implementando CanConvertFrom

Sua <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> implementação `true` `sourceType` deve <xref:System.String> retornar para o tipo e de outra forma, adiar para a implementação base. Não lance exceções de <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.

### <a name="implementing-canconvertto"></a>Implementando CanConvertTo

Sua <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementação `true` `destinationType` deve <xref:System.String>retornar para o tipo e, de outra forma, adiar para a implementação base. Não lance exceções de <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.

## <a name="applying-the-typeconverterattribute"></a>Aplicando o TypeConverterAttribute

Para que seu conversor de tipo personalizado seja usado como conversor de tipo de <xref:System.ComponentModel.TypeConverterAttribute> ação para uma classe personalizada por Serviços XAML .NET, você deve aplicar a definição da sua classe. O <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> que você especifica através do atributo deve ser o nome de tipo do seu conversor de tipo personalizado. Se você aplicar esse atributo, quando um processador XAML lida com valores onde o tipo de propriedade usa seu tipo de classe personalizada, ele pode inserir strings e retornar instâncias de objeto.

Também é possível fornecer um conversor de tipos por propriedade. Em vez de <xref:System.ComponentModel.TypeConverterAttribute> aplicar a à definição de classe, aplique-a `get` / `set` a uma definição de propriedade (a definição principal, não as implementações dentro dela). O tipo da propriedade deve corresponder ao tipo que é processado pelo conversor de tipos personalizado. Com este atributo aplicado, quando um processador XAML lida com valores dessa propriedade, ele pode processar strings de entrada e retornar instâncias de objeto. A técnica de conversor de tipo por propriedade é útil se você optar por usar um tipo de propriedade <xref:System.ComponentModel.TypeConverterAttribute> do Microsoft .NET Framework ou de alguma outra biblioteca onde você não pode controlar a definição de classe e não pode aplicar um lá.

Para fornecer um comportamento de conversão de <xref:System.ComponentModel.TypeConverterAttribute> tipo `Get` para um membro anexado personalizado, aplique-se ao método acessório do padrão de implementação para o membro anexado.

## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Acessando o contexto do provedor de serviços a partir de uma implementação de extensão de marcação

Os serviços disponíveis são os mesmos para qualquer conversor de valor. A diferença está em como cada conversor de valor recebe o contexto do serviço. Os serviços de acesso e os serviços disponíveis estão documentados no tópico [Type Converters e Extensões de Marcação para XAML](type-converters-and-markup-extensions.md).

## <a name="type-converters-in-the-xaml-node-stream"></a>Tipo conversores no fluxo de nó XAML

Se você estiver trabalhando com um fluxo de nó XAML, a ação ou o resultado final de um conversor de tipo ainda não será executado. Em um caminho de carga, a seqüência de atributos que eventualmente precisa ser convertida por tipo para carregar permanece como um valor de texto dentro de um membro inicial e membro final. O conversor de tipo que eventualmente é necessário <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> para esta operação pode ser determinado usando a propriedade. No entanto, obter <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> um valor válido depende de ter um contexto de esquema XAML, que pode acessar tais informações através do membro subjacente, ou o tipo do valor do objeto que o membro usa. Invocar o comportamento de conversão de tipo também requer o contexto do esquema XAML porque isso requer mapeamento de tipo e criação de uma instância de conversor.

## <a name="see-also"></a>Confira também

- <xref:System.ComponentModel.TypeConverterAttribute>
- [Conversores de tipo e extensões de marcação para XAML](type-converters-and-markup-extensions.md)
- [Visão geral de XAML (WPF)](../fundamentals/xaml.md)
