---
title: Definir recursos XAML
description: Saiba mais sobre os recursos XAML no WPF para .NET Core. Entenda os tipos de recursos XAML e aprenda a definir os recursos XAML.
author: thraka
ms.author: adegeo
ms.date: 08/21/2019
ms.openlocfilehash: b278bb92afc308578d60e347871e0150b26a95db
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/31/2019
ms.locfileid: "82071279"
---
# <a name="overview-of-xaml-resources"></a>Visão geral dos recursos XAML

Um recurso é um objeto que pode ser reutilizado em diferentes lugares do seu aplicativo. Exemplos de recursos incluem pincéis e estilos. Esta visão geral descreve como usar recursos no XAML (Extensible Application Markup Language, linguagem de marcação de aplicativos extensível). Você também pode criar e acessar recursos usando código.

> [!NOTE]
> Os recursos XAML descritos neste artigo são diferentes dos recursos do *aplicativo* que geralmente são arquivos adicionados a um aplicativo, como conteúdo, dados ou arquivos incorporados.

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>Usando recursos em XAML

O exemplo a <xref:System.Windows.Media.SolidColorBrush> seguir define um recurso no elemento raiz de uma página. O exemplo, então, faz referência ao recurso e o <xref:System.Windows.Shapes.Ellipse>usa <xref:System.Windows.Controls.TextBlock>para definir <xref:System.Windows.Controls.Button>propriedades de vários elementos infantis, incluindo um , a , e um .

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

Cada elemento de<xref:System.Windows.FrameworkElement> nível <xref:System.Windows.FrameworkContentElement>de <xref:System.Windows.FrameworkElement.Resources%2A> estrutura (ou <xref:System.Windows.ResourceDictionary> ) tem uma propriedade, que é um tipo que contém recursos definidos. Você pode definir recursos em qualquer <xref:System.Windows.Controls.Button>elemento, como um . No entanto, os recursos são mais <xref:System.Windows.Controls.Page> frequentemente definidos no elemento raiz, que está no exemplo.

Cada recurso em um dicionário de recursos deve ter uma chave exclusiva. Quando você define os recursos na marcação, você atribui a chave única através da [diretiva x:Key](../xaml-services/xkey-directive.md). Normalmente, a chave é uma cadeia de caracteres; no entanto, você pode também a definir com outros tipos de objeto usando as extensões de marcação apropriadas. As chaves não-string para recursos são usadas por certas áreas de recurso no WPF, notadamente para estilos, recursos de componentes e estilo de dados.

Você pode usar um recurso definido com a sintaxe de extensão de marcação de recursos que especifica o nome-chave do recurso. Por exemplo, use o recurso como o valor de uma propriedade em outro elemento.

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

No exemplo anterior, quando o carregador XAML <xref:System.Windows.Controls.Control.Background%2A> processa <xref:System.Windows.Controls.Button>o valor `{StaticResource MyBrush}` da propriedade em, a <xref:System.Windows.Controls.Button> lógica de busca de recursos verifica primeiro o dicionário de recursos para o elemento. Se <xref:System.Windows.Controls.Button> não tiver uma definição da `MyBrush` chave de recurso (nesse exemplo não tem; sua coleta de recursos <xref:System.Windows.Controls.Button>está <xref:System.Windows.Controls.Page>vazia), a olhada em seguida verifica o elemento pai de , que é . Se você definir um <xref:System.Windows.Controls.Page> recurso no elemento raiz, todos <xref:System.Windows.Controls.Page> os elementos na árvore lógica do pode acessá-lo. E você pode reutilizar o mesmo recurso para definir o valor de qualquer propriedade que aceite o mesmo tipo que o recurso representa. No exemplo anterior, `MyBrush` o mesmo recurso define <xref:System.Windows.Controls.Control.Background%2A> duas <xref:System.Windows.Controls.Button>propriedades <xref:System.Windows.Shapes.Shape.Fill%2A> diferentes: a de a , e a de a <xref:System.Windows.Shapes.Rectangle>.

## <a name="static-and-dynamic-resources"></a>Recursos estáticos e dinâmicos

