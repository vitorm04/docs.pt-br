---
title: TypeConverters e XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 94cfce44d5702e0550310723ec56184096165436
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187294"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters e XAML
Este tópico apresenta a finalidade da conversão de tipo de cadeia de caracteres como um recurso de linguagem XAML geral. No .NET Framework, <xref:System.ComponentModel.TypeConverter> a classe serve a um propósito específico como parte da implementação de uma classe personalizada gerenciada que pode ser usada como um valor de propriedade no uso de atributoXAML. Se você escrever uma classe personalizada e quiser que as instâncias da sua classe sejam utilizáveis <xref:System.ComponentModel.TypeConverterAttribute> como valores de <xref:System.ComponentModel.TypeConverter> atributo seletos XAML, talvez seja necessário aplicar um à sua classe, escrever uma classe personalizada ou ambos.  

## <a name="type-conversion-concepts"></a>Conceitos de conversão de tipos  
  
### <a name="xaml-and-string-values"></a>XAML e valores de cadeia de caracteres  
 Quando um valor de atributo é definido em um arquivo XAML, o tipo inicial desse valor é uma cadeia de caracteres em texto simples. Mesmo outros primitivos, como <xref:System.Double> são inicialmente seqüências de texto para um processador XAML.  
  
 Um processador XAML precisa de duas informações para processar um valor de atributo. A primeira informação é o tipo de valor da propriedade que está sendo definido. Qualquer cadeia de caracteres que define um valor de atributo e que é processada em XAML deve, por fim, ser convertida ou resolvida para um valor desse tipo. Caso o valor seja um primitivo compreendido pelo analisador XAML (como um valor numérico), será tentada uma conversão direta da cadeia de caracteres. Se o valor for uma enumeração, a cadeia de caracteres será usada para verificar se há uma correspondência de nome com uma constante nomeada na enumeração. Se o valor não for um primitivo compreendido pelo analisador nem uma enumeração, o tipo em questão deverá ser capaz de fornecer uma instância do tipo ou um valor, com base em uma cadeia de caracteres convertida. Isso é feito por meio de indicação de uma classe de conversor de tipos. O conversor de tipos é uma classe auxiliar para fornecer valores de outra classe, tanto para o cenário XAML quanto, potencialmente, para chamadas de código no código .NET.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Usando o comportamento de conversão de tipo existente em XAML  
 Dependendo da sua familiaridade com os conceitos fundamentais de XAML, você pode já estar usando o comportamento de conversão de tipos no aplicativo básico XAML sem perceber. Por exemplo, o WPF define literalmente centenas de <xref:System.Windows.Point>propriedades que tomam um valor de tipo . A <xref:System.Windows.Point> é um valor que descreve uma coordenada em um espaço de coordenadas <xref:System.Windows.Point.X%2A> <xref:System.Windows.Point.Y%2A>bidimensional, e ele realmente só tem duas propriedades importantes: e . Quando você especifica um ponto em XAML, você o especifica como uma string com <xref:System.Windows.Point.X%2A> um <xref:System.Windows.Point.Y%2A> delimitador (tipicamente uma comuma) entre os valores fornecidos. Por exemplo: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`.  
  
 Mesmo este tipo <xref:System.Windows.Point> simples de e seu uso simples em XAML envolvem um conversor de tipo. Neste caso, essa <xref:System.Windows.PointConverter>é a classe.  
  
 O conversor <xref:System.Windows.Point> de tipo para definido no nível de classe <xref:System.Windows.Point>simplifica os usos de marcação de todas as propriedades que tomam . Sem um conversor de tipos aqui, você precisaria da marcação muito mais detalhada a seguir para o mesmo exemplo mostrado anteriormente:  

```xaml
<LinearGradientBrush>
  <LinearGradientBrush.StartPoint>
    <Point X="0" Y="0"/>
  </LinearGradientBrush.StartPoint>
  <LinearGradientBrush.EndPoint>
    <Point X="1" Y="1"/>
  </LinearGradientBrush.EndPoint>
