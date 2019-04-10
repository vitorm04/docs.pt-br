---
title: Contexto do esquema XML padrão e contexto do esquema XAML WPF
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: 0d6a0aa80d8490c509fa9036f88d4f6863ff040c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295595"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>Contexto do esquema XML padrão e contexto do esquema XAML WPF
Um contexto de esquema XAML é uma entidade conceitual que qualifica como uma produção de XAML que usa um vocabulário específico do XAML interage com o objeto de comportamento, incluindo como resolve o mapeamento de tipo, como assemblies são carregados, como determinado leitor e gravador de gravação as configurações são interpretadas. Este tópico descreve os recursos de serviços de XAML do .NET Framework e o contexto do esquema XAML padrão associados, que se baseia no sistema de tipos CLR. Este tópico também descreve o contexto do esquema XAML que é usado para o WPF.  
  
## <a name="default-xaml-schema-context"></a>Contexto de esquema XAML padrão  
 Serviços de XAML do .NET framework implementa e usa um contexto de esquema XAML padrão. O comportamento de contexto do esquema XAML padrão nem sempre é totalmente visível na API do <xref:System.Xaml.XamlSchemaContext> classe. No entanto, em muitos casos o comportamento que influencia o contexto do esquema XAML padrão é observável por meio de uma API comum do sistema de tipo XAML, como os membros da <xref:System.Xaml.XamlMember> ou <xref:System.Xaml.XamlType>, ou por meio de APIs expostas em leitores XAML e gravadores XAML que estão usando o contexto do esquema XAML padrão.  
  
 Você pode criar uma <xref:System.Xaml.XamlSchemaContext> que encapsula o comportamento padrão chamando o <xref:System.Xaml.XamlSchemaContext> construtor. Isso cria explicitamente o contexto do esquema XAML padrão. O mesmo contexto de esquema XAML padrão é criado implicitamente, se você inicializar um leitor XAML ou gravador XAML usando as APIs que não utilizam explicitamente um <xref:System.Xaml.XamlSchemaContext> parâmetro de entrada.  
  
 O contexto do esquema XAML padrão depende de reflexão do CLR para o seu comportamento de mapeamento de tipo. Isso inclui examinando o CLR definindo <xref:System.Type>e relacionadas <xref:System.Reflection.PropertyInfo> ou <xref:System.Reflection.MethodInfo>. Além disso, a atribuição de CLR em tipos ou membros é usada para preencher as especificações para o tipo XAML ou informações de membro XAML que usa o tipo subjacente de CLR. O contexto do esquema XAML padrão não requer técnicas de extensão do sistema de tipo, como o `Invoker` padrão, porque as informações necessárias estão disponíveis no sistema de tipos CLR.  
  
 Para a lógica de carregamento do assembly, o contexto do esquema XAML padrão baseia-se principalmente em quaisquer valores de assembly fornecidos nos mapeamentos de namespace XAML. Além disso, <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> pode indicar um assembly para carregar, para cenários como o carregamento de tipos internos.  
  
## <a name="wpf-xaml-schema-context"></a>Contexto de esquema XAML WPF  
 O contexto do esquema XAML WPF é descrito neste tópico, porque a implementação do WPF fornece uma ilustração interessante dos tipos de recursos que podem ser introduzidos com a implementação de um contexto de esquema XAML não padrão. Além disso, o conceito de contexto de esquema XAML não é discutido muito na documentação do WPF que trata o WPF XAML; o comportamento que o contexto do esquema XAML permite que somente pode ser totalmente compreensível se integrado com uma discussão de como funciona o contexto do esquema XAML padrão. O contexto do esquema XAML WPF implementa o comportamento a seguir.  
  
 **Substituições de pesquisa:** O WPF tem alguns modelos de conteúdo para o XAML em que não há propriedades de conteúdo XAML que funcionam sem sendo <xref:System.Windows.Markup.ContentPropertyAttribute> atribuído. <xref:System.Xaml.XamlType.LookupContentProperty%2A> substituições para WPF implementam esse comportamento.  
  
 **Adiamento para expressões do WPF:** WPF apresenta várias classes de expressão que adiar um valor até que um contexto de tempo de execução está disponível. Além disso, a expansão do modelo é um comportamento de tempo de execução que se baseia em técnicas de adiamento.  
  
 **Digite as otimizações de pesquisa do sistema:** O WPF tem um amplo XAML vocabulário e modelo de objeto, incluindo definições de membro de classe base que herdam a literalmente centenas de classes definidas pelo WPF. Além disso, o próprio WPF é distribuído entre vários assemblies. WPF otimiza sua pesquisa do tipo usando tabelas de pesquisa e outras técnicas. Isso fornece melhorias de desempenho sobre o contexto do esquema XAML padrão e sua pesquisa de texto com base em CLR. Em casos em que não existem tipos em uma tabela de pesquisa, o comportamento usa técnicas de contexto de esquema XAML que são semelhantes para o contexto de esquema XAML padrão.  
  
 **Extensão XamlType e XamlMember:** O WPF estende os conceitos de propriedades com propriedades de dependência e conceitos de eventos com eventos roteados. Para fornecer maior visibilidade desses conceitos para operações de processamento de XAML, o WPF estende <xref:System.Xaml.XamlType> e <xref:System.Xaml.XamlMember>e adiciona as propriedades internas que relatam a propriedade de dependência e roteado características do evento.  
  
