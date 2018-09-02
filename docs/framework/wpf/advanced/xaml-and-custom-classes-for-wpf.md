---
title: XAML e classes personalizadas para WPF
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: acf3ba12a9a7e6ba9a8e378892098f5f265a23d9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43461794"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>XAML e classes personalizadas para WPF
Tal como implementado nas estruturas do [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)], o XAML dá suporte à capacidade de definir uma classe ou estrutura personalizada em qualquer linguagem do [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] e, em seguida, acessar essa classe usando a marcação de XAML. É possível usar uma mistura de tipos definidos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] e tipos personalizados dentro do mesmo arquivo de marcação, normalmente mapeando os tipos personalizados até um prefixo de namespace de XAML. Este tópico aborda as exigências que uma classe personalizada deve cumprir para que possa ser usada como um elemento XAML.  
  
 
  
<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>Classes personalizadas em aplicativos ou assemblies  
 As classes personalizadas que são usadas em XAML podem ser definidas de duas maneiras distintas: dentro do code-behind ou outro código que produz o aplicativo primário do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ou como uma classe em um assembly separado, como um executável ou DLL usados como biblioteca de classes. Cada uma dessas abordagens apresenta vantagens e desvantagens.  
  
-   A vantagem de criar uma biblioteca de classes é que qualquer uma dessas classes personalizadas pode ser compartilhada entre vários aplicativos possíveis diferentes. Uma biblioteca separada também facilita o controle de problemas de versão dos aplicativos e simplifica uma classe em que o uso pretendido da classe é como um elemento raiz em uma página XAML.  
  
-   A vantagem de definir as classes personalizadas no aplicativo é que essa técnica é relativamente simples e minimiza os problemas de implantação e testes encontrados quando assemblies separados são introduzidos além do executável principal do aplicativo.  
  