</LinearGradientBrush>
 ```
  
 Usar a cadeia de caracteres de conversão de tipo ou uma sintaxe equivalente mais detalhada geralmente é uma opção de estilo de codificação. O fluxo de trabalho das ferramentas XAML também pode influenciar a forma como os valores são definidos. Algumas ferramentas XAML tendem a emitir a forma mais detalhada da marcação, porque é mais fácil ir e voltar de modos de exibição de designer ou do próprio mecanismo de serialização.  
  
 Os conversores de tipo existentes geralmente podem ser descobertos nos tipos WPF e .NET Framework <xref:System.ComponentModel.TypeConverterAttribute>verificando uma classe (ou propriedade) para a presença de uma aplicação . Esse atributo nomeará a classe que é o conversor de tipos de suporte para valores desse tipo, para fins de XAML e, potencialmente, outras finalidades.  
  
### <a name="type-converters-and-markup-extensions"></a>Conversores de tipo e extensões de marcação  
 As extensões de marcação e os conversores de tipos exercem funções ortogonais em termos de comportamento do processador XAML e dos cenários aos quais são aplicados. Embora o contexto esteja disponível para usos de extensão de marcação, o comportamento de conversão de tipos de propriedades em que uma extensão de marcação fornece um valor geralmente não é verificado em implementações de extensão de marcação. Em outras palavras, mesmo se uma extensão de marcação retornar uma cadeia de caracteres de texto como saída do `ProvideValue`, o comportamento de conversão de tipo dessa cadeia de caracteres, conforme aplicado a uma propriedade específica ou a um tipo de valor da propriedade, não será chamado. Em geral, a finalidade de uma extensão de marcação é processar uma cadeia de caracteres e retornar um objeto sem nenhum conversor de tipo envolvido.  
  
 Uma situação comum em que uma extensão de marcação é necessária, em vez de um conversor de tipos, é para fazer referência a um objeto que já existe. Na melhor das hipóteses, um conversor de tipo sem monitoração de estado pode gerar somente uma nova instância, o que pode não ser desejável. Para obter mais informações sobre extensões de marcação, consulte [Extensões de marcação e XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Conversores de tipos nativos  
 Na implementação do analisador XAML do WPF e do .NET Framework, alguns tipos têm manipulação de conversão de tipos nativos; porém, não são tipos que poderiam ser interpretados, convencionalmente, como primitivos. Um exemplo desse tipo <xref:System.DateTime>é . A razão para isso é baseada em como a <xref:System.DateTime> arquitetura .NET Framework funciona: o tipo é definido em mscorlib, a biblioteca mais básica em .NET. <xref:System.DateTime>não é permitido ser atribuído com um atributo que vem de<xref:System.ComponentModel.TypeConverterAttribute> outro conjunto que introduz uma dependência (é do Sistema) de modo que o mecanismo usual de descoberta do conversor do tipo atribuindo não pode ser suportado. Em vez disso, o analisador XAML tem uma lista de tipos que precisam de tal processamento nativo e os processa da mesma forma como os primitivos verdadeiros são processados. (No caso <xref:System.DateTime> disso, envolve <xref:System.DateTime.Parse%2A>uma chamada para .)  
  
<a name="Implementing_a_Type_Converter"></a>
## <a name="implementing-a-type-converter"></a>Implementando um conversor de tipos  
  
### <a name="typeconverter"></a>TypeConverter  
 No <xref:System.Windows.Point> exemplo dado anteriormente, a classe <xref:System.Windows.PointConverter> foi mencionada. Para implementações .NET de XAML, todos os conversores de tipo usados <xref:System.ComponentModel.TypeConverter>para fins XAML são classes que derivam da classe base . A <xref:System.ComponentModel.TypeConverter> classe existia em versões do .NET Framework que precedem a existência de XAML; um de seus usos originais foi fornecer conversão de strings para diálogos de propriedade em designers visuais. Para XAML, o <xref:System.ComponentModel.TypeConverter> papel de é expandido para incluir ser a classe base para conversões de cadeia e de seqüência que permitem analisar um valor de atributo de seqüência e, possivelmente, processar um valor de tempo de execução de uma propriedade de objeto específico de volta em uma seqüência para serialização como um atributo.  
  
 <xref:System.ComponentModel.TypeConverter>define quatro membros relevantes para converter e de strings para fins de processamento XAML:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Destes, o método <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>mais importante é . Esse método converte a cadeia de caracteres de entrada para o tipo de objeto necessário. Estritamente falando, o <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> método poderia ser implementado para converter uma gama muito mais ampla de tipos no tipo de destino pretendido do conversor, e assim servir para propósitos <xref:System.String> que se estendem além do XAML, como suportar conversões de tempo de execução, mas para fins XAML é apenas o caminho de código que pode processar uma entrada que importa.  
  
 O próximo método <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>mais importante é. Se um aplicativo for convertido em uma representação de marcação (por exemplo, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> se ele for salvo em XAML como um arquivo), será responsável por produzir uma representação de marcação. Neste caso, o caminho de código que importa para `destinationType` <xref:System.String> XAML é quando você passa a de .  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>e <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> são métodos de suporte que são usados <xref:System.ComponentModel.TypeConverter> quando um serviço consulta os recursos da implementação. Esses métodos devem ser implementados para retornar o `true` para casos específicos de tipo aos quais os métodos de conversão equivalentes do seu conversor dão suporte. Para fins XAML, isso <xref:System.String> geralmente significa o tipo.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informações de cultura e conversores de tipos para XAML  

 Cada <xref:System.ComponentModel.TypeConverter> implementação pode ter sua própria interpretação do que constitui uma seqüência válida para uma conversão, e também pode usar ou ignorar a descrição do tipo passada como parâmetros. Há uma consideração importante em relação à cultura e à conversão de tipos XAML. O XAML dá suporte total ao uso de cadeias de caracteres localizáveis como valores de atributos. Porém, não há suporte para o uso dessa cadeia de caracteres localizável como entrada do conversor de tipos com exigências específicas de cultura, porque os conversores de tipos para valores de atributos XAML envolvem um comportamento de análise de linguagem necessariamente fixo, usando a cultura do `en-US`. Para obter mais informações sobre as razões do design para essa restrição, você deve consultar a especificação do idioma XAML ([\[MS-XAML\]](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf).  
  
 Como exemplo de casos em que a cultura pode ser um problema, algumas culturas usam vírgula como delimitador de ponto decimal para números. Isso vai de encontro ao comportamento que muitos dos conversores de tipos XAML do WPF têm, que é usar uma vírgula como delimitador (com base em precedentes históricos, como a forma comum X,Y ou listas delimitadas por vírgulas). Nem mesmo a passagem de uma cultura no XAML ao redor (definindo `Language` ou `xml:lang` para a cultura do `sl-SI`, um exemplo de cultura que usa vírgula para decimal dessa maneira) resolve o problema.  
  
### <a name="implementing-convertfrom"></a>Implementando ConvertFrom  
 Para ser utilizável <xref:System.ComponentModel.TypeConverter> como uma implementação que <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> suporta XAML, o `value` método para esse conversor deve aceitar uma string como parâmetro. Se a seqüência estava em formato válido <xref:System.ComponentModel.TypeConverter> e pode ser convertida pela implementação, então o objeto retornado deve suportar um elenco para o tipo esperado pela propriedade. Caso contrário, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> a `null`implementação deve retornar .  
  
 Cada <xref:System.ComponentModel.TypeConverter> implementação pode ter sua própria interpretação do que constitui uma seqüência válida para uma conversão, e também pode usar ou ignorar a descrição do tipo ou contextos culturais passados como parâmetros. No entanto, o processamento de XAML do WPF não pode passar valores para o contexto de descrição de tipo em todos os casos; tampouco consegue passar a cultura com base no `xml:lang`.  
  
> [!NOTE]
> Não utilize os caracteres de chave, especialmente o {, como elemento possível do formato da cadeia de caracteres. Esses caracteres são reservados como entrada e saída para uma sequência de extensão de marcação.  
  
### <a name="implementing-convertto"></a>Implementando ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>é potencialmente usado para suporte à serialização. O suporte <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> à serialização para o seu tipo personalizado e seu conversor de tipo não é um requisito absoluto. No entanto, se você estiver implementando um controle, ou usando serialização de <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>como parte dos recursos ou design de sua classe, você deve implementar .  
  
 Para ser utilizável <xref:System.ComponentModel.TypeConverter> como uma implementação que <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> suporta XAML, o método para esse conversor deve `value` aceitar uma instância do tipo (ou um valor) sendo suportado como parâmetro. Quando `destinationType` o parâmetro for <xref:System.String>o tipo, então o objeto retornado deve ser capaz de ser lançado como <xref:System.String>. A cadeia de caracteres retornada deve representar um valor serializado de `value`. Idealmente, o formato de serialização que você escolher deve ser capaz <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> de gerar o mesmo valor se essa string for passada para a implementação do mesmo conversor, sem perda significativa de informação.  
  
 Se o valor não puder ser serializado ou o <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> conversor `null`não suportar a serialização, a implementação deve retornar , e é permitido lançar uma exceção neste caso. Mas se você lançar exceções, você deve relatar a incapacidade <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> de usar essa conversão como parte <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> de sua implementação para que a melhor prática de verificar com primeiro para evitar exceções seja suportada.  
  
 Se `destinationType` o parâmetro não <xref:System.String>for do tipo, você pode escolher o seu próprio manuseio do conversor. Normalmente, você reverteria para o manuseio da <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> implementação base, que na maioria das bases levanta uma exceção específica.  
  
### <a name="implementing-canconvertto"></a>Implementando CanConvertTo  
 Sua <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementação `true` `destinationType` deve <xref:System.String>retornar para o tipo e, de outra forma, adiar para a implementação base.  
  
### <a name="implementing-canconvertfrom"></a>Implementando CanConvertFrom  
 Sua <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> implementação `true` `sourceType` deve <xref:System.String>retornar para o tipo e, de outra forma, adiar para a implementação base.  
  
<a name="Applying_the_TypeConverterAttribute"></a>
## <a name="applying-the-typeconverterattribute"></a>Aplicando o TypeConverterAttribute  
 Para que seu conversor de tipo personalizado seja usado como conversor de tipo de <xref:System.ComponentModel.TypeConverterAttribute> ação para uma classe personalizada por um processador XAML, você deve aplicar a definição à sua classe. O <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> que você especifica através do atributo deve ser o nome de tipo do seu conversor de tipo personalizado. Com esse atributo aplicado, quando um processador XAML manipula valores em que o tipo de propriedade usa o tipo de classe personalizada, ele pode processar cadeias de caracteres de entrada e retornar as instâncias de objeto.  
  
 Também é possível fornecer um conversor de tipos por propriedade. Em vez de <xref:System.ComponentModel.TypeConverterAttribute> aplicar a à definição de classe, aplique-a `get` / `set` a uma definição de propriedade (a definição principal, não as implementações dentro dela). O tipo da propriedade deve corresponder ao tipo que é processado pelo conversor de tipos personalizado. Com este atributo aplicado, quando um processador XAML lida com valores dessa propriedade, ele pode processar strings de entrada e retornar instâncias de objeto. A técnica de conversor de tipo por propriedade é particularmente útil se você optar por usar um tipo de <xref:System.ComponentModel.TypeConverterAttribute> propriedade do Microsoft .NET Framework ou de alguma outra biblioteca onde você não pode controlar a definição de classe e não pode aplicar um lá.  
  
## <a name="see-also"></a>Confira também

- <xref:System.ComponentModel.TypeConverter>
- [Visão geral xaml (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensões de marcação e XAML WPF](markup-extensions-and-wpf-xaml.md)
- [Sintaxe XAML em detalhes](xaml-syntax-in-detail.md)
