---
title: Contexto do esquema XML padrão e contexto do esquema XAML WPF
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: 2e92372de61230a98a02282cc28fc3f479cd94eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071860"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>Contexto do esquema XML padrão e contexto do esquema XAML WPF
Um contexto de esquema XAML é uma entidade conceitual que qualifica como uma produção XAML que usa um vocabulário XAML particular interage com o comportamento de escrita de objetos, incluindo como o mapeamento de tipos resolve, como os conjuntos são carregados, como certas configurações de leitor e escritor são interpretadas. Este tópico descreve os recursos do .NET XAML Services e o contexto de esquema XAML padrão associado, que é baseado no sistema do tipo CLR. Este tópico também descreve o contexto do esquema XAML que é usado para WPF.

## <a name="default-xaml-schema-context"></a>Contexto padrão do esquema XAML

.NET XAML Services implementa e usa um contexto padrão de esquema XAML. O comportamento padrão do contexto do esquema XAML nem sempre <xref:System.Xaml.XamlSchemaContext> é totalmente visível na API da classe. No entanto, em muitos casos, o comportamento que o contexto padrão do esquema XAML influencia é <xref:System.Xaml.XamlMember> observável através de API comum do sistema do tipo XAML, como membros ou <xref:System.Xaml.XamlType>, ou através de APIs expostas em leitores XAML e escritores XAML que estão usando o contexto padrão do esquema XAML.

Você pode <xref:System.Xaml.XamlSchemaContext> criar um que encapsula o <xref:System.Xaml.XamlSchemaContext> comportamento padrão chamando o construtor. Isso cria explicitamente o contexto padrão do esquema XAML. O mesmo contexto padrão do esquema XAML é criado implicitamente, se você inicializar um leitor XAML <xref:System.Xaml.XamlSchemaContext> ou um escritor XAML usando APIs que não tomam explicitamente um parâmetro de entrada.

O contexto padrão do esquema XAML depende da reflexão CLR para seu comportamento de mapeamento de tipo. Isso inclui examinar a CLR <xref:System.Type>definitiva, e relacionada <xref:System.Reflection.PropertyInfo> ou <xref:System.Reflection.MethodInfo>. Além disso, a atribuição clr sobre tipos ou membros é usada para preencher as especificidades para informações do tipo XAML ou membros XAML que usam o tipo de backup CLR. O contexto padrão do esquema XAML não requer técnicas de extensão do sistema de tipo, como o `Invoker` padrão, porque as informações necessárias estão disponíveis no sistema do tipo CLR.

Para a lógica de carregamento de montagem, o contexto padrão do esquema XAML depende principalmente de quaisquer valores de montagem fornecidos em mapeamentos de namespace XAML. Além <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> disso, pode sugerir um conjunto para carregar, para cenários como carregar tipos internos.

## <a name="wpf-xaml-schema-context"></a>Contexto de esquema Do WPF XAML

O contexto do esquema WPF XAML é descrito neste tópico porque a implementação do WPF fornece uma ilustração interessante dos tipos de recursos que podem ser introduzidos implementando um contexto de esquema XAML não padrão. Além disso, o conceito de contexto do esquema XAML não é muito discutido na documentação do WPF que aborda o WPF XAML; o comportamento que o contexto de esquema XAML permite só pode ser totalmente compreensível se integrado a uma discussão de como o contexto padrão do esquema XAML funciona. O contexto do esquema WPF XAML implementa o seguinte comportamento.

**As substituições de lookup:** O WPF tem alguns modelos de conteúdo para XAML <xref:System.Windows.Markup.ContentPropertyAttribute> onde há propriedades de conteúdo XAML que funcionam sem serem atribuídas. <xref:System.Xaml.XamlType.LookupContentProperty%2A>substituições para a WPF implementar esse comportamento.

**Diferimento para expressões WPF:** O WPF apresenta várias classes de expressão que adiam um valor até que um contexto de tempo de execução esteja disponível. Além disso, a expansão do modelo é um comportamento de tempo de execução que se baseia em técnicas de adiamento.

**Digite otimizações de visualização do sistema:** O WPF tem um extenso modelo de vocabulário e objeto XAML, incluindo definições de membros de classe base que herdam literalmente centenas de classes definidas pelo WPF. Além disso, o próprio WPF está espalhado por várias assembléias. O WPF otimiza sua busca de tipo usando tabelas de busca e outras técnicas. Isso fornece melhorias de desempenho em relação ao contexto padrão do esquema XAML e sua pesquisa de tipo baseada em CLR. Nos casos em que os tipos não existem em uma tabela de pesquisa, o comportamento usa técnicas de contexto de esquema XAML semelhantes ao contexto padrão do esquema XAML.

**Extensão XamlType e XamlMember:** O WPF amplia os conceitos de propriedade com propriedades de dependência e conceitos de eventos com eventos roteados. Para dar a esses conceitos maior visibilidade às operações <xref:System.Xaml.XamlType> <xref:System.Xaml.XamlMember>de processamento XAML, o WPF amplia e , e adiciona propriedades internas que relatam propriedade de dependência e características de eventos roteados.

### <a name="accessing-the-wpf-xaml-schema-context"></a>Acessando o contexto do esquema WPF XAML

Se você estiver usando técnicas XAML <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> baseadas no WPF ou <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>, o contexto do esquema WPF XAML já está em uso nessas implementações de leitor XAML e escritor XAML.

