---
title: Visão geral do XAML
description: Saiba como a linguagem XAML é estruturada e implementada pelo Windows Presentation Foundation (WPF) para .NET Core.
author: thraka
ms.date: 08/08/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interfaces [XAML]
- classes [XAML]
- root element [XAML]
- XAML [WPF], about XAML
- base classes [XAML]
- routed events [WPF]
- code-behind files [WPF], XAML
- collection properties [XAML]
- events [XAML]
- property element [XAML]
- content models [XAML]
- Extensible Application Markup Language (see XAML)
- attribute syntax [XAML]
ms.openlocfilehash: b0a9357b623fbde08731a5b1ddb8fee3a93824c2
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "82071783"
---
# <a name="xaml-overview-in-wpf"></a>Visão geral do XAML no WPF

Este artigo descreve os recursos da linguagem XAML e demonstra como você pode usar xaml para escrever aplicativos do Windows Presentation Foundation (WPF). Este artigo descreve especificamente o XAML como implementado pela WPF. XAML em si é um conceito de linguagem maior do que o WPF.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-xaml"></a>O que é XAML

O XAML é uma linguagem de marcação declarativa. Como aplicado ao modelo de programação .NET Core, o XAML simplifica a criação de uma iu para um aplicativo .NET Core. Você pode criar elementos de interface do usuário visíveis na marcação XAML declarativa e, em seguida, separar a definição de Interface do Usuário da lógica de tempo de execução usando arquivos de código atrás que são unidos à marcação através de definições parciais de classe. O XAML representa diretamente a instanciação de objetos em um conjunto específico de tipos de suporte definidos em assemblies. Isso é diferente da maioria das outras linguagens de marcação, que são geralmente uma linguagem interpretada sem um vínculo direto para um sistema de tipos de suporte. O XAML permite um fluxo de trabalho onde partes separadas podem trabalhar na ui e na lógica de um aplicativo, usando ferramentas potencialmente diferentes.

Quando representados como texto, arquivos XAML são arquivos XML que geralmente tem a extensão `.xaml`. Os arquivos podem ser codificados por qualquer codificação XML, mas a codificação como UTF-8 é a usual.

O exemplo a seguir mostra como você pode criar um botão como parte de uma ui. Este exemplo é destinado a dar-lhe um sabor de como xaml representa metáforas comuns de programação de iu (não é uma amostra completa).

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

## <a name="xaml-syntax-in-brief"></a>Sintaxe XAML em breve

