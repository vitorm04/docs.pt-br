---
title: Leitura e gravação XAML básico e de classe de serviços XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: 27c7a45a45e8bbe3594813b29344d1548eecda5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565906"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>Leitura e gravação XAML básico e de classe de serviços XAML
<xref:System.Xaml.XamlServices> é uma classe fornecida pelo serviços XAML do .NET Framework que pode ser usado para cenários de XAML que não necessitam de acesso específico para o fluxo do nó XAML ou informações do sistema de tipo XAML obtido em nós. <xref:System.Xaml.XamlServices> API pode ser resumida como o seguinte: `Load` ou `Parse` para dar suporte a um caminho de carregamento do XAML, `Save` para dar suporte a uma XAML salvar caminho, e `Transform` para fornecer uma técnica que ingressa em um caminho de carregar e salvar caminho. `Transform` pode ser usado para alterar de um esquema XAML para outro. Este tópico resume cada essas classificações de API e descreve as diferenças entre as sobrecargas do método específico.  
  
<a name="load"></a>   
## <a name="load"></a>Carregamento  
 Várias sobrecargas de <xref:System.Xaml.XamlServices.Load%2A> implementar a lógica completa para um caminho de carga. O caminho de carga usa XAML em alguma forma e gera um fluxo do nó XAML. A maioria deles carregar use caminhos XAML em formato de arquivo de texto codificado em XML. No entanto, você também pode carregar um fluxo geral, ou você pode carregar uma fonte pré-carregados de XAML que já está contida em outro <xref:System.Xaml.XamlReader> implementação.  
  
 A sobrecarga mais simples para a maioria dos cenários é <xref:System.Xaml.XamlServices.Load%28System.String%29>. Essa sobrecarga tem um `fileName` parâmetro que é simplesmente o nome de um arquivo de texto que contém o XAML para carregar. Isso é apropriado para cenários de aplicativo, como aplicativos de confiança total que têm serializado anteriormente estado ou dados no computador local. Isso também é útil para estruturas de onde você está definindo o modelo de aplicativo e deseja carregar um dos arquivos padrão que define o comportamento do aplicativo, iniciando a interface do usuário ou outros recursos definidos pelo framework que usam XAML.  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29> tem cenários semelhantes. Essa sobrecarga pode ser útil se você tiver o usuário escolha arquivos para carregar, porque um <xref:System.IO.Stream> é uma saída frequente de outros <xref:System.IO> APIs que podem acessar um sistema de arquivos. Ou poderia acessar fontes XAML por meio de downloads assíncronos ou outras técnicas de rede que também fornecem um fluxo. (O carregamento de um fluxo ou a fonte selecionada pelo usuário pode ter implicações de segurança. Para obter mais informações, consulte [considerações sobre segurança XAML](../../../docs/framework/xaml-services/xaml-security-considerations.md).)  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29> e <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> são sobrecargas que dependem de leitores de formatos de versões anteriores do .NET Framework. Para usar essas sobrecargas, deve ter sido criada uma instância do leitor e utilizado seus `Create` API para carregar o XAML no formulário relevante (texto ou XML). Se você já tiver movido ponteiros de registro em outros leitores ou executada outras operações com eles, isso não é importante. A lógica de caminho de carga de <xref:System.Xaml.XamlServices.Load%2A> sempre processa XAML toda entrada de raiz para baixo. Cenários para essas sobrecargas podem incluir o seguinte:  
  
-   Design superfícies em que você fornecer XAML simples edição de recurso em um editor de texto XML específico existente.  
  
-   Variantes do núcleo <xref:System.IO> cenários, onde você usa os leitores dedicados para abrir os arquivos ou fluxos. Sua lógica executa verificação rudimentar ou processamento do conteúdo antes de tentar carregar como XAML.  
  
 Você pode carregar um arquivo ou fluxo ou você pode carregar um <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, ou <xref:System.Xaml.XamlReader> que encapsular sua entrada XAML Carregando com as APIs do leitor.  
  
 Internamente, cada uma das sobrecargas anteriores é basicamente <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>e transmitido <xref:System.Xml.XmlReader> é usado para criar um novo <xref:System.Xaml.XamlXmlReader>.  
  
 O `Load` assinatura que fornece mais avançadas cenários é <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>. Você pode usar essa assinatura para um dos seguintes casos:  
  
-   Você tiver definido sua própria implementação de um <xref:System.Xaml.XamlReader>.  
  
-   Você precisa especificar as configurações para <xref:System.Xaml.XamlReader> que variam das configurações padrão.  
  
 Exemplos de configurações não padrão estão definindo qualquer um dos seguintes: <xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>; <xref:System.Xaml.XamlReaderSettings.BaseUri%2A>; <xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>; <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>; <xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>. O leitor de padrão para <xref:System.Xaml.XamlServices> é <xref:System.Xaml.XamlXmlReader>. Se você fornecer sua própria <xref:System.Xaml.XamlXmlReader>, com as configurações, os seguintes são propriedades para definir o padrão não <xref:System.Xaml.XamlXmlReaderSettings>: <xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>; <xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>.  
  
