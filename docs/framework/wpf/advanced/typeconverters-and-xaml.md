---
title: TypeConverters e XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b7ee4b3b00a675cfafc884d41079b76656bdf49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="typeconverters-and-xaml"></a>TypeConverters e XAML
Este tópico apresenta a finalidade da conversão de tipo de cadeia de caracteres como um recurso de linguagem XAML geral. No .NET Framework, o <xref:System.ComponentModel.TypeConverter> classe serve a uma finalidade específica como parte da implementação de uma classe personalizada gerenciada que pode ser usada como um valor de propriedade no uso do atributo XAML. Se você escrever uma classe personalizada, e você desejar instâncias da sua classe para ser usado como valores de atributo configurável de XAML, você precisa aplicar um <xref:System.ComponentModel.TypeConverterAttribute> à sua classe, escrever um personalizado <xref:System.ComponentModel.TypeConverter> classe, ou ambos.  
  

  
## <a name="type-conversion-concepts"></a>Conceitos de conversão de tipos  
  
### <a name="xaml-and-string-values"></a>XAML e valores de cadeia de caracteres  
 Quando um valor de atributo é definido em um arquivo XAML, o tipo inicial desse valor é uma cadeia de caracteres em texto simples. Outros tipos primitivos como <xref:System.Double> inicialmente são cadeias de caracteres de texto para um processador XAML.  
  
 Um processador XAML precisa de duas informações para processar um valor de atributo. A primeira informação é o tipo de valor da propriedade que está sendo definido. Qualquer cadeia de caracteres que define um valor de atributo e que é processada em XAML deve, por fim, ser convertida ou resolvida para um valor desse tipo. Caso o valor seja um primitivo compreendido pelo analisador XAML (como um valor numérico), será tentada uma conversão direta da cadeia de caracteres. Se o valor for uma enumeração, a cadeia de caracteres será usada para verificar se há uma correspondência de nome com uma constante nomeada na enumeração. Se o valor não for um primitivo compreendido pelo analisador nem uma enumeração, o tipo em questão deverá ser capaz de fornecer uma instância do tipo ou um valor, com base em uma cadeia de caracteres convertida. Isso é feito por meio de indicação de uma classe de conversor de tipos. O conversor de tipos é uma classe auxiliar para fornecer valores de outra classe, tanto para o cenário XAML quanto, potencialmente, para chamadas de código no código .NET.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Usando o comportamento de conversão de tipo existente em XAML  
 Dependendo da sua familiaridade com os conceitos fundamentais de XAML, você pode já estar usando o comportamento de conversão de tipos no aplicativo básico XAML sem perceber. Por exemplo, o WPF define literalmente centenas de propriedades que recebem um valor do tipo <xref:System.Windows.Point>. Um <xref:System.Windows.Point> é um valor que descreve uma coordenada em um espaço de coordenadas bidimensional e ele tem apenas duas propriedades importantes: <xref:System.Windows.Point.X%2A> e <xref:System.Windows.Point.Y%2A>. Quando você especificar um ponto em XAML, você especificar isso como uma cadeia de caracteres com um delimitador (geralmente uma vírgula) entre o <xref:System.Windows.Point.X%2A> e <xref:System.Windows.Point.Y%2A> valores fornecidos por você. Por exemplo: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1">`.  
  
 Até mesmo esse tipo simple de <xref:System.Windows.Point> e seu uso simple em XAML envolvem um conversor de tipo. Nesse caso, que é a classe <xref:System.Windows.PointConverter>.  
  
 O conversor de tipo <xref:System.Windows.Point> definida no simplifica de nível de classe os usos de marcação de todas as propriedades que se <xref:System.Windows.Point>. Sem um conversor de tipos aqui, você precisaria da marcação muito mais detalhada a seguir para o mesmo exemplo mostrado anteriormente:  
  
 `<LinearGradientBrush>`  
  
 `<LinearGradientBrush.StartPoint>`  
  
 `<Point X="0" Y="0"/>`  
  
 `</LinearGradientBrush.StartPoint>`  
  
 `<LinearGradientBrush.EndPoint>`  
  
 `<Point X="1" Y="1"/>`  
  
 `</LinearGradientBrush.EndPoint>`  
  
 `<LinearGradientBrush>`  
  
 Usar a cadeia de caracteres de conversão de tipo ou uma sintaxe equivalente mais detalhada geralmente é uma opção de estilo de codificação. O fluxo de trabalho das ferramentas XAML também pode influenciar a forma como os valores são definidos. Algumas ferramentas XAML tendem a emitir a forma mais detalhada da marcação, porque é mais fácil ir e voltar de modos de exibição de designer ou do próprio mecanismo de serialização.  
  
 Conversores de tipo existente geralmente podem ser descobertos no WPF e do .NET Framework tipos verificando uma classe (ou propriedade) para a presença de um aplicadas <xref:System.ComponentModel.TypeConverterAttribute>. Esse atributo nomeará a classe que é o conversor de tipos de suporte para valores desse tipo, para fins de XAML e, potencialmente, outras finalidades.  
  
