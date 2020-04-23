---
title: Leitura e gravação XAML básico e de classe de serviços XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: 264a8c4abcf9a7efceb7c7accd786495d35476e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071874"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>Classe XAMLServices e leitura ou escrita XAML básicas

<xref:System.Xaml.XamlServices>é uma classe fornecida pelo .NET que pode ser usada para lidar com cenários XAML que não requerem acesso específico ao fluxo de nós XAML ou às informações do sistema do tipo XAML obtidas desses nós. <xref:System.Xaml.XamlServices>A API pode ser `Load` resumida da seguinte forma: ou `Parse` para oferecer suporte a um caminho de carga XAML, `Save` para oferecer suporte a um caminho de salvamento XAML e `Transform` para fornecer uma técnica que une um caminho de carga e salve caminho. `Transform`pode ser usado para mudar de um esquema XAML para outro. Este tópico resume cada uma dessas classificações de API e descreve as diferenças entre as sobrecargas específicas do método.

## <a name="load"></a>Carregar

Várias sobrecargas de <xref:System.Xaml.XamlServices.Load%2A> implementar a lógica completa para um caminho de carga. O caminho de carga usa XAML de alguma forma e produz um fluxo de nó XAML. A maioria desses caminhos de carga usa XAML em um formulário de arquivo de texto XML codificado. No entanto, você também pode carregar um fluxo geral, ou você pode carregar <xref:System.Xaml.XamlReader> uma fonte XAML pré-carregada que já está contida em uma implementação diferente.

A sobrecarga mais simples <xref:System.Xaml.XamlServices.Load%28System.String%29>para a maioria dos cenários é . Esta sobrecarga `fileName` tem um parâmetro que é simplesmente o nome de um arquivo de texto que contém o XAML para carregar. Isso é apropriado para cenários de aplicativos, como aplicativos de confiança total que já serializaram estado ou dados para o computador local. Isso também é útil para frameworks onde você está definindo o modelo de aplicativo e deseja carregar um dos arquivos padrão que define o comportamento do aplicativo, a interface do usuário inicial ou outros recursos definidos por framework que usam XAML.

<xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29>tem cenários semelhantes. Essa sobrecarga pode ser útil se o usuário escolher <xref:System.IO.Stream> arquivos para carregar, porque a é uma saída freqüente de outras <xref:System.IO> APIs que podem acessar um sistema de arquivos. Ou você pode estar acessando fontes XAML através de downloads assíncronos ou outras técnicas de rede que também fornecem um fluxo. (O carregamento de um fluxo ou fonte selecionada pelo usuário pode ter implicações de segurança. Para obter mais informações, consulte [Considerações de segurança XAML](security-considerations.md).)

<xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29>e <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> são sobrecargas que dependem de leitores de formatos de versões anteriores do .NET. Para usar essas sobrecargas, você já deve ter `Create` criado uma instância do leitor e usado sua API para carregar o XAML na forma relevante (texto ou XML). Se você já moveu ponteiros de registro nos outros leitores ou realizou outras operações com eles, isso não é importante. A lógica do <xref:System.Xaml.XamlServices.Load%2A> caminho de carga de sempre processa toda a entrada XAML da raiz para baixo. Os seguintes cenários podem justificar o uso dessas sobrecargas:

- Superfícies de design onde você fornece recursos de edição XAML simples a partir de um editor de texto específico do XML existente.

- Variantes dos <xref:System.IO> cenários principais, onde você usa os leitores dedicados para abrir arquivos ou fluxos. Sua lógica realiza verificação rudimentar ou processamento do conteúdo antes de tentar carregar como XAML.

Você pode carregar um arquivo ou fluxo, <xref:System.Xml.XmlReader> <xref:System.IO.TextReader>ou <xref:System.Xaml.XamlReader> pode carregar uma , ou que envolve sua entrada XAML carregando com as APIs do leitor.

Internamente, cada uma das sobrecargas <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>anteriores <xref:System.Xml.XmlReader> é, em última <xref:System.Xaml.XamlXmlReader>análise, e o passado é usado para criar um novo .

A `Load` assinatura que prevê cenários mais avançados é <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>. Você pode usar esta assinatura para um dos seguintes casos:

- Você definiu sua própria implementação de um <xref:System.Xaml.XamlReader>.

- Você precisa especificar <xref:System.Xaml.XamlReader> configurações para que variem das configurações padrão.

Exemplos de configurações não padrão:

<xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>\
<xref:System.Xaml.XamlReaderSettings.BaseUri%2A>\
<xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>\
<xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>\
<xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>.

O leitor <xref:System.Xaml.XamlServices> padrão <xref:System.Xaml.XamlXmlReader>para é . Se você fornecer <xref:System.Xaml.XamlXmlReader> as configurações próprias, as seguintes propriedades serão definidas não-padrão: <xref:System.Xaml.XamlXmlReaderSettings>

<xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>

## <a name="parse"></a>Analisar