### <a name="accessing-the-wpf-xaml-schema-context"></a>Acessando o contexto do esquema XAML WPF  
 Se você estiver usando técnicas XAML que se baseiam no WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ou <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>, o contexto do esquema XAML WPF já está em uso nesses leitor XAML e as implementações do gravador XAML.  
  
 Se você estiver usando outro leitor XAML ou implementações de gravador XAML que não sejam inicializados com o contexto do esquema XAML WPF, você poderá obter um trabalho do WPF XAML contexto do esquema de <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>. Em seguida, você pode usar esse valor como a inicialização para outra API que usam um <xref:System.Xaml.XamlSchemaContext>. Por exemplo, você poderia chamar <xref:System.Xaml.XamlXmlReader.%23ctor%2A> para inicialização e passar o contexto do esquema XAML WPF. Ou você pode usar o contexto do esquema XAML WPF para operações do sistema de tipo XAML. Isso pode incluir a inicialização de construção de uma <xref:System.Xaml.XamlType> ou <xref:System.Xaml.XamlMember>, ou chamar <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>.  
  
 Observe que se você acessar determinados aspectos do WPF XAML de um puro perspectivas de fluxo de nó XAML, alguns dos recursos de framework WPF podem não ter atua ainda. Por exemplo, modelos para controles do WPF não são aplicados ainda. Portanto, se você acessar uma propriedade que pode ser preenchida com uma árvore visual completa no tempo de execução, você pode ver apenas um valor da propriedade que faz referência a um modelo. O contexto de serviço fornecido para extensões de marcação do WPF também não pode ser preciso se de uma situação de tempo de execução não fornecido e pode resultar em exceções ao tentar gravar um grafo de objeto.  
  
## <a name="xaml-and-assembly-loading"></a>XAML e o carregamento de Assembly  
 Carregamento de XAML e serviços de XAML do .NET Framework do assembly se integra com o conceito definido pelo CLR de <xref:System.AppDomain>. Um contexto de esquema XAML interpreta como carregar assemblies ou localizar tipos em tempo de execução ou tempo de design, com base no uso de <xref:System.AppDomain> e outros fatores. A lógica é ligeiramente diferente dependendo se o XAML é XAML flexível para um leitor XAML, é o XAML compilado em uma DLL por `XamlBuildTask`, ou BAML gerado do WPF `PresentationBuildTask`.  
  
 O contexto do esquema XAML para WPF integra-se com o modelo de aplicativo do WPF, que por sua vez usa <xref:System.AppDomain> , bem como outros fatores que são os detalhes de implementação de WPF.  
  
#### <a name="xaml-reader-input-loose-xaml"></a>Entrada do leitor XAML (XAML flexível)  
  
1. O contexto do esquema XAML itera por meio de <xref:System.AppDomain> do aplicativo, procurando por um assembly já carregado que corresponde a todos os aspectos do nome, começando do mais recentemente assembly carregado. Se uma correspondência for encontrada, esse assembly é usado para resolução.  
  
2. Caso contrário, uma das técnicas a seguir com base em CLR <xref:System.Reflection.Assembly> API são usados para carregar um assembly:  
  
    -   Se o nome é qualificado no mapeamento, chame <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> no nome qualificado.  
  
    -   Se a etapa anterior falhar, use o nome curto (e o token de chave pública, se presente) para chamar <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
    -   Se o nome não for qualificado no mapeamento, chame <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
#### <a name="xamlbuildtask"></a>XamlBuildTask  
 `XamlBuildTask` é usado para o Windows Communication Foundation (WCF) e o Windows Workflow Foundation.  
  
 Observe que faz referência a assembly por meio de `XamlBuildTask` são sempre totalmente qualificado.  
  
1. Chamar <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> no nome qualificado.  
  
2. Se a etapa anterior falhar, use o nome curto (e o token de chave pública, se presente) para chamar <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)  
 Há dois aspectos para carregamento de assemblies para BAML: carregar o assembly inicial que contém o BAML como um componente e carregar os assemblies de suporte de tipo para qualquer tipos referenciados pela produção de BAML.  
  
##### <a name="assembly-load-for-initial-markup"></a>Carregamento de assembly para marcação inicial:  
 A referência ao assembly a ser carregado a marcação de sempre é não qualificada.  
  
1. O contexto do esquema XAML WPF itera por meio de <xref:System.AppDomain> do aplicativo WPF, procurando por um assembly já carregado que corresponde a todos os aspectos do nome, começando do mais recentemente assembly carregado. Se uma correspondência for encontrada, esse assembly é usado para resolução.  
  
2. Se a etapa anterior falhar, use o nome curto (e o token de chave pública, se presente) para chamar <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
##### <a name="assembly-references-by-baml-types"></a>Referências de assembly por tipos BAML:  
 Referências de assembly para tipos usados na produção BAML são sempre totalmente qualificadas, como uma saída de tarefa de build.  
  
1. O contexto do esquema XAML WPF itera por meio de <xref:System.AppDomain> do aplicativo WPF, procurando por um assembly já carregado que corresponde a todos os aspectos do nome, começando do mais recentemente assembly carregado. Se uma correspondência for encontrada, esse assembly é usado para resolução.  
  
2. Caso contrário, uma das técnicas a seguir é usada para carregar um assembly:  
  
    -   Chamar <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> no nome qualificado.  
  
    -   Se um nome curto + a combinação de token de chave pública corresponder ao assembly que o BAML foi carregado de, use esse assembly.  
  
    -   Use o nome curto + token de chave pública para chamar <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- [Noções básicas sobre estruturas e conceitos do fluxo de nó XAML](understanding-xaml-node-stream-structures-and-concepts.md)