-   Se definidas no mesmo assembly ou em um assembly diferente, as classes personalizadas precisam ser mapeadas entre o namespace de CLR e o namespace de XML para que possam ser usadas no XAML como elementos. Consulte [Namespaces de XAML e mapeamento de namespace para XAML do WPF](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>Exigências para uma classe personalizada como um elemento XAML  
 Para que possa ser instanciada como um elemento de objeto, sua classe deve cumprir as exigências abaixo:  
  
-   A classe personalizada deve ser pública e dar suporte a um construtor público padrão (sem parâmetros). (Consulte a seção a seguir para ver as observações sobre estruturas.)  
  
-   A classe personalizada não deve ser uma classe aninhada. As classes aninhadas e o “ponto” na sintaxe de uso do CLR geral interferem com outros recursos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e/ou do XAML, como propriedades anexadas.  
  
 Além de habilitar a sintaxe de elemento de objeto, sua definição de objeto também habilita a sintaxe de elemento de propriedade para outras propriedades públicas que assumem o objeto como o tipo de valor. Isso ocorre porque, agora, o objeto pode ser instanciado como um elemento de objeto e pode preencher o valor do elemento da propriedade de tal propriedade.  
  
### <a name="structures"></a>Estruturas  
 As estruturas definidas como tipos personalizados sempre podem ser construídas em XAML no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Isso ocorre porque os compiladores do [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] criam implicitamente um construtor padrão para uma estrutura que inicializa todos os valores da propriedade para seus padrões. Em alguns casos, o comportamento de construção padrão e/ou o uso do elemento de objeto para uma estrutura não é desejável. Isso pode ocorrer porque a estrutura se destina a preencher valores e a funcionar conceitualmente como uma união, em que os valores contidos poderão ter interpretações mutuamente exclusivas e, consequentemente, nenhuma das propriedades será configurável. Um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] exemplo de uma estrutura é <xref:System.Windows.GridLength>. Em geral, tais estruturas devem implementar um conversor de tipo de modo que os valores possam ser expressos na forma de atributo, usando as convenções de cadeia de caracteres que criam a interpretações ou modos diferentes de valores da estrutura. A estrutura também deve expor um comportamento semelhante para a construção de código por meio de um construtor não padrão.  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>Exigências para as propriedades de uma classe personalizada como atributos XAML  
 As propriedades devem fazer referência a um tipo por valor (como um primitivo) ou usar uma classe de tipo que tem um construtor padrão ou um conversor de tipos dedicado que um processador XAML possa acessar. Na implementação do CLR XAML, os processadores XAML encontram tais conversores por meio do suporte nativo para primitivos de linguagem, ou aplicativo de <xref:System.ComponentModel.TypeConverterAttribute> para um tipo ou membro em definições de tipo de backup  
  
 Como alternativa, a propriedade poderá fazer referência a um tipo de classe abstrata ou a uma interface. Para classes abstratas ou interfaces, a expectativa de análise de XAML é que o valor da propriedade deve ser preenchido com instâncias de classe práticas que implementam a interface ou instâncias dos tipos que derivam da classe abstrata.  
  
 As propriedades podem ser declaradas em uma classe abstrata, mas podem ser definidas somente em classes práticas que derivam da classe abstrata. Isso ocorre porque criar o elemento de objeto para a classe requer um construtor padrão público na classe.  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>Sintaxe de atributo habilitada para TypeConverter  
 Se você fornecer um conversor de tipos atribuído e dedicado no nível de classe, a conversão de tipos aplicada habilita a sintaxe de atributo para qualquer propriedade que precise instanciar esse tipo. Um conversor de tipos não permite o uso do elemento de objeto do tipo; somente a presença de um construtor padrão para esse tipo permite o uso do elemento de objeto. Portanto, propriedades que são habilitadas por conversor de tipos geralmente não são utilizáveis em sintaxe de propriedade, a menos que o próprio tipo também dê suporte à sintaxe de elemento de objeto. A exceção é que é possível especificar uma sintaxe de elemento de propriedade, mas o elemento de propriedade contêm uma cadeia de caracteres. Esse uso é, basicamente, equivalente ao uso de sintaxe de atributo, e tal uso não é comum, a menos que haja uma necessidade de manipulação mais robusta de espaço em branco do valor do atributo. O exemplo a seguir é um uso de elemento de propriedade que usa uma cadeia de caracteres e o equivalente do uso de atributo:  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 Exemplos de propriedades em que a sintaxe de atributo é permitida, mas sintaxe de elemento de propriedade que contém um elemento de objeto não é permitido por meio de XAML são várias propriedades que usam o <xref:System.Windows.Input.Cursor> tipo. O <xref:System.Windows.Input.Cursor> classe possui um conversor de tipo dedicado <xref:System.Windows.Input.CursorConverter>, mas não expõe um construtor padrão, portanto, o <xref:System.Windows.FrameworkElement.Cursor%2A> propriedade só pode ser definida por meio da sintaxe de atributo, embora o real <xref:System.Windows.Input.Cursor> é um tipo de referência.  
  
### <a name="per-property-type-converters"></a>Conversores de tipo por propriedade  
 Como alternativa, a própria propriedade poderá declarar um conversor de tipos no nível de propriedade. Isso permite que uma "minilinguagem" que instancia objetos do tipo da propriedade em linha, processando valores de cadeia de caracteres de entrada do atributo como entrada para um <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> operação com base no tipo apropriado. Normalmente, isso é feito para fornecer um acessador de conveniência, mas não como meio exclusivo para configurar uma propriedade em XAML. No entanto, também é possível usar conversores de tipos para atributos em que você deseja usar [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] tipos existentes que não fornecem um construtor padrão ou um conversor de tipos atribuído. Exemplos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API são algumas propriedades que usam o <xref:System.Globalization.CultureInfo> tipo. Nesse caso, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usado o Microsoft .NET Framework existentes <xref:System.Globalization.CultureInfo> tipo para abordar melhor compatibilidade e cenários de migração que foram usados nas versões anteriores das estruturas, mas o <xref:System.Globalization.CultureInfo> tipo não oferecia suporte o necessário construtores ou conversão de tipo de nível de tipo para ser usado como um valor da propriedade XAML diretamente.  
  
 Sempre que você expõe uma propriedade que tem uma utilização de XAML, especialmente se for um autor de controle, considere a possibilidade de dar suporte a essa propriedade com uma propriedade de dependência. Isso é especialmente verdadeiro se você usar existente [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] implementação do processador XAML, porque você pode melhorar o desempenho usando <xref:System.Windows.DependencyProperty> fazendo. Uma propriedade de dependência vai expor recursos do sistema de propriedades para a propriedade que os usuários virão a esperar de uma propriedade acessível do XAML. Isso inclui recursos como animação, vinculação de dados e suporte de estilo. Para obter mais informações, consulte [Propriedades de dependência personalizada](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) e [Carregamento de XAML e propriedades de dependência](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
### <a name="writing-and-attributing-a-type-converter"></a>Gravando e atribuindo um conversor de tipos  
 Ocasionalmente, será preciso escrever um personalizado <xref:System.ComponentModel.TypeConverter> derivado da classe para fornecer conversão de tipo para seu tipo de propriedade. Para obter instruções sobre como derivar e criar um conversor de tipo que pode dar suporte a usos XAML e como aplicar a <xref:System.ComponentModel.TypeConverterAttribute>, consulte [TypeConverters e XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>Exigências de sintaxe de atributo do manipulador de eventos XAML em eventos de uma classe personalizada  
 Para que possa ser usado como um evento do [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)], o evento deve ser exposto como um evento público em uma classe que dá suporte a um construtor padrão ou em uma classe abstrata onde o evento pode ser acessado em classes derivadas. Para ser usado de forma conveniente como um evento roteado, sua [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] evento deve implementar explícita `add` e `remove` métodos, que adicionam e removem manipuladores para o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] assinatura de evento e encaminham tais manipuladores para o <xref:System.Windows.UIElement.AddHandler%2A>e <xref:System.Windows.UIElement.RemoveHandler%2A> métodos. Esses métodos adicionam ou removem os manipuladores para o armazenamento do manipulador de eventos roteados na instância à qual o evento está anexado.  
  
