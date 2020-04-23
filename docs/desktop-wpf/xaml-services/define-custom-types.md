---
title: Definir tipos personalizados para uso com os serviços XAML do .NET
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: ff7e4229450e801a6d618c5141efde8cdcbef03d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071853"
---
# <a name="define-custom-types-for-use-with-net-xaml-services"></a>Defina tipos personalizados para uso com serviços .NET XAML

Quando você define tipos personalizados que são objetos de negócios ou são tipos que não têm uma dependência de frameworks específicos, existem certas práticas recomendadas para XAML que você pode seguir. Se você seguir essas práticas, o .NET XAML Services e seus leitores XAML e escritores XAML podem descobrir as características XAML do seu tipo e dar-lhe uma representação apropriada em um fluxo de nó XAML usando o sistema tipo XAML. Este tópico descreve as práticas recomendadas para definições de tipo, definições de membros e atribuição de CLR de tipos ou membros.

## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Padrões de constructor e definições de tipo para XAML

Para ser instanciado como um elemento de objeto no XAML, uma classe personalizada deve atender aos seguintes requisitos:

- A classe personalizada deve ser pública e deve expor um construtor público sem parâmetros. (Consulte a seção a seguir para ver as observações sobre estruturas.)

- A classe personalizada não deve ser uma classe aninhada. O "ponto" extra no caminho de nome completo torna a divisão de namespace de classe ambígua e interfere com outros recursos XAML, como propriedades anexadas.
Se um objeto pode ser instanciado como um elemento objeto, o objeto criado pode preencher o formulário de elemento de propriedade de quaisquer propriedades que levem o objeto como seu tipo subjacente.

Você ainda pode fornecer valores de objeto para tipos que não atendem a esses critérios, se você habilitar um conversor de valor. Para obter mais informações, consulte [Type Converters e Extensões de Marcação para XAML](type-converters-and-markup-extensions.md).

### <a name="structures"></a>Estruturas

Estruturas são sempre capazes de ser construídas em XAML, por definição CLR. Isso porque um compilador CLR cria implicitamente um construtor sem parâmetros para uma estrutura. Este construtor inicializa todos os valores de propriedade para seus padrões.

Em alguns casos, o comportamento de construção padrão para uma estrutura não é desejável. Isso pode ser porque a estrutura se destina a preencher valores e funcionar conceitualmente como uma união. Como união, os valores contidos podem ter interpretações mutuamente exclusivas e, portanto, nenhuma de suas propriedades são definidas. Um exemplo dessa estrutura no vocabulário da <xref:System.Windows.GridLength>WPF é. Tais estruturas devem implementar um conversor de tipo para que os valores possam ser expressos na forma de atributo, utilizando convenções de cordas que criam as diferentes interpretações ou modos dos valores estruturais. A estrutura também deve expor comportamento semelhante para construção de código através de um construtor não-parâmetro.

### <a name="interfaces"></a>Interfaces

Interfaces podem ser usadas como tipos subjacentes de membros. O sistema do tipo XAML verifica a lista atribuída e espera que o objeto fornecido como valor possa ser atribuído à interface. Não há nenhum conceito de como a interface deve ser apresentada como um tipo XAML, desde que um tipo de atribuição relevante suporte aos requisitos de construção XAML.

### <a name="factory-methods"></a>Métodos de fábrica

Os métodos de fábrica são um recurso XAML 2009. Eles modificam o princípio XAML de que os objetos devem ter construtores sem parâmetros. Os métodos de fábrica não estão documentados neste artigo. Ver [x:Diretiva FactoryMethod](xfactorymethod-directive.md).

## <a name="enumerations"></a>Enumerações

Enumerações têm comportamento de conversão de tipo nativo XAML. Os nomes constantes de enumeração especificados no XAML são resolvidos contra o tipo de enumeração subjacente e retornam o valor de enumeração a um escritor de objetos XAML.

O XAML suporta um uso no estilo <xref:System.FlagsAttribute> de bandeiras para enumerações aplicadas. Para obter mais informações, consulte [XAML Sintaxe em detalhes](../../framework/wpf/advanced/xaml-syntax-in-detail.md). ([XAML Sintaxe em detalhes](../../framework/wpf/advanced/xaml-syntax-in-detail.md) é escrita para o público WPF, mas a maioria das informações nesse tópico é relevante para xaml que não é específico para uma estrutura de implementação específica.)

## <a name="member-definitions"></a>Definições de membros

Os tipos podem definir membros para o uso do XAML. É possível para os tipos definir membros que são xaml-utilizáveis mesmo que esse tipo específico não seja utilizável em XAML. Isso é possível por causa da herança clr. Desde que algum tipo que herde o membro suporte o uso de XAML como um tipo, e o membro suporte o uso de XAML para o seu tipo subjacente ou tenha uma sintaxe XAML nativa disponível, esse membro é utilizável em XAML.

### <a name="properties"></a>Propriedades

