---
title: Leitura e gravação XAML básico e de classe de serviços XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: c9ef6a215587750f66d2cf8b5b54cbc51f89037e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938730"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>Leitura e gravação XAML básico e de classe de serviços XAML
<xref:System.Xaml.XamlServices> é uma classe fornecida pelo serviços de XAML do .NET Framework que pode ser usado para lidar com cenários XAML que não exigem acesso específico para o fluxo do nó XAML ou informações do sistema de tipo XAML obtido em nós. <xref:System.Xaml.XamlServices> API pode ser resumida como o seguinte: `Load` ou `Parse` para dar suporte a um caminho de carregamento XAML `Save` para dar suporte a um XAML salvar caminho, e `Transform` para fornecer uma técnica que ingressa em um caminho de carregamento e salvar caminho. `Transform` pode ser usado para alterar de um esquema XAML para outro. Este tópico resume cada uma destas classificações de API e descreve as diferenças entre sobrecargas de método específico.  
  
<a name="load"></a>   
## <a name="load"></a>Carregamento  
 Várias sobrecargas de <xref:System.Xaml.XamlServices.Load%2A> implementar a lógica completa para um caminho de carga. O caminho de carga usa XAML de alguma forma e gera um fluxo do nó XAML. A maioria deles carregar o uso de caminhos XAML em um formulário de arquivo de texto codificado em XML. No entanto, você também pode carregar um fluxo geral, ou você pode carregar uma fonte de XAML pré-carregados que já está contida em um local diferente <xref:System.Xaml.XamlReader> implementação.  
  
 A sobrecarga mais simples para a maioria dos cenários é <xref:System.Xaml.XamlServices.Load%28System.String%29>. Essa sobrecarga tem um `fileName` parâmetro que é simplesmente o nome de um arquivo de texto que contém o XAML para carregar. Isso é adequado para cenários de aplicativos, como aplicativos de confiança total que têm serializado anteriormente estado ou os dados no computador local. Isso também é útil para estruturas de onde você está definindo o modelo de aplicativo e quiser carregar um dos arquivos padrão que define o comportamento do aplicativo, começando a interface do usuário ou outros recursos definidos pelo framework que usam XAML.  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29> tem a cenários semelhantes. Essa sobrecarga pode ser útil se você tiver o usuário escolher arquivos para carregar, porque uma <xref:System.IO.Stream> é uma saída frequente de outros <xref:System.IO> APIs que podem acessar um sistema de arquivos. Ou poderia acessar fontes de XAML por meio de downloads assíncronos ou outras técnicas de rede que também fornecem um fluxo. (O carregamento de um fluxo ou o código-fonte selecionado pelo usuário pode ter implicações de segurança. Para obter mais informações, consulte [considerações sobre segurança de XAML](xaml-security-considerations.md).)  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29> e <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> são sobrecargas que dependem dos leitores dos formatos de versões anteriores do .NET Framework. Para usar essas sobrecargas, você deve já criou uma instância de leitor e usado seu `Create` API para carregar o XAML no formulário relevante (texto ou XML). Se você já tiver movido ponteiros de registro em outros leitores ou executadas outras operações com eles, isso não é importante. A lógica de caminho da carga do <xref:System.Xaml.XamlServices.Load%2A> sempre processa o XAML inteiro da raiz de entrada para baixo. Cenários para essas sobrecargas podem incluir o seguinte:  
  
- Em que você fornecer o recurso de um editor de texto específicas de XML existente de edição de XAML simple de superfícies de design.  
  
- Variantes do núcleo <xref:System.IO> cenários, em que você usar os leitores dedicados para abrir arquivos ou fluxos. Sua lógica executa verificação rudimentar ou processamento do conteúdo antes de tentar carregar como XAML.  
  
 Você pode carregar um arquivo ou fluxo ou você pode carregar uma <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, ou <xref:System.Xaml.XamlReader> que encapsulam a entrada XAML Carregando com as APIs do leitor.  
  
 Internamente, cada uma das sobrecargas anteriores é definitivamente <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>e passado <xref:System.Xml.XmlReader> é usado para criar um novo <xref:System.Xaml.XamlXmlReader>.  
  
 O `Load` assinatura que fornece mais avançados de cenários é <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>. Você pode usar essa assinatura para um dos seguintes casos:  
  
- Você tiver definido sua própria implementação de um <xref:System.Xaml.XamlReader>.  
  
- Você precisa especificar as configurações para <xref:System.Xaml.XamlReader> que variam das configurações padrão.  
  
 Exemplos de configurações não padrão são definir qualquer um dos seguintes: <xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>; <xref:System.Xaml.XamlReaderSettings.BaseUri%2A>; <xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>; <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>; <xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>. O leitor padrão para <xref:System.Xaml.XamlServices> é <xref:System.Xaml.XamlXmlReader>. Se você fornecer seus próprios <xref:System.Xaml.XamlXmlReader>, com as configurações a seguir estão as propriedades definidas não padrão <xref:System.Xaml.XamlXmlReaderSettings>: <xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>; <xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>.  
  