As seções a seguir explicam as formas básicas de sintaxe XAML e fornecem um exemplo de marcação curta. Essas seções não se destinam a fornecer informações completas sobre cada forma de sintaxe, por exemplo, de como esses itens são representados no sistema de tipos de suporte. Para obter mais informações sobre as especificidades da sintaxe XAML, consulte [XAML Sintaxe em detalhes](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

Grande parte do material nas próximas seções será elementar para você se você tiver familiaridade prévia com a linguagem XML. Isso é consequência de um dos princípios básicos de design do XAML. A linguagem XAML define conceitos próprios, mas esses conceitos funcionam dentro da linguagem XML e forma de marcação.

### <a name="xaml-object-elements"></a>Elementos do objeto XAML

Normalmente, um elemento de objeto declara uma instância de um tipo. Esse tipo é definido nos conjuntos referenciados pela tecnologia que usa XAML como linguagem.

A sintaxe de elemento de objeto sempre começa com um colchete de abertura (`<`). Isso é seguido pelo nome do tipo em que você deseja criar uma instância. (O nome pode incluir um prefixo, um conceito que será explicado posteriormente.) Depois disso, você pode, opcionalmente, declarar atributos no elemento objeto. Para completar a tag do elemento objeto,`>`termine com um suporte de ângulo de fechamento (). Em vez disso, você pode usar uma forma de auto-fechamento que não tenha qualquer conteúdo, completando a tag com uma barra para a frente e fechando o suporte de ângulo em sucessão ().`/>` Por exemplo, olhe para o trecho de marcação mostrado anteriormente novamente.

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

Isso especifica dois elementos de objeto: `<StackPanel>` (com conteúdo e, posteriormente, uma marca de fechamento) e `<Button .../>` (o formulário de autofechamento, com vários atributos). Os elementos do `StackPanel` objeto e `Button` cada mapa para o nome de uma classe que é definida pelo WPF e faz parte das assembléias do WPF. Quando você especifica uma tag de elemento de objeto, você cria uma instrução para processamento XAML para criar uma nova instância do tipo subjacente. Cada instância é criada chamando o construtor sem parâmetros do tipo subjacente ao analisar e carregar o XAML.

### <a name="attribute-syntax-properties"></a>Sintaxe de atributos (propriedades)

As propriedades de um objeto geralmente podem ser expressas como atributos do elemento de objeto. A sintaxe de atributo nomeia a propriedade do objeto que está sendo definida, seguida pelo operador de atribuição (=). O valor de um atributo é sempre especificado como uma cadeia de caracteres entre aspas.

A sintaxe de atributo é a sintaxe de configuração de propriedade mais simplificada e é a sintaxe mais intuitiva para os desenvolvedores que já usaram linguagens de marcação anteriormente. Por exemplo, a marcação a seguir cria um botão com texto vermelho e uma tela de fundo azul, além de texto de exibição especificado como `Content`.

[!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]

### <a name="property-element-syntax"></a>Sintaxe de elemento sionitivo de propriedade

Para algumas propriedades de um elemento de objeto, a sintaxe de atributo não é possível porque o objeto ou as informações necessárias para fornecer o valor da propriedade não podem ser expressos adequadamente dentro das restrições de aspas e cadeias de caracteres da sintaxe de atributo. Nesses casos é possível usar uma sintaxe diferente, conhecida como sintaxe de elemento de propriedade.

A sintaxe para a `<TypeName.PropertyName>`tag de início do elemento de propriedade é . Geralmente, o conteúdo dessa tag é um elemento objeto do tipo que a propriedade toma como seu valor. Depois de especificar o conteúdo, você deve fechar o elemento de propriedade com uma tag final. A sintaxe para `</TypeName.PropertyName>`a tag final é .

Se uma sintaxe de atributo é possível, usá-la é normalmente mais conveniente e permite uma marcação mais compacta, mas isso geralmente é apenas uma questão de estilo e não uma limitação técnica. O exemplo a seguir mostra as mesmas propriedades que foram definidas no exemplo de sintaxe de atributo anterior sendo definidas novamente, mas desta vez usando sintaxe de elemento de propriedade para todas as propriedades do `Button`.

[!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]

### <a name="collection-syntax"></a>Sintaxe de coleção

A linguagem XAML inclui algumas otimizações que produzem uma marcação mais legível. Uma otimização desse tipo é tal que, se uma determinada propriedade utiliza um tipo de coleção, os itens que você declara na marcação como elementos filho no valor dessa propriedade tornam-se parte da coleção. Nesse caso, uma coleção de elementos de objeto filho é o valor que está sendo definido para a propriedade de coleção.

O exemplo a seguir mostra a sintaxe de cobrança para definir os <xref:System.Windows.Media.GradientBrush.GradientStops%2A> valores da propriedade.

```xaml
<LinearGradientBrush>
  <LinearGradientBrush.GradientStops>
    <!-- no explicit new GradientStopCollection, parser knows how to find or create -->
    <GradientStop Offset="0.0" Color="Red" />
    <GradientStop Offset="1.0" Color="Blue" />
  </LinearGradientBrush.GradientStops>
</LinearGradientBrush>
```

### <a name="xaml-content-properties"></a>Propriedades de conteúdo XAML

XAML especifica um recurso de idioma pelo qual uma classe pode designar exatamente uma de suas propriedades para ser a propriedade _de conteúdo_ XAML. Elementos filho desse elemento de objeto são usados para definir o valor dessa propriedade de conteúdo. Em outras palavras, para a propriedade de conteúdo exclusivamente, você pode omitir um elemento de propriedade ao definir essa propriedade na marcação XAML e produzir uma metáfora de pai/filho mais visível na marcação.

Por exemplo, <xref:System.Windows.Controls.Border> especifica uma <xref:System.Windows.Controls.Decorator.Child%2A>propriedade de _conteúdo_ de . Os dois <xref:System.Windows.Controls.Border> elementos a seguir são tratados de forma idêntica. O primeiro aproveita a sintaxe de propriedade de conteúdo e omite o elemento de propriedade `Border.Child`. O segundo mostra `Border.Child` explicitamente.

```xaml
<Border>
  <TextBox Width="300"/>
</Border>
<!--explicit equivalent-->
<Border>
  <Border.Child>
    <TextBox Width="300"/>
  </Border.Child>
</Border>
```

Como uma regra da linguagem XAML, o valor de uma propriedade de conteúdo XAML deve ser fornecido inteiramente antes ou inteiramente depois de todos os outros elementos de propriedade nesse elemento de objeto. Por exemplo, a marcação a seguir não compila.

```xaml
<Button>I am a
  <Button.Background>Blue</Button.Background>
  blue button</Button>
```

Para obter mais informações sobre as especificidades da sintaxe XAML, consulte [XAML Sintaxe em detalhes](../../framework/wpf/advanced/xaml-syntax-in-detail.md).

### <a name="text-content"></a>Conteúdo de texto

Um número pequeno de elementos XAML pode processar texto diretamente como seu conteúdo. Para habilitar isso, um dos casos a seguir deve ser verdadeiro:

- A classe deve declarar uma propriedade de conteúdo, e essa propriedade de conteúdo deve <xref:System.Object>ser de um tipo atribuído a uma string (o tipo poderia ser ). Por exemplo, <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.ContentControl.Content%2A> qualquer uso como propriedade <xref:System.Object>de conteúdo e é tipo <xref:System.Windows.Controls.ContentControl> , e <xref:System.Windows.Controls.Button> `<Button>Hello</Button>`isso suporta o seguinte uso em um tal como: .

- O tipo deve declarar um conversor de tipo e, nesse caso, o conteúdo de texto é usado como texto de inicialização para esse conversor de tipo. Por exemplo, `<Brush>Blue</Brush>` converte o `Blue` valor de conteúdo de em um pincel. Esse caso é menos comum na prática.

- O tipo deve ser um primitivo conhecido de linguagem XAML.

### <a name="content-properties-and-collection-syntax-combined"></a>Propriedades de conteúdo e sintaxe de coleta combinadas

Considere este exemplo.

```xaml
<StackPanel>
  <Button>First Button</Button>
  <Button>Second Button</Button>
</StackPanel>
```

Aqui, <xref:System.Windows.Controls.Button> cada um é <xref:System.Windows.Controls.StackPanel>um elemento infantil de . Isso é uma marcação otimizada e intuitiva que omite duas marcas por dois motivos diferentes.

- **Omitido StackPanel.Children elemento de propriedade:** <xref:System.Windows.Controls.StackPanel> deriva de <xref:System.Windows.Controls.Panel>. <xref:System.Windows.Controls.Panel>define <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> como sua propriedade de conteúdo XAML.

- **Elemento objeto UIElementCollection omitido:** A <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> propriedade leva <xref:System.Windows.Controls.UIElementCollection>o tipo <xref:System.Collections.IList>, que implementa . A tag de elementos da coleção pode ser omitida, com <xref:System.Collections.IList>base nas regras xaml para processamento de coleções como . (Neste caso, <xref:System.Windows.Controls.UIElementCollection> na verdade, não pode ser instanciado porque não expõe um <xref:System.Windows.Controls.UIElementCollection> construtor sem parâmetros, e é por isso que o elemento objeto é mostrado comentado).

```xaml
<StackPanel>
  <StackPanel.Children>
    <!--<UIElementCollection>-->
    <Button>First Button</Button>
    <Button>Second Button</Button>
    <!--</UIElementCollection>-->
  </StackPanel.Children>
</StackPanel>
```

### <a name="attribute-syntax-events"></a>Sintaxe de atributos (eventos)

A sintaxe de atributo também pode ser usada para os membros que são eventos, em vez de propriedades. Nesse caso, o nome do atributo é o nome do evento. A implementação de WPF de eventos para XAML, o valor do atributo é o nome de um manipulador que implementa o delegado do evento. Por exemplo, a marcação a seguir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> atribui <xref:System.Windows.Controls.Button> um manipulador para o evento a uma criação na marcação:

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

Há muito mais envolvido no uso de eventos e XAML no WPF do que apenas esse exemplo da sintaxe de atributo. Por exemplo, você talvez esteja se perguntando o que o `ClickHandler` referenciado aqui representa e como ele está definido. Isso será explicado na próxima seção [de Eventos e códigoxaml](#events-and-xaml-code-behind) deste artigo.

## <a name="case-and-white-space-in-xaml"></a>Caixa e espaço em branco em XAML

Em geral, o XAML é sensível a casos. Para fins de resolução de tipos de apoio, o WPF XAML é sensível a maiúsculas e minúsculas pelas mesmas regras que a CLR é sensível a casos. Elementos de objeto, elementos de propriedade e nomes de atributo devem ser especificados usando diferenciação de maiúsculas e minúsculas quando comparados pelo nome ao tipo subjacente no assembly ou a um membro de um tipo. Palavras-chave da linguagem XAML e primitivos também são sensíveis a maiúsculas e minúsculas. Valores nem sempre são sensíveis a maiúsculas e minúsculas. A diferenciação de maiúsculas e minúsculas em valores dependerá do comportamento do conversor de tipo associado com a propriedade que recebe o valor ou do tipo de valor da propriedade. Por exemplo, propriedades <xref:System.Boolean> que tomam `true` o `True` tipo podem tomar valores equivalentes, mas apenas porque a <xref:System.Boolean> conversão nativa do tipo de analisador WPF XAML para string já permite isso como equivalentes.

Os processadores E serializadores WPF XAML ignorarão ou soltarão todo o espaço branco não significativo e normalizarão qualquer espaço branco significativo. Isso é consistente com as recomendações padrão de comportamento em espaço branco da especificação XAML. Esse comportamento só é conseqüência quando você especifica strings dentro de propriedades de conteúdo XAML. Em termos mais simples, xAML converte caracteres de espaço, linefeed e tab em espaços e, em seguida, preserva um espaço se encontrado em qualquer extremidade de uma seqüência contígua. A explicação completa do manuseio do espaço branco XAML não está coberta neste artigo. Para obter mais informações, consulte [o processamento de espaço branco em XAML](../xaml-services/white-space-processing.md).

## <a name="markup-extensions"></a>Extensões de marcação

Extensões de marcação são um conceito de linguagem XAML. Quando usados para fornecer o valor de uma sintaxe de atributo, chaves (`{` e `}`) indicam um uso de extensão de marcação. Esse uso direciona o processamento XAML para escape do tratamento geral de valores de atributo como uma cadeia de caracteres literal ou um valor conversível em cadeia de caracteres.

As extensões de marcação mais comuns [`Binding`](../../framework/wpf/advanced/binding-markup-extension.md)usadas na programação de aplicativos WPF [`StaticResource`](../../framework/wpf/advanced/staticresource-markup-extension.md) são, usadas para expressões de vinculação de dados, e as referências de recursos e [`DynamicResource`](../../framework/wpf/advanced/dynamicresource-markup-extension.md). Usando extensões de marcação, você pode usar a sintaxe de atributo para fornecer valores para propriedades mesmo que essas propriedades não deem suporte a uma sintaxe de atributo em geral. As extensões de marcação geralmente usam tipos de expressão intermediários para habilitar recursos como adiar valores ou referenciar outros objetos que só estão presentes no tempo de execução.

Por exemplo, a marcação a <xref:System.Windows.FrameworkElement.Style%2A> seguir define o valor da propriedade usando sintaxe de atributo. A <xref:System.Windows.FrameworkElement.Style%2A> propriedade toma uma <xref:System.Windows.Style> instância da classe, que por padrão não poderia ser instanciada por uma seqüência de sintaxe de atributo. Mas, neste caso, o atributo faz `StaticResource`referência a uma extensão de marcação específica, . Quando essa extensão de marcação é processada, ela retorna uma referência a um estilo que foi anteriormente instanciado como um recurso com chave em um dicionário de recursos.

[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]

Para uma referência listando todas as extensões de marcação para XAML implementado especificamente no WPF, consulte [Extensões XAML WPF](../../framework/wpf/advanced/wpf-xaml-extensions.md). Para obter uma lista de referência das extensões de marcação definidas pelo System.Xaml e mais amplamente disponíveis para implementações do .NET Core XAML, consulte [XAML Namespace (x:) Características do idioma](../xaml-services/namespace-language-features.md). Para obter mais informações sobre conceitos de extensão de marcação, consulte [Extensões de marcação e XAML WPF](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

## <a name="type-converters"></a>Conversores de tipo

Na seção [Resumo sobre sintaxe XAML](#xaml-syntax-in-brief), foi mencionado que o valor do atributo deve poder ser definido por uma cadeia de caracteres. O manuseio básico e nativo de como as strings são convertidas <xref:System.String> em outros tipos de objetoou valores <xref:System.DateTime> primitivos baseia-se no próprio tipo, além do processamento nativo para determinados tipos, tais como ou <xref:System.Uri>. Mas muitos tipos de WPF ou membros desses tipos estendem o comportamento básico de processamento de atributos de cadeia de tal forma que instâncias de tipos de objetos mais complexos podem ser especificadas como strings e atributos.

A <xref:System.Windows.Thickness> estrutura é um exemplo de um tipo que tem uma conversão de tipo habilitada para usos XAML. <xref:System.Windows.Thickness>indica medidas dentro de um retângulo aninhado e <xref:System.Windows.FrameworkElement.Margin%2A>é usado como valor para propriedades como . Ao colocar um <xref:System.Windows.Thickness>conversor de tipo, todas as propriedades que usam a são mais fáceis de <xref:System.Windows.Thickness> especificar em XAML porque podem ser especificadas como atributos. O exemplo a seguir usa uma conversão de tipo <xref:System.Windows.FrameworkElement.Margin%2A>e sintaxe de atributos para fornecer um valor para:

[!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]

O exemplo anterior de sintaxe de atributo é equivalente ao <xref:System.Windows.FrameworkElement.Margin%2A> seguinte exemplo de sintaxe <xref:System.Windows.Thickness> mais verbosa, onde o é definido através de sintaxe de elemento de propriedade contendo um elemento objeto. As quatro propriedades-chave de <xref:System.Windows.Thickness> são definidas como atributos na nova instância:

[!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]

> [!NOTE]
> Há também um número limitado de objetos onde a conversão de tipo é a única maneira pública de definir uma propriedade para esse tipo sem envolver uma subclasse, porque o tipo em si não tem um construtor sem parâmetros. Um exemplo é <xref:System.Windows.Input.Cursor>.

Para obter mais informações sobre a conversão de tipos, consulte [TypeConverters e XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md).

## <a name="xaml-root-elements-and-xaml-namespaces"></a>Elementos radiculares XAML e espaços de nomes XAML

Um arquivo XAML deve ter apenas um elemento raiz, a fim de ser tanto um arquivo XML bem formado quanto um arquivo XAML válido. Para cenários típicos de WPF, você usa um elemento raiz que <xref:System.Windows.Window> tem <xref:System.Windows.Controls.Page> um significado <xref:System.Windows.ResourceDictionary> proeminente no modelo <xref:System.Windows.Application> de aplicativo WPF (por exemplo, ou para uma página, para um dicionário externo ou para a definição do aplicativo). O exemplo a seguir mostra o elemento raiz de um arquivo XAML <xref:System.Windows.Controls.Page>típico para uma página WPF, com o elemento raiz de .

[!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]

O elemento raiz também contém os atributos `xmlns` e `xmlns:x`. Esses atributos indicam a um processador XAML quais namespaces XAML contêm as definições de tipo para tipos de suporte que a marcação referenciará como elementos. O atributo `xmlns` indica especificamente o namespace XAML padrão. Dentro do namespace XAML padrão, os elementos de objeto na marcação podem ser especificados sem um prefixo. Para a maioria dos cenários de aplicativos WPF, e para quase todos os exemplos dados nas seções WPF do SDK, o namespace XAML padrão é mapeado para o namespace do WPF `http://schemas.microsoft.com/winfx/2006/xaml/presentation`. O atributo `xmlns:x` indica um namespace XAML adicional, que mapeia o namespace `http://schemas.microsoft.com/winfx/2006/xaml` da linguagem XAML.

Esse uso de `xmlns` para definir um escopo para uso e mapeamento de um namescope é consistente com a especificação do XML 1.0. Namescopes XAML são diferentes de namescopes XML apenas porque um namescope XAML também implica algo sobre como os elementos do namescope têm suporte de tipos quando se trata de resolução de tipo e análise do XAML.

Os `xmlns` atributos são estritamente necessários no elemento raiz de cada arquivo XAML. As definições do `xmlns` serão aplicadas a todos os elementos descendentes do elemento raiz (esse comportamento é novamente consistente com a especificação XML 1.0 para `xmlns`). Atributos `xmlns` também são permitidos em outros elementos abaixo da raiz e se aplicariam a quaisquer elementos descendentes do elemento definidor. No entanto, definição ou redefinição frequente de namespaces XAML pode resultar em um estilo de marcação XAML difícil de ler.

A implementação do WPF do seu processador XAML inclui uma infra-estrutura que tem consciência dos conjuntos principais wpf. Os conjuntos de núcleos Do WPF são conhecidos por conter os tipos que suportam os mapeamentos WPF para o namespace XAML padrão. Isso é habilitado por meio da configuração que faz parte de seu arquivo de build do projeto e dos sistemas de projeto e build do WPF. Portanto, declarar o namespace XAML padrão `xmlns` como padrão é tudo o que é necessário para referenciar elementos XAML que vêm de conjuntos WPF.

### <a name="the-x-prefix"></a>O x: prefixo

No exemplo de elemento raiz anterior, o prefixo `x:` foi usado para mapear o namespace XAML `http://schemas.microsoft.com/winfx/2006/xaml`, que é o namespace XAML dedicado que dá suporte a constructos de linguagem XAML. Este `x:` prefixo é usado para mapear este namespace XAML nos modelos para projetos, em exemplos e na documentação ao longo deste SDK. O namespace XAML para a linguagem XAML contém várias construções de programação que você usará com freqüência em seu XAML. A seguir está uma lista dos constructos de programação de prefixo `x:` mais comuns que você usará:

- [x:Chave](../xaml-services/xkey-directive.md): Define uma chave única <xref:System.Windows.ResourceDictionary> para cada recurso em um (ou conceitos de dicionário semelhantes em outras estruturas). `x:Key`provavelmente responderá por 90% dos `x:` usos que você verá na marcação de um aplicativo WPF típico.

- [x:Classe](../xaml-services/xclass-directive.md): Especifica o namespace clr e o nome da classe para a classe que fornece código atrás para uma página XAML. Você deve ter uma classe desse tipo para dar suporte a code-behind segundo o modelo de programação do WPF e, portanto, você quase sempre vê `x:` mapeado, mesmo que não existam recursos.

- [X:Name](../xaml-services/xname-directive.md): especifica um nome de objeto de tempo de execução para a instância que existe em código de tempo de execução após o processamento de um elemento de objeto. Em geral, você usará frequentemente uma propriedade equivalente definida pelo WPF para [X:Name](../xaml-services/xname-directive.md). Essas propriedades mapeiam especificamente para uma propriedade de suporte CLR e, portanto, são mais convenientes para a programação de aplicativos, onde você frequentemente usa código de tempo de execução para encontrar os elementos nomeados a partir de XAML inicializado. A propriedade mais <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>comum é. Você ainda pode usar [x:Nome](../xaml-services/xname-directive.md) quando a <xref:System.Windows.FrameworkElement.Name%2A> propriedade equivalente de nível de estrutura WPF não for suportada em um tipo específico. Isso ocorre em determinados cenários de animação.

- [X:Static](../xaml-services/xstatic-markup-extension.md): permite uma referência que retorna um valor estático que não é uma propriedade XAML compatível.

- [x:Tipo](../xaml-services/xtype-markup-extension.md): Constrói <xref:System.Type> uma referência com base em um nome de tipo. Isso é usado para especificar atributos <xref:System.Type>que tomam, como, <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>embora<xref:System.Type> freqüentemente a propriedade tenha string-to-conversion nativa de tal forma que o uso da extensão de marcação [x:Type](../xaml-services/xtype-markup-extension.md) seja opcional.

Há constructos de programação adicionais no prefixo `x:`/namespace XAML que não são tão comuns. Para obter detalhes, consulte [Recursos de linguagem (x:) do namespace XAML](../xaml-services/namespace-language-features.md).

## <a name="custom-prefixes-and-custom-types-in-xaml"></a>Prefixos personalizados e tipos personalizados em XAML

Para seus próprios conjuntos personalizados, ou para conjuntos fora do núcleo WPF do **PresentationCore,** `xmlns` **PresentationFramework** e **WindowsBase,** você pode especificar o conjunto como parte de um mapeamento personalizado. Você pode então referenciar tipos desse assembly em seu XAML, desde que esse tipo esteja corretamente implementado para dar suporte aos usos XAML que você está tentando executar.

A seguir, um exemplo básico de como os prefixos personalizados funcionam na marcação XAML. O `custom` prefixo é definido na tag elemento raiz e mapeado para um conjunto específico que está embalado e disponível com o aplicativo. Esse assembly contém um tipo `NumericUpDown`, que é implementado para dar suporte ao uso geral do XAML, bem como usar uma herança de classe que permite sua inserção, nesse momento específico, em um modelo de conteúdo XAML WPF. Uma instância desse controle `NumericUpDown` é declarada como um elemento de objeto, usando o prefixo para que um analisador XAML saiba qual namespace XAML contém o tipo e, portanto, a localização do assembly de suporte que contém a definição de tipo.

```xaml
<Page
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:custom="clr-namespace:NumericUpDownCustomControl;assembly=CustomLibrary"
    >
  <StackPanel Name="LayoutRoot">
    <custom:NumericUpDown Name="numericCtrl1" Width="100" Height="60"/>
...
  </StackPanel>
</Page>
```

Para obter mais informações sobre tipos personalizados em XAML, consulte [XAML e classes personalizadas para WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).

Para obter mais informações sobre como os namespaces xml e os espaços de nomes de código em conjuntos estão relacionados, consulte [XAML Namespaces e Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

## <a name="events-and-xaml-code-behind"></a>Eventos e código xaml por trás

A maioria dos aplicativos WPF consiste tanto na marcação XAML quanto no code-behind. Dentro de um projeto, o XAML é escrito como um `.xaml` arquivo, e uma linguagem CLR como Microsoft Visual Basic ou C# é usada para escrever um arquivo de código atrás. Quando um arquivo XAML é compilado com marcação como parte dos modelos de aplicativos e programação WPF, o local do arquivo XAML code-behind para um arquivo XAML é identificado por meio da especificação de um namespace e classe como o atributo `x:Class` do elemento raiz do XAML.

Nos exemplos até agora você viu vários botões, mas nenhum deles tinha ainda qualquer comportamento lógico associado. O mecanismo principal de nível de aplicação para adicionar um comportamento para um elemento objeto é usar um evento existente da classe de elementos e escrever um manipulador específico para esse evento que é invocado quando esse evento é levantado em tempo de execução. O nome do evento e o nome do manipulador a usar são especificados na marcação, enquanto o código que implementa o manipulador é definido no code-behind.

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

[!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
[!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]

Observe que o arquivo code-behind usa o namespace CLR `ExampleNamespace` e declara `ExamplePage` como uma classe parcial dentro desse namespace. Isso é comparável ao valor do atributo `x:Class` de `ExampleNamespace`.`ExamplePage` que foi fornecido na raiz da marcação. O compilador de marcação do WPF criará uma classe parcial para qualquer arquivo XAML compilado, derivando uma classe do tipo de elemento raiz. Quando você fornece um código-trás que também define a mesma classe parcial, o código resultante é combinado dentro do mesmo namespace e classe do aplicativo compilado.

Para obter mais informações sobre os requisitos para programação de código atrás no WPF, consulte [Code-behind, Event Handler e Partial Class Requirements in WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md#code-behind-event-handler-and-partial-class-requirements-in-wpf).

Se você não deseja criar um arquivo code-behind separado, você também pode embutir seu código em um arquivo XAML. No entanto, o código embutido é uma técnica menos versátil que tem limitações significativas. Para obter mais informações, consulte [Code-Behind e XAML em WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

### <a name="routed-events"></a>Eventos roteados

Um recurso de evento em particular que é fundamental para o WPF é um evento roteado. Eventos roteados habilitam um elemento para manipular um evento que foi acionado por um elemento diferente, desde que os elementos estejam conectados por meio de uma relação de árvore. Ao especificar o tratamento de eventos com um atributo XAML, o evento roteado pode ser escutado e manipulado em qualquer elemento, incluindo elementos que não listam esse evento específico na tabela de membros de classe. Isso é feito qualificando o atributo de nome do evento com o nome de classe proprietária. Por exemplo, `StackPanel` o pai `StackPanel`  /  `Button` no exemplo em curso poderia registrar <xref:System.Windows.Controls.Primitives.ButtonBase.Click> um manipulador para `Button.Click` o `StackPanel` evento do botão de elemento filho especificando o atributo no elemento objeto, com o nome do manipulador como o valor do atributo. Para obter mais informações, consulte [Visão geral de eventos roteados](../../framework/wpf/advanced/routed-events-overview.md).

## <a name="xaml-named-elements"></a>Elementos nomeados xAML

Por padrão, a instância do objeto criada em um grafo de objeto pelo processamento de um elemento de objeto XAML não tem um identificador exclusivo nem uma referência de objeto. Por outro lado, se você chamar um construtor no código, você quase sempre usará o resultado do construtor para definir uma variável para a instância construída, de modo que você poderá fazer referência à instância posteriormente no seu código. Para oferecer acesso padronizado a objetos que criados por meio de uma definição de marcação, o XAML define o [atributo X:Name](../xaml-services/xname-directive.md). Você pode definir o valor do atributo `x:Name` em qualquer elemento de objeto. Em seu code-behind, o identificador escolhido é equivalente a uma variável de instância que faz referência à instância construída. Em todos os aspectos, os elementos nomeados funcionam como se fossem instâncias de objeto (o nome faz referência a essa instância), e seu código atrás pode referenciar os elementos nomeados para lidar com interações em tempo de execução dentro do aplicativo. Essa conexão entre instâncias e variáveis é realizada pelo compilador de marcação WPF XAML, e envolve mais especificamente recursos e padrões como <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> esse que não serão discutidos detalhadamente neste artigo.

Os elementos XAML de <xref:System.Windows.FrameworkElement.Name%2A> nível de estrutura WPF herdam uma propriedade, que é equivalente ao atributo definido por `x:Name` XAML. Algumas outras classes também fornecem equivalentes de nível de propriedade para `x:Name`, que também geralmente é definido como uma propriedade `Name`. Em termos gerais, se você não encontrar uma propriedade `Name` na tabela de membros de seu elemento/tipo escolhido, use `x:Name` em vez disso. Os `x:Name` valores fornecerão um identificador para um elemento XAML que pode ser usado em tempo <xref:System.Windows.FrameworkElement.FindName%2A>de execução, seja por subsistemas específicos ou por métodos utilitários como .

O exemplo <xref:System.Windows.FrameworkElement.Name%2A> a <xref:System.Windows.Controls.StackPanel> seguir se baseia em um elemento. Em seguida, um <xref:System.Windows.Controls.Button> manipulador <xref:System.Windows.Controls.StackPanel> em <xref:System.Windows.Controls.StackPanel> um interior `buttonContainer` que faz <xref:System.Windows.FrameworkElement.Name%2A>referência à referência de instância definida por .

[!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]

[!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
[!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]

Assim como uma variável, o nome XAML para uma instância é regido por um conceito do escopo, de modo que pode ser imposto que os nomes sejam exclusivos dentro de um determinado escopo previsível. A marcação primária que define uma página denota um namescope XAML exclusivo, com o limite de namescopes XAML sendo o elemento raiz dessa página. No entanto, outras fontes de marcação podem interagir com uma página em tempo de execução, como estilos ou modelos dentro de estilos, e essas fontes de marcação geralmente têm seus próprios namescopes XAML que não necessariamente se conectam com o namescope XAML da página. Para obter `x:Name` mais informações sobre e namescopes XAML, consulte <xref:System.Windows.FrameworkElement.Name%2A>, [x:Diretiva de nome](../xaml-services/xname-directive.md)ou [Namescopes WPF XAML](../../framework/wpf/advanced/wpf-xaml-namescopes.md).

## <a name="attached-properties-and-attached-events"></a>Propriedades anexadas e eventos anexados

O XAML Especifica um recurso de linguagem que permite que determinadas propriedades ou eventos sejam especificados em qualquer elemento, independentemente de a propriedade ou evento existir nas definições do tipo para o elemento em que ele está sendo definido. A versão de propriedades desse recurso é chamada de uma propriedade anexada, a versão de eventos é chamada de um evento anexado. Conceitualmente, você pode pensar em propriedades anexadas e eventos anexados como membros globais que podem ser definidos em qualquer instância de objeto/elemento XAML. No entanto, esse elemento/classe ou uma infraestrutura maior deve dar suporte a um repositório de propriedades de suporte para os valores anexados.

Propriedades anexadas em XAML normalmente são usadas por meio da sintaxe de atributo. Na sintaxe de atributos, você `ownerType.propertyName`especifica uma propriedade anexada no formulário .

Superficialmente, isso se assemelha a um uso `ownerType` de elemento de propriedade, mas neste caso o que você especifica é sempre um tipo diferente do elemento objeto onde a propriedade anexada está sendo definida. `ownerType`é o tipo que fornece os métodos de acessório que são exigidos por um processador XAML para obter ou definir o valor da propriedade anexada.

O cenário mais comum para propriedades anexadas é habilitar que elementos filho relatem um valor da propriedade para o respectivo elemento pai.

O exemplo a <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> seguir ilustra a propriedade anexada. A <xref:System.Windows.Controls.DockPanel> classe define os <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> acessórios para e, portanto, possui a propriedade anexada. A <xref:System.Windows.Controls.DockPanel> classe também inclui a lógica que itera seus elementos infantis <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>e verifica especificamente cada elemento para obter um valor definido de . Se um valor for encontrado, esse valor será usado durante o layout para posicionar os elementos filho. O uso <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> da propriedade anexada e dessa capacidade de <xref:System.Windows.Controls.DockPanel> posicionamento é, de fato, o cenário motivador para a classe.

[!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]

No WPF, a maioria ou todas as propriedades anexadas também são implementadas como propriedades de dependência. Para obter mais informações, consulte [Visão geral das propriedades anexadas](../../framework/wpf/advanced/attached-properties-overview.md).

Eventos anexados usam `ownerType.eventName` uma forma semelhante de sintaxe de atributo. Assim como nos eventos não anexados, o valor do atributo para um evento anexado em XAML especifica o nome do método manipulador que é invocado quando o evento é manipulado no elemento. Usos de evento anexado no XAML WPF são menos comuns. Para obter mais informações, consulte [Visão geral de eventos anexados](../../framework/wpf/advanced/attached-events-overview.md).

## <a name="base-types-and-xaml"></a>Tipos de base e XAML

O WPF XAML subjacente e seu namespace XAML é uma coleção de tipos que correspondem a objetos CLR, além de elementos de marcação para XAML. No entanto, nem todas as classes podem ser mapeadas para elementos. Classes abstratas, <xref:System.Windows.Controls.Primitives.ButtonBase>como , e certas classes de base não abstratas, são usadas para herança no modelo de objetos CLR. Classes base, incluindo aquelas abstratas, são importantes para o desenvolvimento de XAML, porque cada um dos elementos XAML concretos herda os membros de alguma classe base na sua hierarquia. Frequentemente esses membros incluem propriedades que podem ser definidas como atributos no elemento ou eventos que podem ser manipulados. <xref:System.Windows.FrameworkElement>é a classe ui base concreta da WPF no nível de estrutura wpf. Ao projetar a ui, você usará várias classes de forma, painel, decorador ou controle, que todas derivam <xref:System.Windows.FrameworkElement>. Uma classe base <xref:System.Windows.FrameworkContentElement>relacionada, suporta elementos orientados a documentos que funcionam bem para uma apresentação <xref:System.Windows.FrameworkElement>de layout de fluxo, usando APIs que deliberadamente espelham as APIs em . A combinação de atributos no nível do elemento e um modelo de objeto CLR fornece-lhe um conjunto de propriedades comuns que são definidas na maioria dos elementos XAML concretos, independentemente do elemento XAML específico e seu tipo subjacente.

## <a name="xaml-security"></a>Segurança XAML

XAML é uma linguagem de marcação que representa diretamente a instanciação e execução de objetos. Portanto, elementos criados em XAML têm a mesma capacidade que o código gerado equivalente no que se refere a interagir com recursos de sistema (acesso a rede e E/S do sistema de arquivos, por exemplo). O XAML carregado em um aplicativo totalmente confiável tem o mesmo acesso aos recursos do sistema que o aplicativo de hospedagem.

### <a name="code-access-security-cas-in-wpf"></a>Segurança de acesso de código (CAS) no WPF

**Esta seção só se aplica ao .NET Framework. O WPF para .NET Core não suporta CAS. Para obter mais informações, consulte [diferenças de segurança de acesso ao código](../migration/differences-from-net-framework.md#code-access-security).**

O WPF for .NET Framework suporta o Cas (Code Access Security, segurança de acesso ao código). Isso significa que o conteúdo do WPF em execução na região da internet reduziu as permissões de execução. "Loose XAML" (páginas de XAML não compiladas interpretadas na hora da carga por um visualizador XAML) e XBAP geralmente são executadas nesta zona de internet e usam o mesmo conjunto de permissões. No entanto, o XAML carregado em um aplicativo totalmente confiável tem o mesmo acesso aos recursos de sistema que o aplicativo host. Para obter mais informações, consulte [Segurança parcialmente confiável do WPF](../../framework/wpf/wpf-partial-trust-security.md).

## <a name="loading-xaml-from-code"></a>Carregando XAML do código

XAML pode ser usado para definir toda a interface do usuário, mas às vezes também é apropriado definir apenas uma parte da interface do usuário em XAML. Essa funcionalidade pode ser usada para habilitar personalização parcial, armazenamento local de informações, uso do XAML para fornecer um objeto comercial ou uma variedade de cenários possíveis. A chave para esses <xref:System.Windows.Markup.XamlReader> cenários <xref:System.Windows.Markup.XamlReader.Load%2A> é a classe e seu método. A entrada é um arquivo XAML e a saída é um objeto que representa toda a árvore de objetos em tempo de execução que foi criada com base nessa marcação. Em seguida, você pode inserir o objeto como propriedade de outro objeto que já existe no aplicativo. Desde que a propriedade seja uma propriedade apropriada no modelo de conteúdo que tenha eventuais recursos de exibição e que notifique o mecanismo de execução de que o novo conteúdo foi adicionado ao aplicativo, você pode modificar facilmente o conteúdo de um aplicativo em execução carregando em XAML. Para o .NET Framework, esse recurso geralmente só está disponível em aplicativos de confiança total, devido às óbvias implicações de segurança de carregar arquivos em aplicativos à medida que eles são executados.

## <a name="see-also"></a>Confira também

- [Sintaxe XAML em detalhes](../../framework/wpf/advanced/xaml-syntax-in-detail.md)
- [XAML e classes personalizadas para WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Namespace XAML (x:) Funcionalidades de linguagem](../xaml-services/namespace-language-features.md)
- [Extensões XAML WPF](../../framework/wpf/advanced/wpf-xaml-extensions.md)
- [Visão geral de elementos base](../../framework/wpf/advanced/base-elements-overview.md)
- [Árvores no WPF](../../framework/wpf/advanced/trees-in-wpf.md)