Se você definir propriedades como uma propriedade CLR pública usando os padrões típicos `get` de CLR e `set` acessórios e palavras-chave apropriadas à linguagem, o sistema de tipo XAML pode relatar a propriedade como um membro com informações apropriadas fornecidas para <xref:System.Xaml.XamlMember> propriedades, como <xref:System.Xaml.XamlMember.IsReadPublic%2A> e <xref:System.Xaml.XamlMember.IsWritePublic%2A>.

Propriedades específicas podem habilitar uma sintaxe de texto aplicando <xref:System.ComponentModel.TypeConverterAttribute>. Para obter mais informações, consulte [Type Converters e Extensões de Marcação para XAML](type-converters-and-markup-extensions.md).

Na ausência de uma sintaxe de texto ou conversão XAML nativa e na ausência de outra indireção, como um uso de extensão de marcação, o tipo de propriedade (no<xref:System.Xaml.XamlMember.TargetType%2A> sistema do tipo XAML) deve ser capaz de retornar uma instância a um escritor de objetos XAML tratando o tipo de destino como um tipo CLR.

Se usar xAML 2009, [x:Extensão de marcação de referência](xreference-markup-extension.md) pode ser usado para fornecer valores se as considerações anteriores não forem atendidas; no entanto, isso é mais um problema de uso do que um problema de definição de tipo.

### <a name="events"></a>Eventos

Se você definir eventos como um evento CLR público, o sistema do <xref:System.Xaml.XamlMember.IsEvent%2A> `true`tipo XAML pode relatar o evento como um membro com como . A fiação dos manipuladores de eventos não está dentro do escopo dos recursos de Serviços XAML .NET; a fiação é deixada para estruturas e implementações específicas.

### <a name="methods"></a>Métodos

O código inline para métodos não é um recurso XAML padrão. Na maioria dos casos, você não faz referência direta aos membros do método xaml, e o papel dos métodos no XAML é apenas fornecer suporte para padrões XAML específicos. [x:FactoryMethod Directive](xfactorymethod-directive.md) é uma exceção.

### <a name="fields"></a>Campos

As diretrizes de design da CLR desencorajam campos não estáticos. Para campos estáticos, você pode acessar valores de campo estáticos somente através de [x:Extensão de marcação estática;](xstatic-markup-extension.md) neste caso, você não está fazendo nada especial na definição CLR para expor um campo para [x:usos estáticos.](xstatic-markup-extension.md)

## <a name="attachable-members"></a>Membros anexáveis

Os membros anexáveis são expostos ao XAML através de um padrão de método acessório em um tipo definidor. O tipo definidor em si não precisa ser xaml-utilizável como um objeto. Na verdade, um padrão comum é declarar uma classe de serviço cujo papel é possuir o membro acoplado e implementar os comportamentos relacionados, mas não servir a nenhuma outra função, como uma representação de UI. Para as seções a seguir, o espaço reservado *PropertyName* representa o nome do membro anexado. Esse nome deve ser válido na [Gramática XamlName](xamlname-grammar.md).

Tenha cuidado com as colisões de nomes entre esses padrões e outros métodos de um tipo. Se existe um membro que corresponde a um dos padrões, ele pode ser interpretado como um caminho de uso de membro anexado por um processador XAML, mesmo que essa não fosse sua intenção.

#### <a name="the-getpropertyname-accessor"></a>O acessório GetPropertyName

A assinatura `GetPropertyName` do acessório deve ser:

`public static object GetPropertyName(object target)`

- O objeto `target` pode ser especificado como um tipo mais específico na sua implementação. Você pode usá-lo para escopo do uso do seu membro anexado; os usos fora do escopo pretendido lançarão exceções de elenco inválidas que são então superadas por um erro de análise XAML. O nome `target` do parâmetro não é `target` um requisito, mas é nomeado por convenção na maioria das implementações.

- O valor retornado pode ser especificado como um tipo mais específico na sua implementação.

Para suportar <xref:System.ComponentModel.TypeConverter> uma sintaxe de texto habilitada para <xref:System.ComponentModel.TypeConverterAttribute> o `GetPropertyName` uso de atributo do membro acopnível, aplique-se ao acessório. Aplicar-se `get` ao em `set` vez do pode parecer não intuitivo; no entanto, esta convenção pode apoiar o conceito de membros acopladores somente de leitura que são serializáveis, o que é útil em cenários de designer.

#### <a name="the-setpropertyname-accessor"></a>O acessório SetPropertyName

A assinatura `SetPropertyName` do acessório deve ser:

`public static void SetPropertyName(object target, object value)`

- O `target` objeto pode ser especificado como um tipo mais específico em sua implementação, com a mesma lógica e consequências descritas na seção anterior.

- O objeto `value` pode ser especificado como um tipo mais específico na sua implementação.

Lembre-se que o valor para este método é a entrada proveniente do uso xaml, tipicamente na forma de atributo. A partir do formulário de atributo deve haver suporte ao `GetPropertyName`conversor de valor para uma sintaxe de texto, e você atribui no acessório.