Um recurso pode ser referenciado como estático ou dinâmico. As referências são criadas usando a [extensão staticResource Markup](../../framework/wpf/advanced/staticresource-markup-extension.md) ou a [DynamicResource Markup Extension](../../framework/wpf/advanced/dynamicresource-markup-extension.md). Uma extensão de marcação é um recurso XAML que permite especificar uma referência de objeto, tendo o processo de extensão de marcação na seqüência de atributos e retornar o objeto a um carregador XAML. Para obter mais informações sobre o comportamento de extensão de marcação, consulte [Extensões de marcação e WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

Quando você usa uma extensão de marcação, você normalmente fornece um ou mais parâmetros na forma de string que são processados por essa extensão de marcação específica. O [StaticResource Markup Extension](../../framework/wpf/advanced/staticresource-markup-extension.md) processa uma chave, procurando o valor dessa chave em todos os dicionários de recursos disponíveis. O processamento acontece durante a carga, que é quando o processo de carregamento precisa atribuir o valor da propriedade. Em vez disso, a [Extensão de Marcação de Recursos Dinâmicos](../../framework/wpf/advanced/dynamicresource-markup-extension.md) processa uma chave criando uma expressão, e essa expressão permanece não avaliada até que o aplicativo seja executado, momento em que a expressão é avaliada e fornece um valor.

Quando você referencia um recurso, as seguintes considerações podem influenciar se uma referência de recurso estático ou dinâmico será usada:

- Ao determinar o design geral de como você cria os recursos para o seu aplicativo (por página, no aplicativo, em XAML solto ou em uma montagem somente de recursos), considere o seguinte:

- A funcionalidade do aplicativo. Atualizar recursos em tempo real faz parte dos requisitos do seu aplicativo?
- O respectivo comportamento de pesquisa desse tipo de referência de recurso.
- A propriedade ou o tipo de recurso específico e o comportamento nativo desses tipos.

## <a name="static-resources"></a>Recursos estáticos

As referências de recursos estáticos funcionam melhor nas seguintes circunstâncias:

- O design do aplicativo concentra a maioria de seus recursos em dicionários de recursos em nível de página ou aplicativo. As referências estáticas de recursos não são reavaliadas com base em comportamentos de tempo de execução, como recarregar uma página. Portanto, pode haver algum benefício de desempenho para evitar um grande número de referências dinâmicas de recursos quando elas não são necessárias com base no seu recurso e design de aplicativos.

- Você está definindo o valor de uma <xref:System.Windows.DependencyObject> propriedade <xref:System.Windows.Freezable>que não está em um ou um .

- Você está criando um dicionário de recursos que será compilado em um DLL e embalado como parte do aplicativo ou compartilhado entre aplicativos.

- Você está criando um tema para um controle personalizado e está definindo recursos que são usados dentro dos temas. Para este caso, você normalmente não deseja o comportamento dinâmico de busca de referência de recursos; em vez disso, você quer o comportamento de referência de recursos estáticos para que a aparência seja previsível e independente do tema. Com uma referência de recurso dinâmico, até mesmo uma referência dentro de um tema é deixada sem avaliação até o tempo de execução. e há uma chance de que, quando o tema é aplicado, algum elemento local irá redefinir uma chave que seu tema está tentando referenciar, e o elemento local cairá antes do próprio tema na consulta. Se isso acontecer, seu tema não se comportará como esperado.

- Você está usando recursos para definir um grande número de propriedades de dependência. As propriedades de dependência têm cache de valor efetivo conforme habilitado pelo sistema de propriedades, portanto, se você fornecer um valor para um imóvel de dependência que pode ser avaliado no tempo de carga, a propriedade de dependência não precisa verificar se há uma expressão reavaliada e pode retornar o último valor efetivo. Essa técnica pode ser uma vantagem de desempenho.

- Você deseja alterar o recurso subjacente para todos os consumidores ou deseja manter instâncias graváveis separadas para cada consumidor usando o [x:Atributo compartilhado](../xaml-services/xshared-attribute.md).

### <a name="static-resource-lookup-behavior"></a>Comportamento de pesquisa de recursos estáticos

O seguinte descreve o processo de consulta que acontece automaticamente quando um recurso estático é referenciado por uma propriedade ou elemento:

01. O processo de pesquisa verifica a chave solicitada no dicionário de recursos definido pelo elemento que define a propriedade.

01. O processo de análise então atravessa a árvore lógica para cima até o elemento pai e seu dicionário de recursos. Esse processo continua até que o elemento raiz seja alcançado.

01. Os recursos do aplicativo são verificados. Os recursos do aplicativo são esses recursos <xref:System.Windows.Application> dentro do dicionário de recursos que é definido pelo objeto para o seu aplicativo WPF.

As referências de recursos estáticos em um dicionário de recursos devem referenciar um recurso que já foi definido lexicalmente antes da referência ao recurso. As referências de encaminhamento não podem ser resolvidas por uma referência de recursos estáticos. Por essa razão, projete sua estrutura de dicionário de recursos para que os recursos sejam definidos no ou perto do início de cada dicionário de recursos respectivo.

A análise de recursos estáticos pode se estender a temas ou recursos do sistema, mas essa consulta só é suportada porque o carregador XAML adia a solicitação. O adiamento é necessário para que o tema de tempo de execução no momento em que a página é carregada se aplique adequadamente ao aplicativo. No entanto, referências estáticas de recursos a chaves que são conhecidas por existirem apenas em temas ou como recursos do sistema não são recomendadas, porque tais referências não são reavaliadas se o tema for alterado pelo usuário em tempo real. Uma referência de recurso dinâmico é mais confiável quando você solicita recursos do sistema ou de tema. A exceção é quando um próprio elemento de tema solicita outro recurso. Essas referências devem ser referências de recursos estáticos, pelas razões mencionadas anteriormente.

O comportamento de exceção se uma referência de recurso estático não for encontrada varia. Se o recurso foi adiado, a exceção ocorre em runtime. Se o recurso não foi adiado, a exceção ocorre em tempo de carregamento.

## <a name="dynamic-resources"></a>Recursos dinâmicos

Os recursos dinâmicos funcionam melhor quando:

- O valor do recurso, incluindo recursos do sistema, ou recursos que são definidos pelo usuário, depende de condições que não são conhecidas até o tempo de execução. Por exemplo, você pode criar valores de setter <xref:System.Windows.SystemColors> <xref:System.Windows.SystemFonts>que <xref:System.Windows.SystemParameters>se referem às propriedades do sistema como expostas por , ou . Esses valores são realmente dinâmicos, pois, basicamente, são obtidos do ambiente em runtime do usuário e do sistema operacional. Você também pode ter temas em nível do aplicativo que podem ser alterados, em que o acesso aos recursos em nível de página também deve captar a alteração.

- Você está criando ou referenciando estilos temáticos para um controle personalizado.

- Você pretende ajustar o <xref:System.Windows.ResourceDictionary> conteúdo de um durante uma vida útil do aplicativo.

- Você tem uma estrutura de recursos complicada que tem interdependências, em que uma referência de encaminhamento pode ser necessária. As referências estáticas de recursos não suportam referências avançadas, mas as referências dinâmicas de recursos as suportam porque o recurso não precisa ser avaliado até o tempo de execução, e as referências de encaminhamento não são, portanto, um conceito relevante.

- Você está fazendo referência a um recurso que é grande na perspectiva de um conjunto de compilação ou trabalho, e o recurso pode não ser usado imediatamente quando a página é carregada. Referências de recursos estáticos sempre carregam de XAML quando a página é carregada. No entanto, uma referência dinâmica de recursos não carrega até que seja usada.

- Você está criando um estilo onde os valores do setter podem vir de outros valores que são influenciados por temas ou outras configurações do usuário.

- Você está aplicando recursos a elementos que podem ser reparentados na árvore lógica durante a vida útil do aplicativo. Potencialmente, a alteração do pai também altera o escopo de pesquisa de recursos; portanto, se você desejar que o recurso de um elemento reassociado seja reavaliado com base no novo escopo, sempre use uma referência de recursos dinâmicos.

### <a name="dynamic-resource-lookup-behavior"></a>Comportamento de pesquisa de recursos dinâmicos

O comportamento de busca de recursos para uma referência de recurso <xref:System.Windows.FrameworkElement.FindResource%2A> <xref:System.Windows.FrameworkElement.SetResourceReference%2A>dinâmico faz um paralelo com o comportamento de busca em seu código se você ligar ou :

01. A busca verifica a chave solicitada no dicionário de recursos definido pelo elemento que define a propriedade:

    - Se o elemento <xref:System.Windows.FrameworkElement.Style%2A> define uma <xref:System.Windows.FrameworkElement.Style?displayProperty=fullName> propriedade, o <xref:System.Windows.Style.Resources> elemento tem seu dicionário verificado.

    - Se o elemento <xref:System.Windows.Controls.Control.Template%2A> definir uma <xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName> propriedade, o dicionário do elemento será verificado.

01. A olhada atravessa a árvore lógica para cima até o elemento pai e seu dicionário de recursos. Esse processo continua até que o elemento raiz seja alcançado.

01. Os recursos do aplicativo são verificados. Os recursos do aplicativo são esses recursos <xref:System.Windows.Application> dentro do dicionário de recursos que são definidos pelo objeto para o seu aplicativo WPF.

01. O dicionário de recursos temáticos é verificado para o tema ativo atualmente. Se o tema for alterado em runtime, o valor será reavaliado.

01. Os recursos do sistema são verificados.

O comportamento de exceção (se houver) varia:

- Se um recurso foi <xref:System.Windows.FrameworkElement.FindResource%2A> solicitado por uma chamada e não foi encontrado, uma exceção será descartada.

- Se um recurso foi <xref:System.Windows.FrameworkElement.TryFindResource%2A> solicitado por uma chamada e não foi encontrado, `null`nenhuma exceção será lançada, e o valor devolvido é . Se a propriedade que está `null`sendo definida não aceitar, então ainda é possível que uma exceção mais profunda seja lançada, dependendo da propriedade individual que está sendo definida.

- Se um recurso foi solicitado por uma referência de recurso dinâmico em XAML e não foi encontrado, então o comportamento depende do sistema de propriedade geral. O comportamento geral é como se nenhuma operação de configuração de propriedade ocorresse no nível em que o recurso existe. Por exemplo, se você tentar definir o plano de fundo em um elemento de botão individual usando um recurso que não pôde ser avaliado, então nenhum valor definido resultados, mas o valor efetivo ainda pode vir de outros participantes no sistema de propriedade e precedência de valor. Por exemplo, o valor de fundo ainda pode vir de um estilo de botão definido localmente ou do estilo temático. Para propriedades que não são definidas por estilos temáticos, o valor efetivo após uma avaliação de recurso falhada pode vir do valor padrão nos metadados de propriedade.

### <a name="restrictions"></a>Restrições

As referências de recursos dinâmicos têm algumas restrições importantes. Pelo menos uma das seguintes condições deve ser verdadeira:

- A propriedade que está sendo <xref:System.Windows.FrameworkElement> definida <xref:System.Windows.FrameworkContentElement>deve ser uma propriedade em um ou . Essa propriedade deve ser <xref:System.Windows.DependencyProperty>apoiada por um.

- A referência é para `StyleSetter`um valor dentro de um .

- O imóvel que está sendo <xref:System.Windows.Freezable> definido deve ser um imóvel <xref:System.Windows.FrameworkElement> em <xref:System.Windows.FrameworkContentElement> um que <xref:System.Windows.Setter> é fornecido como um valor de um ou propriedade, ou um valor.

Como o imóvel que <xref:System.Windows.DependencyProperty> está <xref:System.Windows.Freezable> sendo definido deve ser um ou propriedade, a maioria das alterações de propriedade pode se propagar para a ui porque uma alteração de propriedade (o valor do recurso dinâmico alterado) é reconhecida pelo sistema de propriedade. A maioria dos controles inclui lógica que forçará outro layout de um controle se uma <xref:System.Windows.DependencyProperty> alteração e essa propriedade pode afetar o layout. No entanto, nem todas as propriedades que possuem uma [extensão de marcação dinâmica](../../framework/wpf/advanced/dynamicresource-markup-extension.md) de recursos, pois seu valor é garantido para fornecer atualizações em tempo real na ui. Essa funcionalidade ainda pode variar dependendo da propriedade, bem como dependendo do tipo que possui o imóvel, ou mesmo da estrutura lógica do seu aplicativo.

## <a name="styles-datatemplates-and-implicit-keys"></a>Estilos, DataTemplates e chaves implícitas

Embora todos os itens <xref:System.Windows.ResourceDictionary> em um deve ter uma chave, isso não `x:Key`significa que todos os recursos devem ter uma explícita . Vários tipos de objeto dão suporte a uma chave implícita quando definidos como um recurso, em que o valor da chave é vinculado ao valor de outra propriedade. Esse tipo de chave é conhecida como `x:Key` uma chave implícita, enquanto um atributo é uma chave explícita. Você pode substituir uma chave implícita especificando uma chave explícita.

Um cenário importante para os <xref:System.Windows.Style>recursos é quando você define um . Na verdade, <xref:System.Windows.Style> a é quase sempre definida como uma entrada em um dicionário de recursos, porque os estilos são inerentemente destinados à reutilização. Para obter mais informações sobre estilos, consulte [Styling e Templating](styles-templates-overview.md).

Os estilos de controles podem ser criados com uma chave implícita e referenciados com ela. Os estilos de tema que definem a aparência padrão de um controle se baseiam nessa chave implícita. Do ponto de vista de solicitá-lo, a chave implícita é o <xref:System.Type> próprio controle. Do ponto de vista da definição dos <xref:System.Windows.Style.TargetType%2A> recursos, a chave implícita é o do estilo. Portanto, se você está criando temas para controles personalizados ou criando estilos que interagem com os estilos temáticos existentes, você não precisa especificar uma [diretiva x:Chave](../xaml-services/xkey-directive.md) para isso <xref:System.Windows.Style>. Além disso, você desejar usar os estilos de tema, não precisará especificar nenhum estilo. Por exemplo, a definição de estilo <xref:System.Windows.Style> a seguir funciona, mesmo que o recurso não pareça ter uma chave:

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

Esse estilo realmente tem uma `typeof(System.Windows.Controls.Button)`chave: a chave implícita. Na marcação, você <xref:System.Windows.Style.TargetType%2A> pode especificar um nome de tipo diretamente (ou você pode usar opcionalmente [{x:Type...}](../xaml-services/xtype-markup-extension.md) para retornar <xref:System.Type>um .

Através dos mecanismos de estilo de tema padrão usados pelo WPF, esse estilo é aplicado como o estilo de tempo de execução de a <xref:System.Windows.Controls.Button> na página, mesmo que o <xref:System.Windows.Controls.Button> próprio não tente especificar sua <xref:System.Windows.FrameworkElement.Style%2A> propriedade ou uma referência de recurso específica ao estilo. Seu estilo definido na página é encontrado anteriormente na seqüência de pesquisa do que o estilo do dicionário temático, usando a mesma chave que o estilo de dicionário temático tem. Você pode `<Button>Hello</Button>` apenas especificar em qualquer lugar <xref:System.Windows.Style.TargetType%2A> da `Button` página, e o estilo com o qual você definiu se aplicaria a esse botão. Se você quiser, você ainda pode explicitamente digitar o <xref:System.Windows.Style.TargetType%2A> estilo com o mesmo valor de tipo que para clareza em sua marcação, mas isso é opcional.

As teclas implícitas para estilos <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> `true`não se aplicam em um controle se for . (Observe também <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> que pode ser definido como parte do comportamento nativo para a classe de controle, em vez de explicitamente em uma instância do controle.) Além disso, a fim de suportar chaves implícitas para <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> cenários de classe derivadas, o controle deve substituir (todos os controles existentes fornecidos como parte do WPF incluem essa substituição). Para obter mais informações sobre estilos, temas e design de controle, consulte [Diretrizes para projetar controles estilizados](../../framework/wpf/controls/guidelines-for-designing-stylable-controls.md).

<xref:System.Windows.DataTemplate>também tem uma chave implícita. A chave implícita <xref:System.Windows.DataTemplate> para <xref:System.Windows.DataTemplate.DataType%2A> a é o valor da propriedade. <xref:System.Windows.DataTemplate.DataType%2A>também pode ser especificado como o nome do tipo em vez de usar explicitamente [{x:Type...}](../xaml-services/xtype-markup-extension.md). Para obter detalhes, consulte [Visão geral de Data Templating](../../framework/wpf/data/data-templating-overview.md).

## <a name="see-also"></a>Confira também

- <xref:System.Windows.ResourceDictionary>
- [Recursos de aplicação](../../framework/wpf/advanced/optimizing-performance-application-resources.md)
- [Recursos e código](../../framework/wpf/advanced/resources-and-code.md)
- [Definir e referenciar um recurso](../../framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [Visão geral do gerenciamento de aplicativos](../../framework/wpf/app-development/application-management-overview.md)
- [x:Extensão de marcação de tipo](../xaml-services/xtype-markup-extension.md)
- [Extensão de marcação staticResource](../../framework/wpf/advanced/staticresource-markup-extension.md)
- [Extensão de marcação DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md)
