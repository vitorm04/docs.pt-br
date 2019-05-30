---
title: 'Suporte do .NET Framework para aplicativos da Windows Store e Windows Runtime '
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Windows Store apps, .NET Framework support for
- Windows Runtime, .NET Framework support for
- .NET for Windows Store apps
- .NET Framework, and Windows Store apps
- .NET Framework, and Windows Runtime
ms.assetid: 6fa7d044-ae12-4c54-b8ee-50915607a565
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45e28ebb9319447f2e1ae98f1de883f90840720f
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378294"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Suporte do .NET Framework para aplicativos da Windows Store e Windows Runtime 
O .NET Framework 4.5 oferece suporte a vários cenários de desenvolvimento de software com o [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Esses cenários se enquadram em três categorias:

- Desenvolvendo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos com controles XAML, conforme descrito em [aplicativos de roteiro para Windows Store usando c# ou Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10)), [como tos (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10)), e [visão geral de aplicativos .NET para Windows Store ](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

- Desenvolvimento de bibliotecas de classes para usar no [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos que você cria com o .NET Framework.

- Desenvolvendo [!INCLUDE[wrt](../../../includes/wrt-md.md)] componentes, empacotados em. Arquivos WinMD, que podem ser usados por qualquer linguagem de programação que dá suporte a [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Por exemplo, consulte [Criando componentes do tempo de execução do Windows em c# e Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

 Este tópico descreve o suporte que o .NET Framework fornece para todas as três categorias e descreve os cenários de [!INCLUDE[wrt](../../../includes/wrt-md.md)] componentes. A primeira seção inclui informações básicas sobre a relação entre o .NET Framework e o [!INCLUDE[wrt](../../../includes/wrt-md.md)]e explica algumas Singularidades do que você pode encontrar no sistema de Ajuda e o IDE. O [segunda seção](#WindowsRuntimeComponents) aborda cenários para o desenvolvimento de [!INCLUDE[wrt](../../../includes/wrt-md.md)] componentes.

## <a name="the-basics"></a>Os conceitos básicos
 O .NET Framework oferece suporte os cenários de desenvolvimento de três listados anteriormente, fornecendo [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]e dando suporte a [!INCLUDE[wrt](../../../includes/wrt-md.md)] em si.

- [Namespaces do .NET framework e o tempo de execução do Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) fornece uma exibição simplificada das bibliotecas de classes do .NET Framework e incluem somente os tipos e membros que você pode usar para criar [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos e [!INCLUDE[wrt](../../../includes/wrt-md.md)] componentes.

    - Quando você usa o Visual Studio (Visual Studio 2012 ou posterior) para desenvolver uma [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo ou um [!INCLUDE[wrt](../../../includes/wrt-md.md)] garante que o componente, um conjunto de assemblies de referência que você vê apenas os tipos relevantes e os membros.

    - Esse conjunto de APIs simplificado é simplificado ainda mais pela remoção dos recursos que estão duplicadas dentro do .NET Framework ou que duplicar [!INCLUDE[wrt](../../../includes/wrt-md.md)] recursos. Por exemplo, ele contém apenas as versões genéricas dos tipos de coleção, e o modelo de objeto do documento XML é eliminado em favor do [!INCLUDE[wrt](../../../includes/wrt-md.md)] conjunto de APIs de XML.

    - Recursos que simplesmente encapsulam a API do sistema operacional também serão removidos, pois o [!INCLUDE[wrt](../../../includes/wrt-md.md)] é fácil chamar do código gerenciado.

     Para ler mais sobre o [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], consulte o [visão geral de aplicativos .NET para Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Para ler sobre o processo de seleção de API, consulte o [.NET para aplicativos estilo Metro](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) entrada no blog do .NET.

- O [tempo de execução do Windows](/uwp/api/) fornece elementos da interface do usuário para a compilação [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos e fornece acesso aos recursos do sistema operacional. Como o .NET Framework, o [!INCLUDE[wrt](../../../includes/wrt-md.md)] tem os metadados que permite que os compiladores c# e Visual Basic usar o [!INCLUDE[wrt](../../../includes/wrt-md.md)] bibliotecas de classes a maneira como eles usam o .NET Framework. O .NET Framework torna mais fácil de usar o [!INCLUDE[wrt](../../../includes/wrt-md.md)] , ocultando algumas diferenças:

    - Algumas diferenças de programação padrões entre o .NET Framework e o [!INCLUDE[wrt](../../../includes/wrt-md.md)], como o padrão para adicionar e remover manipuladores de eventos, estão ocultos. Você simplesmente usa o padrão do .NET Framework.

    - Algumas diferenças nos tipos comumente usados (por exemplo, tipos primitivos e coleções) ficam ocultos. Basta usar o tipo do .NET Framework, conforme discutido em [diferenças que são visíveis no IDE](#DifferencesVisibleInIDE), mais adiante neste artigo.

 A maioria das vezes, o suporte do .NET Framework para o [!INCLUDE[wrt](../../../includes/wrt-md.md)] é transparente. A próxima seção discute algumas das diferenças aparentes entre código gerenciado e o [!INCLUDE[wrt](../../../includes/wrt-md.md)].

<a name="AboutReferenceDocumentation"></a>
### <a name="the-net-framework-and-the-includewrtincludeswrt-mdmd-reference-documentation"></a>O .NET Framework e o [!INCLUDE[wrt](../../../includes/wrt-md.md)] documentação de referência
 O tempo de execução do Windows e os conjuntos de documentação do .NET Framework são separados. Se você pressionar F1 para exibir a Ajuda em um tipo ou membro, documentação de referência do conjunto apropriado de é exibida. No entanto, se você procurar por meio de [referência de tempo de execução do Windows](/uwp/api/) você pode encontrar exemplos parecem confusas:

- Tópicos como a <xref:Windows.Foundation.Collections.IIterable%601> interface não tiver a sintaxe de declaração para o Visual Basic ou c#. Em vez disso, uma anotação é exibida acima da seção de sintaxe (nesse caso, ".NET: Essa interface é exibido como System.Collections.Generic.IEnumerable\<T > "). Isso ocorre porque o .NET Framework e o [!INCLUDE[wrt](../../../includes/wrt-md.md)] fornecem funcionalidade semelhante com interfaces diferentes. Além disso, há diferenças de comportamento: `IIterable` tem uma `First` método em vez de um <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> método para retornar o enumerador. Em vez de forçá-lo a aprender uma maneira diferente de executar uma tarefa comum, o .NET Framework oferece suporte a [!INCLUDE[wrt](../../../includes/wrt-md.md)] , fazendo com que seu código gerenciado são exibidos usar o tipo que você está familiarizado com. Você não verá os `IIterable` no IDE de interface e, portanto, a única maneira de você encontrará no [!INCLUDE[wrt](../../../includes/wrt-md.md)] documentação de referência está navegando por essa documentação diretamente.

- O <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> documentação ilustra um problema intimamente relacionado: Seus tipos de parâmetro parecem ser diferentes para diferentes idiomas. Para c# e Visual Basic, os tipos de parâmetro são <xref:System.String?displayProperty=nameWithType> e <xref:System.Uri?displayProperty=nameWithType>. Novamente, isso ocorre porque o .NET Framework tem seu próprio `String` e `Uri` tipos de e para tipos tais comumente usadas, ele não faz sentido para forçar os usuários do .NET Framework para aprender uma maneira diferente de fazer as coisas. No IDE, o .NET Framework oculta correspondente [!INCLUDE[wrt](../../../includes/wrt-md.md)] tipos.

- Em alguns casos, como o <xref:Windows.UI.Xaml.GridLength> estrutura, o .NET Framework fornece um tipo com o mesmo nome, mas mais funcionalidade. Por exemplo, um conjunto de tópicos do construtor e a propriedade estão associados `GridLength`, mas eles têm blocos de sintaxe apenas do Visual Basic e c# porque os membros estão disponíveis apenas em código gerenciado. No [!INCLUDE[wrt](../../../includes/wrt-md.md)], estruturas têm apenas campos. O [!INCLUDE[wrt](../../../includes/wrt-md.md)] estrutura requer uma classe auxiliar, <xref:Windows.UI.Xaml.GridLengthHelper>, para fornecer funcionalidade equivalente. Você não verá que a classe auxiliar no IDE quando você está escrevendo o código gerenciado.

- No IDE, [!INCLUDE[wrt](../../../includes/wrt-md.md)] tipos aparecem para derivar de <xref:System.Object?displayProperty=nameWithType>. Eles parecem ter membros herdados <xref:System.Object>, tais como <xref:System.Object.ToString%2A?displayProperty=nameWithType>. Esses membros operam como fariam se os tipos, na verdade, herdada de <xref:System.Object>, e [!INCLUDE[wrt](../../../includes/wrt-md.md)] tipos podem ser convertidos em <xref:System.Object>. Essa funcionalidade é parte do que o .NET Framework dá suporte a [!INCLUDE[wrt](../../../includes/wrt-md.md)]. No entanto, se você exibir os tipos no [!INCLUDE[wrt](../../../includes/wrt-md.md)] consultar a documentação, nenhum desses membros são exibidos. A documentação para esses membros herdados aparentes é fornecida pelo <xref:System.Object?displayProperty=nameWithType> documentação de referência.

<a name="DifferencesVisibleInIDE"></a>
### <a name="differences-that-are-visible-in-the-ide"></a>Diferenças que são visíveis no IDE
 Mais programação cenários avançados, como o uso de um [!INCLUDE[wrt](../../../includes/wrt-md.md)] componente escrito em c# para fornecer a lógica do aplicativo para um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo compilado para Windows usando JavaScript, essas diferenças são aparentes no IDE, bem como a documentação. Quando o seu componente retorna um `IDictionary<int, string>` com o JavaScript e examinar o depurador do JavaScript, você verá os métodos de `IMap<int, string>` como o JavaScript usa a [!INCLUDE[wrt](../../../includes/wrt-md.md)] tipo. Alguns usados com frequência a coleção de tipos que aparecem de forma diferente em dois idiomas são mostrados na tabela a seguir:

|Tipo [!INCLUDE[wrt](../../../includes/wrt-md.md)]|Tipo correspondente do .NET Framework|
|--------------------------------------------------------------|---------------------------------------|
|`IIterable<T>`|`IEnumerable<T>`|
|`IIterator<T>`|`IEnumerator<T>`|
|`IVector<T>`|`IList<T>`|
|`IVectorView<T>`|`IReadOnlyList<T>`|
|`IMap<K, V>`|`IDictionary<TKey, TValue>`|
|`IMapView<K, V>`|`IReadOnlyDictionary<TKey, TValue>`|
|`IBindableIterable`|`IEnumerable`|
|`IBindableVector`|`IList`|
|`Windows.UI.Xaml.Data.INotifyPropertyChanged`|`System.ComponentModel.INotifyPropertyChanged`|
|`Windows.UI.Xaml.Data.PropertyChangedEventHandler`|`System.ComponentModel.PropertyChangedEventHandler`|
|`Windows.UI.Xaml.Data.PropertyChangedEventArgs`|`System.ComponentModel.PropertyChangedEventArgs`|

 No [!INCLUDE[wrt](../../../includes/wrt-md.md)], `IMap<K, V>` e `IMapView<K, V>` são iterados usando `IKeyValuePair`. Quando você os transmite para código gerenciado, eles aparecem como `IDictionary<TKey, TValue>` e `IReadOnlyDictionary<TKey, TValue>`, então, naturalmente, você usa `System.Collections.Generic.KeyValuePair<TKey, TValue>` para enumerá-los.

 A forma como as interfaces aparecem no código gerenciado afeta a forma como aparecem os tipos que implementam essas interfaces. Por exemplo, a classe `PropertySet` implementa `IMap<K, V>`, que aparece no código gerenciado como `IDictionary<TKey, TValue>`. `PropertySet` aparece como se ele tivesse implementado `IDictionary<TKey, TValue>` em vez de `IMap<K, V>`, por isso, no código gerenciado, ele parece ter um método `Add`, que se comporta como o método `Add` em dicionários do .NET Framework. Ela não parece ter um método `Insert`.

 Para obter mais informações sobre como usar o .NET Framework para criar uma [!INCLUDE[wrt](../../../includes/wrt-md.md)] componente e um passo a passo que mostra como usar um componente com JavaScript, consulte [Criando componentes do tempo de execução do Windows em c# e Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>Tipos primitivos
 Para habilitar o uso natural do [!INCLUDE[wrt](../../../includes/wrt-md.md)] no código gerenciado, tipos primitivos do .NET Framework são exibidos em vez de [!INCLUDE[wrt](../../../includes/wrt-md.md)] tipos primitivos em seu código. No .NET Framework, os tipos primitivos como a estrutura `Int32`, têm muitas propriedades e métodos úteis, como o método `Int32.TryParse`. Por outro lado, estruturas e tipos primitivos no [!INCLUDE[wrt](../../../includes/wrt-md.md)] têm apenas campos. Quando você usa primitivos no código gerenciado, eles parecem ser tipos do .NET Framework, e você pode usar as propriedades e métodos de tipos do .NET Framework, como faria normalmente. A lista a seguir fornece um resumo:

- Para tipos primitivos do [!INCLUDE[wrt](../../../includes/wrt-md.md)]`Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (uma coleção de caracteres Unicode imutável), `Enum`, `UInt32`, `UInt64` e `Guid`, use o tipo de mesmo nome no namespace `System`.

- Para `UInt8`, use `System.Byte`.

- Para `Char16`, use `System.Char`.

- Para a interface `IInspectable`, use `System.Object`.

- Para `HRESULT`, use uma estrutura com um `System.Int32` membro.

 Como com tipos de interface, a única vez em que você pode ver evidências de que essa representação é quando seu projeto do .NET Framework é um [!INCLUDE[wrt](../../../includes/wrt-md.md)] componente que é usado por um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo criado usando JavaScript.

 Outro basic, comumente usado [!INCLUDE[wrt](../../../includes/wrt-md.md)] tipos que aparecem no código gerenciado como seus equivalentes do .NET Framework incluem o `Windows.Foundation.DateTime` estrutura, que aparece no código gerenciado como o <xref:System.DateTimeOffset?displayProperty=nameWithType> estrutura e o `Windows.Foundation.TimeSpan` estrutura, que aparece como o <xref:System.TimeSpan?displayProperty=nameWithType> estrutura.

### <a name="other-differences"></a>Outras diferenças
 Em alguns casos, o fato de que os tipos do .NET Framework aparecem no seu código em vez de [!INCLUDE[wrt](../../../includes/wrt-md.md)] tipos requer uma ação de sua parte. Por exemplo, o <xref:Windows.Foundation.Uri?displayProperty=nameWithType> classe aparece como <xref:System.Uri?displayProperty=nameWithType> no código do .NET Framework. <xref:System.Uri?displayProperty=nameWithType> permite que um URI relativo, mas <xref:Windows.Foundation.Uri?displayProperty=nameWithType> requer um URI absoluto. Portanto, quando você passa um URI para um [!INCLUDE[wrt](../../../includes/wrt-md.md)] método, você deve garantir que ele é absoluto. (Consulte [passando um URI para o tempo de execução do Windows](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).)

<a name="WindowsRuntimeComponents"></a>
## <a name="scenarios-for-developing-windows-runtime-components"></a>Cenários para o desenvolvimento de componentes de tempo de execução do Windows
 Os cenários com suporte para gerenciados [!INCLUDE[wrt](../../../includes/wrt-md.md)] componentes dependem dos seguintes princípios gerais:

- [!INCLUDE[wrt](../../../includes/wrt-md.md)] Componentes que são criados usando o .NET Framework não têm nenhuma diferença aparente de outros [!INCLUDE[wrt](../../../includes/wrt-md.md)]bibliotecas. Por exemplo, se você reimplementar um nativo [!INCLUDE[wrt](../../../includes/wrt-md.md)] componente usando código gerenciado, os dois componentes são indistinguíveis externamente. O fato de que seu componente é escrito em código gerenciado é invisível para o código que usa a ele, mesmo que o código seja próprio código gerenciado. No entanto, internamente, o componente é o verdadeiro código gerenciado e é executado no common language runtime (CLR).

- Componentes podem conter tipos que implementam a lógica do aplicativo, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI controles, ou ambos.

    > [!NOTE]
    >  É recomendável separar elementos de interface do usuário da lógica do aplicativo. Além disso, você não pode usar [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] controles de interface do usuário em um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo compilado para Windows usando JavaScript e HTML.

- Um componente pode ser um projeto dentro de uma solução do Visual Studio para um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo ou um componente reutilizável que você pode adicionar a várias soluções.

    > [!NOTE]
    >  Se seu componente for usado apenas com c# ou Visual Basic, não há nenhum motivo para torná-lo um [!INCLUDE[wrt](../../../includes/wrt-md.md)] componente. Se você fizer uma biblioteca de classes do .NET Framework comum em vez disso, você não tiver que restringir sua superfície de API pública para [!INCLUDE[wrt](../../../includes/wrt-md.md)] tipos.

- Você pode liberar versões dos componentes reutilizáveis, usando o [!INCLUDE[wrt](../../../includes/wrt-md.md)] <xref:Windows.Foundation.Metadata.VersionAttribute> atributo para identificar quais tipos (e quais membros dentro de um tipo) foram adicionadas em versões diferentes.

- Os tipos no seu componente podem derivar [!INCLUDE[wrt](../../../includes/wrt-md.md)] tipos. Controles podem derivar dos tipos primitivos de controle na <xref:Windows.UI.Xaml.Controls.Primitives> namespace ou de mais terminado controles como <xref:Windows.UI.Xaml.Controls.Button>.

    > [!IMPORTANT]
    >  Começando com [!INCLUDE[win8](../../../includes/win8-md.md)] e o .NET Framework 4.5, todos os tipos públicos em um gerenciado [!INCLUDE[wrt](../../../includes/wrt-md.md)] componente deve ser lacrado. Um tipo em outro [!INCLUDE[wrt](../../../includes/wrt-md.md)] componente não pode derivar a partir deles. Se você quiser fornecer um comportamento polimórfico no seu componente, você pode criar uma interface e implementá-lo nos tipos polimórficos.

- Todos os tipos de parâmetro e retorno sobre os tipos públicos em seu componente devem ser [!INCLUDE[wrt](../../../includes/wrt-md.md)] tipos (incluindo o [!INCLUDE[wrt](../../../includes/wrt-md.md)] tipos que define seu componente).

 As seções a seguir fornecem exemplos de cenários comuns.

### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>Lógica do aplicativo para um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo com o JavaScript
 Quando você desenvolve um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo para Windows usando JavaScript, você pode descobrir que algumas partes da lógica do aplicativo funcionar melhor em código gerenciado, ou são mais fáceis de desenvolver. JavaScript não é possível usar as bibliotecas de classes do .NET Framework diretamente, mas você pode tornar a biblioteca de classes um. Arquivo WinMD. Nesse cenário, o [!INCLUDE[wrt](../../../includes/wrt-md.md)] componente é parte integrante do aplicativo, portanto, não faz sentido para fornecer atributos de versão.

### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>Reutilizável [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] controles de interface do usuário
 Você pode empacotar um conjunto de controles de interface do usuário relacionados em um reutilizável [!INCLUDE[wrt](../../../includes/wrt-md.md)] componente. O componente pode ser comercializado por conta própria ou usado como um elemento em aplicativos que você cria. Nesse cenário, faz sentido usar o [!INCLUDE[wrt](../../../includes/wrt-md.md)] <xref:Windows.Foundation.Metadata.VersionAttribute> atributo para melhorar a compatibilidade.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Lógica de aplicativo reutilizáveis de aplicativos existentes do .NET Framework
 Você pode empacotar o código gerenciado de seus aplicativos de área de trabalho existentes como um autônomo [!INCLUDE[wrt](../../../includes/wrt-md.md)] componente. Isso permite que você use o componente no [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] os aplicativos criados usando C++ ou JavaScript, bem como em [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos criados usando c# ou Visual Basic. Controle de versão é uma opção, se houver vários cenários de reutilização para que o código.

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Visão geral dos aplicativos .NET para Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|Descreve os tipos do .NET Framework e os membros que você pode usar para criar [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos e [!INCLUDE[wrt](../../../includes/wrt-md.md)]componentes. (No Centro de desenvolvimento do Windows.)|
|[Roteiro para aplicativos da Windows Store usando c# ou Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Fornece os principais recursos para ajudá-lo a começar a desenvolver [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos usando c# ou Visual Basic, incluindo muitos tópicos do guia de início rápido, diretrizes e práticas recomendadas. (No Centro de desenvolvimento do Windows.)|
|[Como tos (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Fornece os principais recursos para ajudá-lo a começar a desenvolver [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos usando c# ou Visual Basic, incluindo muitos tópicos do guia de início rápido, diretrizes e práticas recomendadas. (No Centro de desenvolvimento do Windows.)|
|[Criando componentes do Windows Runtime no C# e no Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|Descreve como criar uma [!INCLUDE[wrt](../../../includes/wrt-md.md)] componente usando o .NET Framework, explica como usá-lo como parte de um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo compilado para Windows usando JavaScript e descreve como depurar a combinação com o Visual Studio. (No Centro de desenvolvimento do Windows.)|
|[Referência de tempo de execução do Windows](/uwp/api/)|A documentação de referência para o [!INCLUDE[wrt](../../../includes/wrt-md.md)]. (No Centro de desenvolvimento do Windows.)|
|[Passando um URI para o Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|Descreve um problema que pode surgir quando você passa um URI de código gerenciado para o [!INCLUDE[wrt](../../../includes/wrt-md.md)]e como evitá-la.|