### <a name="type-converters-and-markup-extensions"></a>Conversores de tipo e extensões de marcação  
 As extensões de marcação e os conversores de tipos exercem funções ortogonais em termos de comportamento do processador XAML e dos cenários aos quais são aplicados. Embora o contexto esteja disponível para usos de extensão de marcação, o comportamento de conversão de tipos de propriedades em que uma extensão de marcação fornece um valor geralmente não é verificado em implementações de extensão de marcação. Em outras palavras, mesmo se uma extensão de marcação retornar uma cadeia de caracteres de texto como saída do `ProvideValue`, o comportamento de conversão de tipo dessa cadeia de caracteres, conforme aplicado a uma propriedade específica ou a um tipo de valor da propriedade, não será chamado. Em geral, a finalidade de uma extensão de marcação é processar uma cadeia de caracteres e retornar um objeto sem nenhum conversor de tipo envolvido.  
  
 Uma situação comum em que uma extensão de marcação é necessária, em vez de um conversor de tipos, é para fazer referência a um objeto que já existe. Na melhor das hipóteses, um conversor de tipo sem monitoração de estado pode gerar somente uma nova instância, o que pode não ser desejável. Para obter mais informações sobre extensões de marcação, consulte [Extensões de marcação e XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Conversores de tipos nativos  
 Na implementação do analisador XAML do WPF e do .NET Framework, alguns tipos têm manipulação de conversão de tipos nativos; porém, não são tipos que poderiam ser interpretados, convencionalmente, como primitivos. Um exemplo desse tipo é <xref:System.DateTime>. A razão para isso é baseada no funcionamento da arquitetura do .NET Framework: o tipo <xref:System.DateTime> é definido no mscorlib, a biblioteca mais básica do .NET. <xref:System.DateTime>não tem permissão para ser atribuído com um atributo que vêm de outro assembly que apresenta uma dependência (<xref:System.ComponentModel.TypeConverterAttribute> é do sistema) para o mecanismo de descoberta de conversor de tipo normal por atribuição não pode ser suportado. Em vez disso, o analisador XAML tem uma lista de tipos que precisam de tal processamento nativo e os processa da mesma forma como os primitivos verdadeiros são processados. (No caso de <xref:System.DateTime> isso envolve uma chamada para <xref:System.DateTime.Parse%2A>.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementando um conversor de tipos  
  
### <a name="typeconverter"></a>TypeConverter  
 No <xref:System.Windows.Point> exemplo fornecido anteriormente, a classe <xref:System.Windows.PointConverter> foi mencionado. Para implementações de .NET de XAML, todos os conversores de tipo que são usados para fins XAML são classes que derivam da classe base <xref:System.ComponentModel.TypeConverter>. O <xref:System.ComponentModel.TypeConverter> classe existia em versões do .NET Framework que precedem a existência de XAML; um dos seus usos originais era fornecer conversão de cadeia de caracteres para caixas de diálogo de propriedade em designers visuais. Para XAML, a função de <xref:System.ComponentModel.TypeConverter> é expandido para incluir sendo a classe base para conversões de cadeia de caracteres e de cadeia de caracteres que permitem analisar o valor de atributo de cadeia de caracteres e um valor de tempo de execução de uma propriedade de objeto específico de processamento possivelmente novamente em uma cadeia de caracteres para serialização como um atributo.  
  
 <xref:System.ComponentModel.TypeConverter>define quatro membros que são relevantes para converter para e de cadeias de caracteres para fins de processamento de XAML:  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Desses, o método mais importante é <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Esse método converte a cadeia de caracteres de entrada para o tipo de objeto necessário. Estritamente falando, o <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> método pode ser implementado para converter uma grande variedade de tipos para o tipo de destino pretendido do conversor e, portanto, têm finalidades que ampliam XAML, como suporte a conversões de tempo de execução, mas para fins XAML é apenas o caminho de código que pode processar um <xref:System.String> entrada que é importante.  
  
 O próximo método mais importante é <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Se um aplicativo é convertido em uma representação de marcação (por exemplo, se ele for salvo em XAML, como um arquivo), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> é responsável por produzir uma representação de marcação. Nesse caso, o caminho de código que é importante para XAML é quando você passar um `destinationType` de <xref:System.String> .  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>e <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> são métodos de suporte que são usados quando os recursos de consultas de um serviço de <xref:System.ComponentModel.TypeConverter> implementação. Esses métodos devem ser implementados para retornar o `true` para casos específicos de tipo aos quais os métodos de conversão equivalentes do seu conversor dão suporte. Para fins XAML, isso geralmente significa o <xref:System.String> tipo.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informações de cultura e conversores de tipos para XAML  
 Cada <xref:System.ComponentModel.TypeConverter> implementação pode ter sua própria interpretação do que constitui uma cadeia de caracteres válida para a conversão e pode também usar ou ignorar a descrição do tipo passada como parâmetros. Há uma consideração importante em relação à cultura e à conversão de tipos XAML. O XAML dá suporte total ao uso de cadeias de caracteres localizáveis como valores de atributos. Porém, não há suporte para o uso dessa cadeia de caracteres localizável como entrada do conversor de tipos com exigências específicas de cultura, porque os conversores de tipos para valores de atributos XAML envolvem um comportamento de análise de linguagem necessariamente fixo, usando a cultura do `en-US`. Para obter mais informações sobre os motivos de design para essa restrição, você deve consultar a especificação da linguagem XAML ([\[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)).  
  
 Como exemplo de casos em que a cultura pode ser um problema, algumas culturas usam vírgula como delimitador de ponto decimal para números. Isso vai de encontro ao comportamento que muitos dos conversores de tipos XAML do WPF têm, que é usar uma vírgula como delimitador (com base em precedentes históricos, como a forma comum X,Y ou listas delimitadas por vírgulas). Nem mesmo a passagem de uma cultura no XAML ao redor (definindo `Language` ou `xml:lang` para a cultura do `sl-SI`, um exemplo de cultura que usa vírgula para decimal dessa maneira) resolve o problema.  
  
### <a name="implementing-convertfrom"></a>Implementando ConvertFrom  
 Para ser usado como um <xref:System.ComponentModel.TypeConverter> implementação com suporte para XAML, a <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> método para esse conversor deverá aceitar uma cadeia de caracteres como o `value` parâmetro. Se a cadeia de caracteres era inválido Formatar e pode ser convertida pelo <xref:System.ComponentModel.TypeConverter> implementação e, em seguida, o objeto retornado deve oferecer suporte a uma conversão para o tipo esperado pela propriedade. Caso contrário, o <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementação deve retornar `null`.  
  
 Cada <xref:System.ComponentModel.TypeConverter> implementação pode ter sua própria interpretação do que constitui uma cadeia de caracteres válida para a conversão e pode também usar ou ignorar os contextos de descrição ou a cultura de tipo passados como parâmetros. No entanto, o processamento de XAML do WPF não pode passar valores para o contexto de descrição de tipo em todos os casos; tampouco consegue passar a cultura com base no `xml:lang`.  
  
> [!NOTE]
>  Não utilize os caracteres de chave, especialmente o {, como elemento possível do formato da cadeia de caracteres. Esses caracteres são reservados como entrada e saída para uma sequência de extensão de marcação.  
  
### <a name="implementing-convertto"></a>Implementando ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>potencialmente é usado para suporte de serialização. Suporte a serialização por <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> para seu tipo personalizado e seu tipo de conversor não é um requisito absoluto. No entanto, se você estiver implementando um controle ou usando a serialização de como parte dos recursos ou o design da sua classe, você deve implementar <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Para ser usado como um <xref:System.ComponentModel.TypeConverter> implementação com suporte para XAML, a <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> método para esse conversor deverá aceitar uma instância do tipo (ou um valor) suporte como a `value` parâmetro. Quando o `destinationType` parâmetro é do tipo <xref:System.String>, em seguida, o objeto retornado deve ser capaz de ser convertida como <xref:System.String>. A cadeia de caracteres retornada deve representar um valor serializado de `value`. Idealmente, o formato de serialização que você escolher deve ser capaz de gerar o mesmo valor se essa cadeia de caracteres foi passada para o <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementação de conversor do mesmo, sem perda significativa de informações.  
  
 Se o valor não pode ser serializado, ou se o conversor não oferece suporte à serialização, o <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> implementação deve retornar `null`e é permitido para lançar uma exceção nesse caso. Mas se lançar exceções, você pode relatar a incapacidade de usar essa conversão como parte de sua <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementação para que a prática recomendada de verificação com <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> primeiro evitar exceções é suportado.  
  
 Se `destinationType` parâmetro não é do tipo <xref:System.String>, você pode escolher seu próprio tratamento de conversor. Normalmente, você reverteria a implementação base tratamento, o que o basemost <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> gera uma exceção específica.  
  
### <a name="implementing-canconvertto"></a>Implementando CanConvertTo  
 O <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementação deve retornar `true` para `destinationType` do tipo <xref:System.String>e caso contrário Adiar para a implementação base.  
  
### <a name="implementing-canconvertfrom"></a>Implementando CanConvertFrom  
 O <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> implementação deve retornar `true` para `sourceType` do tipo <xref:System.String>e caso contrário Adiar para a implementação base.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Aplicando o TypeConverterAttribute  
 Para que o conversor de tipo personalizado a ser usado como a atuar conversor de tipo para uma classe personalizada por um processador XAML, você deve aplicar o [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> à sua definição de classe. O <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> que você especifique por meio do atributo deve ser o nome do tipo do seu conversor de tipo personalizado. Com esse atributo aplicado, quando um processador XAML manipula valores em que o tipo de propriedade usa o tipo de classe personalizada, ele pode processar cadeias de caracteres de entrada e retornar as instâncias de objeto.  
  
 Também é possível fornecer um conversor de tipos por propriedade. Em vez de aplicar um [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> na definição de classe, aplicá-la a uma definição de propriedade (definição do principal, não o `get` / `set` implementações dentro dela). O tipo da propriedade deve corresponder ao tipo que é processado pelo conversor de tipos personalizado. Com esse atributo aplicado, quando um processador XAML manipula valores dessa propriedade, ele pode processar cadeias de caracteres de entrada e retornar as instâncias de objeto. A técnica de conversor de tipo de propriedade é particularmente útil se você optar por usar um tipo de propriedade do [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] ou de alguma outra biblioteca onde você não pode controlar a definição de classe e não é possível aplicar um <xref:System.ComponentModel.TypeConverterAttribute> existe.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.TypeConverter>  
 [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensões de marcação e XAML do WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Sintaxe XAML em detalhes](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