> [!NOTE]
>  É possível registrar manipuladores diretamente para eventos roteados usando <xref:System.Windows.UIElement.AddHandler%2A>e para deliberadamente não definir um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] evento que expõe o evento roteado. Em geral, isso não é recomendado, porque o evento não permitirá sintaxe de atributo XAML para anexar manipuladores; a classe resultante oferecerá um modo de exibição de XAML menos transparente dos recursos do tipo.  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>Gravando propriedades de coleção  
 As propriedades que usam um tipo de coleção têm uma sintaxe XAML que permite especificar os objetos que são adicionados à coleção. Essa sintaxe possui dois recursos notáveis.  
  
-   O objeto que é o objeto de coleção não precisa ser especificado na sintaxe de elemento de objeto. A presença desse tipo de coleção é implícita sempre que você especifica uma propriedade em XAML que utiliza um tipo de coleção.  
  
-   Os elementos filho da propriedade de coleção na marcação são processados para se tornarem membros da coleção. Normalmente, o acesso ao código para os membros de uma coleção é realizado por meio de métodos de lista/dicionário, como `Add`, ou por meio de um indexador. Entretanto, a sintaxe de XAML não dá suporte a métodos ou indexadores (exceção: o XAML 2009 pode dar suporte a métodos, mas seu uso restringe os possíveis usos do WPF; consulte [Recursos da linguagem XAML 2009](../../../../docs/framework/xaml-services/xaml-2009-language-features.md)). As coleções obviamente são uma exigência muito comum para a criação de uma árvore de elementos; você precisa de alguma forma para preencher essas coleções em XAML declarativo. Portanto, os elementos filho de uma propriedade de coleção são processados ao serem adicionados à coleção que é o valor de tipo de propriedade da coleção.  
  
 A implementação de serviços de XAML do .NET Framework e, consequentemente, o processador XAML do WPF usam a seguinte definição para o que constitui uma propriedade de coleção. O tipo de propriedade da propriedade deve implementar um dos seguintes:  
  
-   Implementa <xref:System.Collections.IList>.  
  
-   Implementa <xref:System.Collections.IDictionary> ou o equivalente genérico (<xref:System.Collections.Generic.IDictionary%602>).  
  
-   Deriva <xref:System.Array> (para obter mais informações sobre matrizes em XAML, consulte [extensão de marcação X:array](../../../../docs/framework/xaml-services/x-array-markup-extension.md).)  
  
-   Implementa <xref:System.Windows.Markup.IAddChild> (uma interface definida por [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]).  
  
 Cada um desses tipos de CLR tem um método do `Add`, que é usado pelo processador de XAML para adicionar itens à coleção subjacente ao criar o grafo do objeto.  
  