<a name="parse"></a>   
## <a name="parse"></a>Parse  
 <xref:System.Xaml.XamlServices.Parse%2A> é como `Load` porque ele é um caminho de carga API que cria um fluxo do nó XAML de entrada XAML. No entanto, nesse caso, a entrada XAML é fornecida diretamente como uma cadeia de caracteres que contém todos os o XAML para carregar. <xref:System.Xaml.XamlServices.Parse%2A> é uma abordagem leve que é mais adequada para cenários de aplicativos que os cenários de estrutura. Para obter mais informações, consulte <xref:System.Xaml.XamlServices.Parse%2A>. <xref:System.Xaml.XamlServices.Parse%2A> é realmente apenas um encapsulado <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> chamada que envolve um <xref:System.IO.StringReader> internamente.  
  
<a name="save"></a>   
## <a name="save"></a>Salvar  
 Várias sobrecargas de <xref:System.Xaml.XamlServices.Save%2A> implementar salvar caminho. Todos os <xref:System.Xaml.XamlServices.Save%2A> métodos usam um gráfico de objeto como entrada e produzem saída como um fluxo de arquivos, ou <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> instância.  
  
 O objeto de entrada deve ser o objeto raiz de alguma representação de objeto. Isso pode ser a única raiz de um objeto de negócios, a raiz de uma árvore de objetos para uma página em um cenário de interface do usuário, a superfície de edição de trabalho de uma ferramenta de design ou outros conceitos do objeto raiz que são apropriados para cenários.  
  
 Em muitos cenários de árvore de objetos que você salva é relacionada a uma operação original que carregados XAML com <xref:System.Xaml.XamlServices.Load%2A> ou com outra API implementado por um modelo de aplicativo do framework. Pode haver diferenças capturadas na árvore de objetos que são devido a alterações de estado, as alterações na qual seu aplicativo capturados configurações de tempo de execução de um usuário, alterado XAML porque seu aplicativo é um etc superfície, do design XAML. Com ou sem alterações, o conceito de primeira Carregando XAML de marcação e, em seguida, salvá-lo novamente e comparar as duas formas de marcação XAML, às vezes, é conhecido como uma representação de ida e volta da XAML.  
  
 O desafio de salvar e serializar um objeto complexo que é definido em um formato de marcação é alcançar um equilíbrio entre a representação completa sem perda de informações, em vez de detalhamento que torna o XAML menos legível por humanos. Além disso, clientes diferentes para o XAML podem ter diferentes definições ou expectativas de como esse equilíbrio deve ser definido. O <xref:System.Xaml.XamlServices.Save%2A> APIs representam uma definição desse equilíbrio. O <xref:System.Xaml.XamlServices.Save%2A> APIs usam o contexto de esquema XAML disponível e as características do padrão baseado em CLR do <xref:System.Xaml.XamlType>, <xref:System.Xaml.XamlMember>, e conceitos do sistema para determinar onde determinadas construções de fluxo de nó XAML podem ser de tipo de outros intrínsecos de XAML e XAML otimizado quando eles são salvos de volta na marcação. Por exemplo, <xref:System.Xaml.XamlServices> salvar caminhos pode usar o contexto de esquema XAML padrão baseado em CLR para resolver <xref:System.Xaml.XamlType> para objetos, pode determinar um <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>e, em seguida, poderá omitir as marcas de elemento de propriedade quando a propriedade eles gravam o conteúdo XAML do objeto.  
  
<a name="transform"></a>   
## <a name="transform"></a>Transformar  
 <xref:System.Xaml.XamlServices.Transform%2A> Converte ou transforma XAML vinculando um caminho de carga e de salvar caminho como uma única operação. Um contexto de esquema diferente ou o sistema de tipos de backup diferente pode ser usado para <xref:System.Xaml.XamlReader> e <xref:System.Xaml.XamlWriter>, que é o que influenciará como o XAML resultante é transformado. Isso funciona bem para operações de transformação amplo.  
  
 Para operações que dependem de examinar cada nó em um fluxo de nó XAML, você normalmente não usa <xref:System.Xaml.XamlServices.Transform%2A>. Em vez disso, você precisará definir sua própria série de operação carga caminho salvar caminho e levantar sua própria lógica. Em um dos caminhos, use um par de gravador XAML/leitor XAML em torno de seu próprio loop de nó. Por exemplo, carregar o XAML inicial usando <xref:System.Xaml.XamlXmlReader> e intervir em nós com sucessivas <xref:System.Xaml.XamlXmlReader.Read%2A> chamadas. Operar no nível do fluxo de nó XAML que você pode agora ajustar nós individuais (tipos, membros, outros nós) para aplicar uma transformação, ou deixe o nó como-está. Em seguida, envie o nó em diante, para o relevantes `Write` API de um <xref:System.Xaml.XamlObjectWriter> e gravar o objeto. Para obter mais informações, consulte [Noções básicas sobre XAML Stream estruturas e conceitos nó](understanding-xaml-node-stream-structures-and-concepts.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xaml.XamlObjectWriter>
- <xref:System.Xaml.XamlServices>
- [Serviços XAML](index.md)