<xref:System.Xaml.XamlServices.Parse%2A>é `Load` como porque é uma API de caminho de carga que cria um fluxo de nó XAML a partir da entrada XAML. No entanto, neste caso, a entrada XAML é fornecida diretamente como uma string que contém todo o XAML para carregar. <xref:System.Xaml.XamlServices.Parse%2A>é uma abordagem leve que é mais apropriada para cenários de aplicativos do que cenários-quadro. Para obter mais informações, consulte <xref:System.Xaml.XamlServices.Parse%2A>. <xref:System.Xaml.XamlServices.Parse%2A>é apenas <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> uma chamada <xref:System.IO.StringReader> embrulhada que envolve um internamente.

## <a name="save"></a>Salvar

Várias sobrecargas de <xref:System.Xaml.XamlServices.Save%2A> implementar o caminho de salvamento. Todos os <xref:System.Xaml.XamlServices.Save%2A> métodos tomam um gráfico de objetos como entrada <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> e produzem saída como um fluxo, arquivo ou instância.

Espera-se que o objeto de entrada seja o objeto raiz de alguma representação de objeto. Esta pode ser a única raiz de um objeto de negócios, a raiz de uma árvore de objetos para uma página em um cenário de UI, a superfície de edição de trabalho de uma ferramenta de design ou outros conceitos de objeto raiz apropriados para cenários.

Em muitos cenários, a árvore de objetos que você salva está <xref:System.Xaml.XamlServices.Load%2A> relacionada a uma operação original que carregou XAML com ou com outra API implementada por um modelo de framework/aplicativo. Pode haver diferenças capturadas na árvore de objetos que são devido a alterações de estado, alterações onde o aplicativo capturou configurações de tempo de execução de um usuário, mudou XAML porque seu aplicativo é uma superfície de design XAML, etc. Com ou sem alterações, o conceito de primeiro carregar XAML da marcação e depois salvá-lo novamente e comparar os dois formulários de marcação XAML é às vezes referido como uma representação de ida e volta do XAML.

O desafio de salvar e serializar um objeto complexo que é definido em uma forma de marcação é alcançar um equilíbrio entre representação completa sem perda de informações, versus verbosidade que torna o XAML menos legível por humanos. Além disso, diferentes clientes para XAML podem ter definições ou expectativas diferentes de como esse equilíbrio deve ser definido. As <xref:System.Xaml.XamlServices.Save%2A> APIs representam uma definição desse equilíbrio. As <xref:System.Xaml.XamlServices.Save%2A> APIs usam o contexto de esquema XAML disponível <xref:System.Xaml.XamlType> <xref:System.Xaml.XamlMember>e as características padrão baseadas em CLR de , e outros conceitos de sistema do tipo XAML e XAML para determinar onde certas construções de fluxo de nós XAML podem ser otimizadas quando são salvas de volta para marcação. Por exemplo, <xref:System.Xaml.XamlServices> os caminhos de salvamento podem usar o contexto <xref:System.Xaml.XamlType> padrão xaml <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>padrão baseado em CLR para resolver objetos, pode determinar um e, em seguida, pode omitir tags de elemento de propriedade quando eles escrevem a propriedade para o conteúdo XAML do objeto.

<a name="transform"></a>
## <a name="transform"></a>Transformar

<xref:System.Xaml.XamlServices.Transform%2A>converte ou transforma XAML ligando um caminho de carga e um caminho de salvamento como uma única operação. Um contexto de esquema diferente ou um sistema <xref:System.Xaml.XamlReader> <xref:System.Xaml.XamlWriter>de tipo de apoio diferente pode ser usado e, que é o que influencia como o XAML resultante é transformado. Isso funciona bem para operações de transformação ampla.

Para operações que dependem de examinar cada nó em um fluxo de <xref:System.Xaml.XamlServices.Transform%2A>nó XAML, você normalmente não usa . Em vez disso, você precisa definir sua própria série de operação de caminho de salvamento de caminho de carga e interpor sua própria lógica. Em um dos caminhos, use um par de leitores XAML/XAML em torno do seu próprio loop de nó. Por exemplo, carregue o XAML inicial usando <xref:System.Xaml.XamlXmlReader> e <xref:System.Xaml.XamlXmlReader.Read%2A> entre nos nós com chamadas sucessivas. Operando no nível de fluxo de nó XAML, agora você pode ajustar os nódulos individuais (tipos, membros, outros nós) para aplicar uma transformação ou deixar o nó como está. Em seguida, você envia o `Write` nó para <xref:System.Xaml.XamlObjectWriter> a API relevante de a e escreve o objeto. Para obter mais informações, consulte [Entendendo estruturas e conceitos de fluxo de nó XAML](understanding-xaml-node-stream-structures-and-concepts.md).

## <a name="see-also"></a>Confira também

- <xref:System.Xaml.XamlObjectWriter>
- <xref:System.Xaml.XamlServices>
- [Serviços XAML](../../../api/index.md)