Se você estiver usando outras implementações de leitor XAML ou escritor XAML que não inicializem com o contexto do esquema WPF <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>XAML, você poderá obter um contexto de esquema WPF XAML em funcionamento a partir de . Em seguida, você pode usar esse valor como <xref:System.Xaml.XamlSchemaContext>inicialização para outraS API que usam um . Por exemplo, você <xref:System.Xaml.XamlXmlReader.%23ctor%2A> pode pedir inicialização e passar o contexto do esquema WPF XAML. Ou você pode usar o contexto do esquema WPF XAML para operações do sistema tipo XAML. Isso pode incluir a <xref:System.Xaml.XamlType> inicialização da construção de um ou <xref:System.Xaml.XamlMember>, ou chamada <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>.

Observe que se você acessar certos aspectos do WPF XAML a partir de uma perspectiva de fluxo de nó XAML pura, alguns dos recursos de framework do WPF podem não ter agido ainda. Por exemplo, os modelos WPF para controles ainda não são aplicados. Assim, se você acessar uma propriedade que no tempo de execução pode ser preenchida com uma árvore visual completa, você só poderá ver um valor de propriedade que faça referência a um modelo. O contexto de serviço fornecido para extensões de marcação WPF também pode não ser preciso se fornecido a partir de uma situação sem tempo de execução, e pode resultar em exceções ao tentar escrever um gráfico de objetos.

## <a name="xaml-and-assembly-loading"></a>Carregamento xaml e montagem

O carregamento de montagem para serviços XAML e .NET XAML integra-se ao conceito definido pela CLR de <xref:System.AppDomain>. Um contexto de esquema XAML interpreta como carregar conjuntos ou encontrar tipos em tempo <xref:System.AppDomain> de execução ou tempo de projeto, com base no uso e outros fatores. A lógica é ligeiramente diferente dependendo se o XAML é XAML solto para um leitor `XamlBuildTask`XAML, é XAML `PresentationBuildTask`compilado em um DLL por , ou é BAML gerado por WPF'

O contexto do esquema XAML para WPF integra-se ao modelo <xref:System.AppDomain> de aplicação WPF, que por sua vez usa bem como outros fatores que são detalhes de implementação do WPF.

#### <a name="xaml-reader-input-loose-xaml"></a>Entrada do leitor XAML (XAML solta)

01. O contexto do esquema XAML itera através do <xref:System.AppDomain> aplicativo, procurando um conjunto já carregado que corresponda a todos os aspectos do nome, a partir do conjunto mais recente carregado. Se for encontrada uma correspondência, essa montagem é usada para resolução.

02. Caso contrário, uma das seguintes <xref:System.Reflection.Assembly> técnicas baseadas na API CLR é usada para carregar um conjunto:

    - Se o nome for qualificado <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> no mapeamento, ligue para o nome qualificado.

    - Se a etapa anterior falhar, use o nome curto (e <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>o token de chave pública, se estiver presente) para chamar .

    - Se o nome não for qualificado <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>no mapeamento, ligue .

#### <a name="xamlbuildtask"></a>XamlBuildTask

`XamlBuildTask`é usado para o Windows Communication Foundation (WCF) e o Windows Workflow Foundation.

Observe que as `XamlBuildTask` referências de montagem são sempre totalmente qualificadas.

1. Ligue <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> para o nome qualificado.

2. Se a etapa anterior falhar, use o nome curto (e <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>o token de chave pública, se estiver presente) para chamar .

#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)

Existem dois aspectos para o carregamento de montagem para BAML: carregar o conjunto inicial que contém o BAML como um componente e carregar os conjuntos de suporte de tipo para quaisquer tipos referenciados pela produção BAML.

##### <a name="assembly-load-for-initial-markup"></a>Carga de montagem para marcação inicial:

A referência à montagem para carregar a marcação é sempre desqualificada.

1. O contexto do esquema WPF XAML <xref:System.AppDomain> itera através do aplicativo WPF, procurando um conjunto já carregado que corresponda a todos os aspectos do nome, a partir do conjunto mais recentecarregado. Se for encontrada uma correspondência, essa montagem é usada para resolução.

2. Se a etapa anterior falhar, use o nome curto (e <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>o token de chave pública, se estiver presente) para chamar .

##### <a name="assembly-references-by-baml-types"></a>Referências de montagem por tipos BAML:

As referências de montagem para os tipos utilizados na produção baml são sempre totalmente qualificadas, como uma saída da tarefa de construção.

01. O contexto do esquema WPF XAML <xref:System.AppDomain> itera através do aplicativo WPF, procurando um conjunto já carregado que corresponda a todos os aspectos do nome, a partir do conjunto mais recentecarregado. Se for encontrada uma correspondência, essa montagem é usada para resolução.

02. Caso contrário, uma das seguintes técnicas é usada para carregar um conjunto:

    - Ligue <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> para o nome qualificado.
  
    - Se uma combinação de token de chave curta + chave pública corresponder ao conjunto do qual o BAML foi carregado, use esse conjunto.

    - Use nome curto + token <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>de chave pública para chamar .

## <a name="see-also"></a>Confira também

- [Noções básicas sobre estruturas e conceitos do fluxo de nó XAML](understanding-xaml-node-stream-structures-and-concepts.md)