### <a name="attachable-member-stores"></a>Lojas de membros acopladas

Os métodos do acessório normalmente não são suficientes para fornecer um meio de colocar valores de membros anexáveis em um gráfico de objeto, ou para recuperar valores do gráfico do objeto e serializá-los corretamente. Para fornecer essa funcionalidade, os `target` objetos nas assinaturas do acessório anterior devem ser capazes de armazenar valores. O mecanismo de armazenamento deve ser consistente com o princípio do membro acoplado de que o membro é anexado a alvos onde o membro anexado não está na lista de membros. .NET XAML Services fornece uma técnica de implementação <xref:System.Xaml.IAttachedPropertyStore> <xref:System.Xaml.AttachablePropertyServices>para lojas de membros anexáveis através das APIs e . <xref:System.Xaml.IAttachedPropertyStore>é usado pelos escritores XAML para descobrir a implementação da `target` loja, e deve ser implementado no tipo que é o dos acessórios. As <xref:System.Xaml.AttachablePropertyServices> APIs estáticas são usadas dentro do corpo dos acessórios <xref:System.Xaml.AttachableMemberIdentifier>e referem-se ao membro anexável pelo seu .

## <a name="xaml-related-clr-attributes"></a>Atributos CLR relacionados ao XAML

Atribuir corretamente seus tipos, membros e assembléias é importante para relatar as informações do sistema do tipo XAML aos Serviços .NET XAML. O relatório das informações do sistema do tipo XAML é relevante se uma das seguintes situações se aplicar:

- Você pretende seus tipos de uso com sistemas XAML que são diretamente baseados em leitores XAML serviços .NET e escritores XAML.
- Você define ou usa uma estrutura de utilização de XAML baseada nos leitores XAML e escritores XAML.

Para obter uma listagem de cada atributo relacionado ao XAML relevante para o suporte xaml de seus tipos [personalizados, consulte Atributos CLR relacionados à XAML para tipos e bibliotecas personalizados](clr-attributes-with-custom-types-and-libraries.md).

## <a name="usage"></a>Uso

O uso de tipos personalizados exige que o autor da marcação deva mapear um prefixo para o espaço de nome de montagem e CLR que contenha o tipo personalizado. Este procedimento não está documentado neste tópico.

## <a name="access-level"></a>Nível de acesso

O XAML fornece um meio de carregar `internal` e instanciar tipos que têm um nível de acesso. Esse recurso é fornecido para que o código do usuário possa definir seus próprios tipos e, em seguida, instanciar essas classes a partir da marcação que também faz parte do mesmo escopo de código do usuário.

Um exemplo do WPF é sempre <xref:System.Windows.Controls.UserControl> que o código do usuário define um que se destina a refatorar um comportamento de IU, mas não como parte de qualquer mecanismo de extensão possível que possa estar implícito declarando a classe de suporte com `public` nível de acesso. Tal <xref:System.Windows.Controls.UserControl> pode ser declarado `internal` com acesso se o código de respaldação for compilado no mesmo conjunto a partir do qual é referenciado como um tipo XAML.

Para um aplicativo que carrega XAML <xref:System.Xaml.XamlObjectWriter>sob total `internal` confiança e usa, as classes de carregamento com nível de acesso estão sempre habilitadas.

Para um aplicativo que carrega XAML sob confiança parcial, você <xref:System.Xaml.Permissions.XamlAccessLevel> pode controlar as características do nível de acesso usando a API. Além disso, os mecanismos de diferimento (como o sistema de modelo sufiaba) devem ser capazes de propagar quaisquer permissões de nível de acesso e preservá-las para eventuais avaliações de tempo de execução; isso é tratado internamente <xref:System.Xaml.Permissions.XamlAccessLevel> passando as informações.

### <a name="wpf-implementation"></a>Implementação do WPF

O WPF XAML usa um modelo de acesso de confiança parcial onde <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> se o BAML for carregado sob confiança parcial, o acesso é restrito para o conjunto que é a fonte BAML. Para o adiamento, o <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> WPF usa como mecanismo para passar as informações de nível de acesso.

Na terminologia WPF XAML, um *tipo interno* é um tipo que é definido pelo mesmo conjunto que também inclui o xaml de referência. Esse tipo pode ser mapeado através de um namespace XAML que deliberadamente `xmlns:local="clr-namespace:WPFApplication1"`omite a montagem= parte de um mapeamento, por exemplo, . Se o BAML faz referência a `internal` um tipo interno `GeneratedInternalTypeHelper` e esse tipo tem nível de acesso, isso gera uma classe para o conjunto. Se você quiser `GeneratedInternalTypeHelper`evitar, você `public` deve usar o nível de acesso, ou deve fatorar a classe relevante em uma montagem separada e tornar essa montagem dependente.

## <a name="see-also"></a>Confira também

- [Atributos CLR relacionados a XAML para tipos personalizados e bibliotecas](clr-attributes-with-custom-types-and-libraries.md)
- [Serviços XAML](../../../api/index.md)
