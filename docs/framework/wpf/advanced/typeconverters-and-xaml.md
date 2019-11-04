---
title: TypeConverters e XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: aac6c347886b2c29e599952d7642fbe76441b617
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458916"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters e XAML
Este tópico apresenta a finalidade da conversão de tipo de cadeia de caracteres como um recurso de linguagem XAML geral. Na .NET Framework, a classe <xref:System.ComponentModel.TypeConverter> atende a uma finalidade específica como parte da implementação de uma classe personalizada gerenciada que pode ser usada como um valor de propriedade no uso do atributo XAML. Se você escrever uma classe personalizada e desejar que as instâncias da sua classe sejam utilizáveis como valores de atributo configurável XAML, talvez seja necessário aplicar um <xref:System.ComponentModel.TypeConverterAttribute> à sua classe, escrever uma classe de <xref:System.ComponentModel.TypeConverter> personalizada ou ambos.  

## <a name="type-conversion-concepts"></a>Conceitos de conversão de tipos  
  
### <a name="xaml-and-string-values"></a>XAML e valores de cadeia de caracteres  
 Quando um valor de atributo é definido em um arquivo XAML, o tipo inicial desse valor é uma cadeia de caracteres em texto simples. Até mesmo outros primitivos, como <xref:System.Double> são cadeias de caracteres de texto inicialmente para um processador XAML.  
  
 Um processador XAML precisa de duas informações para processar um valor de atributo. A primeira informação é o tipo de valor da propriedade que está sendo definido. Qualquer cadeia de caracteres que define um valor de atributo e que é processada em XAML deve, por fim, ser convertida ou resolvida para um valor desse tipo. Caso o valor seja um primitivo compreendido pelo analisador XAML (como um valor numérico), será tentada uma conversão direta da cadeia de caracteres. Se o valor for uma enumeração, a cadeia de caracteres será usada para verificar se há uma correspondência de nome com uma constante nomeada na enumeração. Se o valor não for um primitivo compreendido pelo analisador nem uma enumeração, o tipo em questão deverá ser capaz de fornecer uma instância do tipo ou um valor, com base em uma cadeia de caracteres convertida. Isso é feito por meio de indicação de uma classe de conversor de tipos. O conversor de tipos é uma classe auxiliar para fornecer valores de outra classe, tanto para o cenário XAML quanto, potencialmente, para chamadas de código no código .NET.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Usando o comportamento de conversão de tipo existente em XAML  
 Dependendo da sua familiaridade com os conceitos fundamentais de XAML, você pode já estar usando o comportamento de conversão de tipos no aplicativo básico XAML sem perceber. Por exemplo, o WPF define literalmente centenas de propriedades que usam um valor do tipo <xref:System.Windows.Point>. Uma <xref:System.Windows.Point> é um valor que descreve uma coordenada em um espaço de coordenadas bidimensional e, na verdade, tem apenas duas propriedades importantes: <xref:System.Windows.Point.X%2A> e <xref:System.Windows.Point.Y%2A>. Quando você especifica um ponto no XAML, você o especifica como uma cadeia de caracteres com um delimitador (normalmente uma vírgula) entre o <xref:System.Windows.Point.X%2A> e os valores de <xref:System.Windows.Point.Y%2A> que você fornece. Por exemplo: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`.  
  
 Até mesmo esse simples tipo de <xref:System.Windows.Point> e seu uso simples em XAML envolvem um conversor de tipo. Nesse caso, essa é a classe <xref:System.Windows.PointConverter>.  
  
 O conversor de tipo para <xref:System.Windows.Point> definido no nível de classe simplifica os usos de marcação de todas as propriedades que usam <xref:System.Windows.Point>. Sem um conversor de tipos aqui, você precisaria da marcação muito mais detalhada a seguir para o mesmo exemplo mostrado anteriormente:  

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
  
 Os conversores de tipo existentes geralmente podem ser descobertos em tipos WPF e .NET Framework verificando uma classe (ou Propriedade) quanto à presença de uma <xref:System.ComponentModel.TypeConverterAttribute>aplicada. Esse atributo nomeará a classe que é o conversor de tipos de suporte para valores desse tipo, para fins de XAML e, potencialmente, outras finalidades.  
  
### <a name="type-converters-and-markup-extensions"></a>Conversores de tipo e extensões de marcação  
 As extensões de marcação e os conversores de tipos exercem funções ortogonais em termos de comportamento do processador XAML e dos cenários aos quais são aplicados. Embora o contexto esteja disponível para usos de extensão de marcação, o comportamento de conversão de tipos de propriedades em que uma extensão de marcação fornece um valor geralmente não é verificado em implementações de extensão de marcação. Em outras palavras, mesmo se uma extensão de marcação retornar uma cadeia de caracteres de texto como saída do `ProvideValue`, o comportamento de conversão de tipo dessa cadeia de caracteres, conforme aplicado a uma propriedade específica ou a um tipo de valor da propriedade, não será chamado. Em geral, a finalidade de uma extensão de marcação é processar uma cadeia de caracteres e retornar um objeto sem nenhum conversor de tipo envolvido.  
  
 Uma situação comum em que uma extensão de marcação é necessária, em vez de um conversor de tipos, é para fazer referência a um objeto que já existe. Na melhor das hipóteses, um conversor de tipo sem monitoração de estado pode gerar somente uma nova instância, o que pode não ser desejável. Para obter mais informações sobre extensões de marcação, consulte [Extensões de marcação e XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Conversores de tipos nativos  
 Na implementação do analisador XAML do WPF e do .NET Framework, alguns tipos têm manipulação de conversão de tipos nativos; porém, não são tipos que poderiam ser interpretados, convencionalmente, como primitivos. Um exemplo desse tipo é <xref:System.DateTime>. O motivo disso se baseia em como a arquitetura de .NET Framework funciona: o tipo <xref:System.DateTime> é definido em mscorlib, a biblioteca mais básica no .NET. <xref:System.DateTime> não tem permissão para ser atribuída a um atributo proveniente de outro assembly que introduz uma dependência (<xref:System.ComponentModel.TypeConverterAttribute> é do sistema), portanto, o mecanismo de descoberta do conversor de tipo usual por atribuição não pode ser suportado. Em vez disso, o analisador XAML tem uma lista de tipos que precisam de tal processamento nativo e os processa da mesma forma como os primitivos verdadeiros são processados. (No caso de <xref:System.DateTime> isso envolve uma chamada para <xref:System.DateTime.Parse%2A>.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementando um conversor de tipos  
  
### <a name="typeconverter"></a>TypeConverter  
 No exemplo de <xref:System.Windows.Point> fornecido anteriormente, a classe <xref:System.Windows.PointConverter> foi mencionada. Para implementações do .NET de XAML, todos os conversores de tipo usados para fins XAML são classes que derivam da classe base <xref:System.ComponentModel.TypeConverter>. A classe <xref:System.ComponentModel.TypeConverter> existia em versões do .NET Framework que precedem a existência do XAML; um de seus usos originais era fornecer conversão de cadeia de caracteres para caixas de diálogo de propriedade em designers visuais. Para o XAML, a função de <xref:System.ComponentModel.TypeConverter> é expandida para incluir a classe base para as conversões de cadeia de caracteres e de cadeia de caracteres que habilitam a análise de um valor de atributo de cadeia de caracteres e, possivelmente, o processamento de um valor de tempo de execução de uma propriedade de objeto específica de volta para uma cadeia de caracteres para serialização como um atributo.  
  
 <xref:System.ComponentModel.TypeConverter> define quatro membros que são relevantes para a conversão de e para cadeias de caracteres para fins de processamento XAML:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Desses, o método mais importante é <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Esse método converte a cadeia de caracteres de entrada para o tipo de objeto necessário. Estritamente falando, o método <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> poderia ser implementado para converter um intervalo muito mais amplo de tipos no tipo de destino pretendido do conversor e, portanto, atender a finalidades que se estendem além de XAML, como suporte a conversões de tempo de execução, mas para fins de XAML, ele é somente o caminho de código que pode processar uma entrada de <xref:System.String> que importa.  
  
 O próximo método mais importante é <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Se um aplicativo for convertido em uma representação de marcação (por exemplo, se for salvo em XAML como um arquivo), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> será responsável por produzir uma representação de marcação. Nesse caso, o caminho de código que importa para XAML é quando você passa uma `destinationType` de <xref:System.String>.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> e <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> são métodos de suporte que são usados quando um serviço consulta os recursos da implementação do <xref:System.ComponentModel.TypeConverter>. Esses métodos devem ser implementados para retornar o `true` para casos específicos de tipo aos quais os métodos de conversão equivalentes do seu conversor dão suporte. Para fins de XAML, isso geralmente significa o tipo de <xref:System.String>.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informações de cultura e conversores de tipos para XAML  
 Cada implementação de <xref:System.ComponentModel.TypeConverter> pode ter sua própria interpretação do que constitui uma cadeia de caracteres válida para uma conversão e também pode usar ou ignorar a descrição do tipo passada como parâmetros. Há uma consideração importante em relação à cultura e à conversão de tipos XAML. O XAML dá suporte total ao uso de cadeias de caracteres localizáveis como valores de atributos. Porém, não há suporte para o uso dessa cadeia de caracteres localizável como entrada do conversor de tipos com exigências específicas de cultura, porque os conversores de tipos para valores de atributos XAML envolvem um comportamento de análise de linguagem necessariamente fixo, usando a cultura do `en-US`. Para obter mais informações sobre os motivos de design para essa restrição, você deve consultar a especificação da linguagem XAML ([\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)).  
  
 Como exemplo de casos em que a cultura pode ser um problema, algumas culturas usam vírgula como delimitador de ponto decimal para números. Isso vai de encontro ao comportamento que muitos dos conversores de tipos XAML do WPF têm, que é usar uma vírgula como delimitador (com base em precedentes históricos, como a forma comum X,Y ou listas delimitadas por vírgulas). Nem mesmo a passagem de uma cultura no XAML ao redor (definindo `Language` ou `xml:lang` para a cultura do `sl-SI`, um exemplo de cultura que usa vírgula para decimal dessa maneira) resolve o problema.  
  
### <a name="implementing-convertfrom"></a>Implementando ConvertFrom  
 Para ser utilizável como uma implementação <xref:System.ComponentModel.TypeConverter> que dá suporte a XAML, o método <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> para esse conversor deve aceitar uma cadeia de caracteres como o parâmetro `value`. Se a cadeia de caracteres estava em um formato válido e puder ser convertida pela implementação de <xref:System.ComponentModel.TypeConverter>, o objeto retornado deverá dar suporte a uma conversão para o tipo esperado pela propriedade. Caso contrário, a implementação de <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> deve retornar `null`.  
  
 Cada implementação de <xref:System.ComponentModel.TypeConverter> pode ter sua própria interpretação do que constitui uma cadeia de caracteres válida para uma conversão e também pode usar ou ignorar a descrição do tipo ou contextos de cultura passados como parâmetros. No entanto, o processamento de XAML do WPF não pode passar valores para o contexto de descrição de tipo em todos os casos; tampouco consegue passar a cultura com base no `xml:lang`.  
  
> [!NOTE]
> Não utilize os caracteres de chave, especialmente o {, como elemento possível do formato da cadeia de caracteres. Esses caracteres são reservados como entrada e saída para uma sequência de extensão de marcação.  
  
### <a name="implementing-convertto"></a>Implementando ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> é potencialmente usado para suporte de serialização. O suporte de serialização por meio de <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> para seu tipo personalizado e seu conversor de tipo não é um requisito absoluto. No entanto, se você estiver implementando um controle ou usando a serialização do como parte dos recursos ou do design de sua classe, deverá implementar <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Para ser utilizável como uma implementação <xref:System.ComponentModel.TypeConverter> que dá suporte a XAML, o método <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> para esse conversor deve aceitar uma instância do tipo (ou um valor) com suporte como o parâmetro `value`. Quando o parâmetro `destinationType` é o tipo <xref:System.String>, o objeto retornado deve ser capaz de ser convertido como <xref:System.String>. A cadeia de caracteres retornada deve representar um valor serializado de `value`. O ideal é que o formato de serialização escolhido seja capaz de gerar o mesmo valor se essa cadeia de caracteres fosse passada para a implementação de <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> do mesmo conversor, sem perda significativa de informações.  
  
 Se o valor não puder ser serializado ou o conversor não oferecer suporte à serialização, a implementação de <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> deverá retornar `null`e terá permissão para gerar uma exceção nesse caso. Mas se você lançar exceções, deverá informar a incapacidade de usar essa conversão como parte de sua implementação de <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> para que a prática recomendada de verificação com <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> primeiro para evitar exceções seja suportada.  
  
 Se `destinationType` parâmetro não for do tipo <xref:System.String>, você poderá escolher sua própria manipulação de conversor. Normalmente, você reverteria para o tratamento de implementação base, que no <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> basemost gera uma exceção específica.  
  
### <a name="implementing-canconvertto"></a>Implementando CanConvertTo  
 Sua implementação de <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> deve retornar `true` para `destinationType` do tipo <xref:System.String>e, caso contrário, adiar para a implementação base.  
  
### <a name="implementing-canconvertfrom"></a>Implementando CanConvertFrom  
 Sua implementação de <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> deve retornar `true` para `sourceType` do tipo <xref:System.String>e, caso contrário, adiar para a implementação base.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Aplicando o TypeConverterAttribute  
 Para que o conversor de tipo personalizado seja usado como o conversor de tipo atuante para uma classe personalizada por um processador XAML, você deve aplicar o <xref:System.ComponentModel.TypeConverterAttribute> à sua definição de classe. O <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> especificado por meio do atributo deve ser o nome do tipo do conversor de tipo personalizado. Com esse atributo aplicado, quando um processador XAML manipula valores em que o tipo de propriedade usa o tipo de classe personalizada, ele pode processar cadeias de caracteres de entrada e retornar as instâncias de objeto.  
  
 Também é possível fornecer um conversor de tipos por propriedade. Em vez de aplicar um <xref:System.ComponentModel.TypeConverterAttribute> à definição de classe, aplique-o a uma definição de propriedade (a definição principal, não o `get`/`set` implementações dentro dele). O tipo da propriedade deve corresponder ao tipo que é processado pelo conversor de tipos personalizado. Com esse atributo aplicado, quando um processador XAML manipula valores dessa propriedade, ele pode processar cadeias de caracteres de entrada e retornar instâncias de objeto. A técnica de conversor de tipo por propriedade é particularmente útil se você optar por usar um tipo de Propriedade do Microsoft .NET Framework ou de alguma outra biblioteca em que você não pode controlar a definição de classe e não pode aplicar um <xref:System.ComponentModel.TypeConverterAttribute> lá.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ComponentModel.TypeConverter>
- [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md)
- [Sintaxe XAML em detalhes](xaml-syntax-in-detail.md)