> [!NOTE]
>  Genérica `List` e `Dictionary` interfaces (<xref:System.Collections.Generic.IList%601> e <xref:System.Collections.Generic.IDictionary%602>) não têm suporte para detecção de coleção pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] processador XAML. No entanto, você pode usar o <xref:System.Collections.Generic.List%601> da classe como uma classe base, pois ela implementa <xref:System.Collections.IList> diretamente, ou <xref:System.Collections.Generic.Dictionary%602> como uma classe base, pois ela implementa <xref:System.Collections.IDictionary> diretamente.  
  
 Quando declarar uma propriedade que utiliza uma coleção, tenha cuidado com a maneira como o valor da propriedade é inicializado em novas instâncias do tipo. Se você não estiver implementando a propriedade como uma propriedade de dependência, é adequado que ela use um campo de suporte que chame o construtor do tipo de coleção. Se a propriedade for uma propriedade de dependência, talvez seja necessário inicializar a propriedade de coleção como parte do construtor de tipo padrão. Isso ocorre porque uma propriedade de dependência extrai o valor padrão de metadados e, normalmente, você não quer que o valor inicial de uma propriedade de coleção seja uma coleção estática e compartilhada. Deve haver uma instância de coleção por cada instância de tipo. Para obter mais informações, consulte [Propriedades de dependência personalizada](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
 É possível implementar um tipo de coleção personalizada para sua propriedade da coleção. Por causa do tratamento de propriedade de coleção implícito, o tipo de coleção personalizada não precisa fornecer um construtor padrão para ser usado em XAML implicitamente. No entanto, opcionalmente, você pode fornecer um construtor padrão para o tipo de coleção. Pode ser uma prática que vale a pena. Exceto se fornecer um construtor padrão, você não poderá declarar explicitamente a coleção como um elemento de objeto. Alguns autores de marcação podem preferir ver a coleção explícita como uma questão de estilo de marcação. Além disso, um construtor padrão pode simplificar as exigências de inicialização ao criar novos objetos que usam o tipo de coleção como valor de propriedade.  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>Declarando propriedades de conteúdo XAML  
 A linguagem XAML define o conceito de uma propriedade de conteúdo do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Cada classe que é útil na sintaxe de objetos pode ter exatamente uma propriedade de conteúdo XAML. Para declarar uma propriedade para ser a propriedade de conteúdo XAML para a sua classe, aplique o <xref:System.Windows.Markup.ContentPropertyAttribute> como parte da definição de classe. Especifique o nome da propriedade conteúdo XAML desejado como o <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A> no atributo. A propriedade é especificada como uma cadeia de caracteres por nome, não como um constructo de reflexão, como <xref:System.Reflection.PropertyInfo>.  
  
 Você pode especificar uma propriedade de coleção para ser a propriedade de conteúdo XAML. Isso resulta em um uso para a propriedade em que o elemento de objeto pode ter um ou mais elementos filho, sem nenhum elemento de objeto de coleção interveniente ou marcas de elemento de propriedade. Em seguida, esses elementos são tratados como o valor da propriedade de conteúdo XAML e adicionados à instância de coleção de suporte.  
  
 Algumas propriedades de conteúdo XAML existentes usam o tipo de propriedade de `Object`. Isso permite que um XAML conteúdo de valores de propriedade que pode levar primitiva, como um <xref:System.String> , bem como utilizar um valor de objeto de referência único. Se você seguir esse modelo, seu tipo será responsável pela determinação de tipo, bem como pela manipulação de tipos possíveis. A razão típica para uma <xref:System.Object> conteúdo de tipo deve dar suporte a um meio simple de adicionar conteúdo de objeto como uma cadeia de caracteres (que recebe um tratamento de apresentação padrão) ou um meio avançado de adicionar conteúdo de objeto que especifica uma apresentação não padrão ou dados adicionais.  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>Serialização de XAML  
 Para alguns cenários, como se você fosse um autor de controle, você poderia querer garantir que qualquer representação de objeto que possa ser instanciada em XAML também possa ser serializada para marcação XAML equivalente. As exigências de serialização não são descritas neste tópico. Consulte [Visão geral da criação de controle](../../../../docs/framework/wpf/controls/control-authoring-overview.md) e [Árvore de elementos e serialização](../../../../docs/framework/wpf/advanced/element-tree-and-serialization.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Propriedades de dependência personalizada](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Visão geral da criação de controle](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Visão geral de elementos base](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [Carregamento de XAML e propriedades da dependência](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)