<a name="parse"></a>   
## <a name="parse"></a>Parse  
 <xref:System.Xaml.XamlServices.Parse%2A> é como `Load` porque ele é um caminho de carga API que cria um fluxo do nó XAML de entrada XAML. No entanto, nesse caso, a entrada XAML é fornecida diretamente como uma cadeia de caracteres que contém o XAML para carregar. <xref:System.Xaml.XamlServices.Parse%2A> é uma abordagem superficial que é mais apropriada para cenários de aplicativo de cenários do framework. Para obter mais informações, consulte <xref:System.Xaml.XamlServices.Parse%2A>. <xref:System.Xaml.XamlServices.Parse%2A> é realmente apenas um encapsulado <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> chamada que envolve um <xref:System.IO.StringReader> internamente.  
  
<a name="save"></a>   
## <a name="save"></a>Salvar  
 Várias sobrecargas de <xref:System.Xaml.XamlServices.Save%2A> implementar salvar caminho. Todos os <xref:System.Xaml.XamlServices.Save%2A> métodos usam um gráfico de objeto como entrada e produzem saída como um fluxo de arquivos, ou <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> instância.  
  
 O objeto de entrada deve ser o objeto raiz de alguns representação de objeto. Isso pode ser a única raiz de um objeto de negócios, a raiz de uma árvore de objetos de uma página em um cenário de interface do usuário, a superfície de edição de trabalho de uma ferramenta de design ou outros conceitos do objeto raiz que são apropriados para cenários.  
  
 Em muitos cenários de árvore de objetos que você salvar está relacionado a uma operação original que carregado XAML com <xref:System.Xaml.XamlServices.Load%2A> ou com outra API implementado por um modelo de aplicativo do framework. Pode haver diferenças capturadas na árvore de objetos devido a alterações de estado, alterações em que seu aplicativo capturadas configurações de tempo de execução de um usuário, alterado XAML porque seu aplicativo é uma XAML design superfície, etc. Com ou sem alterações, o conceito de primeiro carregamento XAML da marcação e, em seguida, salvá-lo novamente e comparar as duas formas de marcação XAML às vezes é conhecido como uma representação de ida e volta do XAML.  
  
 O desafio com salvamento e serializar um objeto complexo que é definido em um formulário de marcação é atingir um equilíbrio entre a representação completa sem perda de informações, em vez de detalhamento que faz com que o XAML menos legível. Além disso, clientes diferentes para XAML podem ter diferentes definições ou as expectativas de como esse equilíbrio deve ser definido. O <xref:System.Xaml.XamlServices.Save%2A> APIs representam uma definição desse equilíbrio. O <xref:System.Xaml.XamlServices.Save%2A> APIs usam o contexto de esquema XAML disponível e as características do padrão com base em CLR do <xref:System.Xaml.XamlType>, <xref:System.Xaml.XamlMember>, e conceitos do sistema para determinar em que determinadas construções de fluxo do nó XAML podem ser de tipo de outros XAML intrínseco e XAML otimização quando eles são salvos para marcação. Por exemplo, <xref:System.Xaml.XamlServices> salvar caminhos pode usar o contexto do esquema padrão com base em CLR XAML para resolver <xref:System.Xaml.XamlType> para objetos, pode determinar um <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>e, em seguida, poderá omitir as marcas de elemento de propriedade quando eles gravam a propriedade de conteúdo XAML do objeto.  
  
<a name="transform"></a>   
## <a name="transform"></a>Transformar  
 <xref:System.Xaml.XamlServices.Transform%2A> Converte ou transforma XAML com a vinculação de um caminho de carregar e salvar caminho como uma única operação. Um contexto de esquema diferente ou o sistema de tipos diferentes de backup pode ser usado para <xref:System.Xaml.XamlReader> e <xref:System.Xaml.XamlWriter>, que é o que influencia como o XAML resultante é transformado. Isso funciona bem para operações de transformação amplo.  
  
 Para operações que dependem de examinar cada nó em um fluxo do nó XAML, você normalmente não usa <xref:System.Xaml.XamlServices.Transform%2A>. Em vez disso, você precisa definir sua própria série de operação carga caminho salvar caminho e interromper sua própria lógica. Em um dos caminhos, use um par de gravador do leitor/XAML XAML ao redor de seu próprio loop de nó. Por exemplo, carregar o XAML inicial usando <xref:System.Xaml.XamlXmlReader> e analisar os nós com sucessivas <xref:System.Xaml.XamlXmlReader.Read%2A> chamadas. Operando no nível de fluxo do nó XAML, você pode agora ajustar nós individuais (tipos, membros, outros nós) para aplicar uma transformação ou deixe o nó como-é. Em seguida, você envia o nó em diante para relevante `Write` API de um <xref:System.Xaml.XamlObjectWriter> e gravar o objeto. Para obter mais informações, consulte [Noções básicas sobre estruturas de fluxo de nó de XAML e conceitos](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xaml.XamlObjectWriter>  
 <xref:System.Xaml.XamlServices>  
 [Serviços XAML](../../../docs/framework/xaml-services/index.md)
