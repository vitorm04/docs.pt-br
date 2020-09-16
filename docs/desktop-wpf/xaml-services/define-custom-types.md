---
title: Definir tipos personalizados para uso com os serviços XAML do .NET
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: 2c0578b5397172814c708706173c69ef69f91b2a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551772"
---
# <a name="define-custom-types-for-use-with-net-xaml-services"></a>Definir tipos personalizados para uso com serviços XAML .NET

Quando você define tipos personalizados que são objetos comerciais ou tipos que não têm uma dependência em estruturas específicas, há certas práticas recomendadas para XAML que você pode seguir. Se você seguir essas práticas, os serviços XAML .NET e seus leitores XAML e gravadores XAML poderão descobrir as características XAML do seu tipo e dar a ela a representação apropriada em um fluxo de nó XAML usando o sistema de tipos XAML. Este tópico descreve as práticas recomendadas para definições de tipo, definições de membro e atribuição CLR de tipos ou membros.

## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Padrões de construtor e definições de tipo para XAML

Para ser instanciado como um elemento Object em XAML, uma classe personalizada deve atender aos seguintes requisitos:

- A classe personalizada deve ser pública e deve expor um construtor público sem parâmetros. (Consulte a seção a seguir para ver as observações sobre estruturas.)

- A classe personalizada não deve ser uma classe aninhada. O "ponto" extra no caminho de nome completo torna a divisão de namespace de classe ambígua e interfere com outros recursos XAML, como propriedades anexadas.
Se um objeto puder ser instanciado como um elemento Object, o objeto criado poderá preencher o formulário do elemento Property de todas as propriedades que usam o objeto como seu tipo subjacente.

Você ainda pode fornecer valores de objeto para tipos que não atendem a esses critérios, se você habilitar um conversor de valor. Para obter mais informações, consulte [tipos de conversores e extensões de marcação para XAML](type-converters-and-markup-extensions.md).

### <a name="structures"></a>Estruturas

As estruturas sempre podem ser construídas em XAML, por definição CLR. Isso ocorre porque um compilador CLR cria implicitamente um construtor sem parâmetros para uma estrutura. Esse construtor inicializa todos os valores de propriedade para seus padrões.

Em alguns casos, o comportamento de construção padrão para uma estrutura não é desejável. Isso pode ocorrer porque a estrutura destina-se a preencher valores e funções conceitualmente como uma União. Como uma União, os valores contidos podem ter interpretações mutuamente exclusivas e, portanto, nenhuma de suas propriedades é configurável. Um exemplo de tal estrutura no vocabulário do WPF é <xref:System.Windows.GridLength> . Essas estruturas devem implementar um conversor de tipo para que os valores possam ser expressos na forma de atributo, usando convenções de cadeias de caracteres que criam diferentes interpretações ou modos de valores de estrutura. A estrutura também deve expor comportamento semelhante para a construção de código por meio de um construtor sem parâmetros.

### <a name="interfaces"></a>Interfaces

As interfaces podem ser usadas como tipos subjacentes de membros. O sistema de tipos XAML verifica a lista atribuível e espera que o objeto fornecido como o valor possa ser atribuído à interface. Não há nenhum conceito de como a interface deve ser apresentada como um tipo XAML, desde que um tipo de atribuição relevante dê suporte aos requisitos de construção XAML.

### <a name="factory-methods"></a>Métodos de fábrica

Os métodos de fábrica são um recurso XAML 2009. Eles modificam o princípio do XAML que os objetos devem ter construtores sem parâmetros. Os métodos de fábrica não estão documentados neste artigo. Consulte a [diretiva x:FactoryMethod](xfactorymethod-directive.md).

## <a name="enumerations"></a>Enumerações

Enumerações têm comportamento de conversão de tipo nativo XAML. Nomes de constantes de enumeração especificados em XAML são resolvidos em relação ao tipo de enumeração subjacente e retornam o valor de enumeração para um gravador de objeto XAML.

O XAML dá suporte ao uso em estilo de sinalizadores para enumerações com <xref:System.FlagsAttribute> aplicado. Para obter mais informações, consulte [sintaxe XAML em detalhes](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail). (A[sintaxe XAML em detalhes](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail) é escrita para o público do WPF, mas a maioria das informações nesse tópico é relevante para XAML que não é específico de uma estrutura de implementação específica.)

## <a name="member-definitions"></a>Definições de membro

Os tipos podem definir membros para uso XAML. É possível que os tipos definam Membros que são utilizáveis por XAML mesmo se esse tipo específico não for utilizável por XAML. Isso é possível devido à herança do CLR. Desde que algum tipo que herde o membro dê suporte ao uso de XAML como um tipo, e o membro dê suporte ao uso de XAML para seu tipo subjacente ou tenha uma sintaxe XAML nativa disponível, esse membro será utilizável por XAML.

### <a name="properties"></a>Propriedades

Se você definir propriedades como uma propriedade CLR pública usando os padrões comuns de CLR `get` e `set` acessador e palavras-chave apropriadas à linguagem, o sistema de tipos XAML poderá relatar a propriedade como um membro com as informações apropriadas fornecidas para <xref:System.Xaml.XamlMember> Propriedades, como <xref:System.Xaml.XamlMember.IsReadPublic%2A> e <xref:System.Xaml.XamlMember.IsWritePublic%2A> .

Propriedades específicas podem habilitar uma sintaxe de texto aplicando-se <xref:System.ComponentModel.TypeConverterAttribute> . Para obter mais informações, consulte [tipos de conversores e extensões de marcação para XAML](type-converters-and-markup-extensions.md).

Na ausência de uma sintaxe de texto ou conversão nativa de XAML e na ausência de indireção adicional, como o uso de uma extensão de marcação, o tipo de uma propriedade ( <xref:System.Xaml.XamlMember.TargetType%2A> no sistema de tipos XAML) deve ser capaz de retornar uma instância para um gravador de objeto XAML, tratando o tipo de destino como um tipo CLR.

Se estiver usando XAML 2009, a [extensão de marcação x:Reference](xreference-markup-extension.md) poderá ser usada para fornecer valores se as considerações anteriores não forem atendidas; no entanto, isso é mais de um problema de uso do que um problema de definição de tipo.

### <a name="events"></a>Eventos

Se você definir eventos como um evento CLR público, o sistema de tipos XAML poderá relatar o evento como um membro com <xref:System.Xaml.XamlMember.IsEvent%2A> as `true` . A fiação dos manipuladores de eventos não está dentro do escopo dos recursos dos serviços XAML .NET; a fiação é deixada para estruturas e implementações específicas.

### <a name="methods"></a>Métodos

Código embutido para métodos não é um recurso XAML padrão. Na maioria dos casos, você não referencia diretamente membros de método do XAML, e a função de métodos em XAML é apenas para fornecer suporte a padrões XAML específicos. a [diretiva x:FactoryMethod](xfactorymethod-directive.md) é uma exceção.

### <a name="fields"></a>Campos

As diretrizes de design do CLR desestimulam campos não estáticos. Para campos estáticos, você pode acessar valores de campo estáticos somente por meio da [extensão de marcação x:static](xstatic-markup-extension.md); Nesse caso, você não está fazendo nada de especial na definição de CLR para expor um campo para usos de [x:static](xstatic-markup-extension.md) .

## <a name="attachable-members"></a>Membros anexáveis

Os membros anexáveis são expostos ao XAML por meio de um padrão de método de acessador em um tipo de definição. O tipo de definição em si não precisa ser utilizável por XAML como um objeto. Na verdade, um padrão comum é declarar uma classe de serviço cuja função seja possuir o membro anexável e implementar os comportamentos relacionados, mas não servir nenhuma outra função, como uma representação de interface do usuário. Para as seções a seguir, o espaço reservado *PropertyName* representa o nome do seu membro anexável. Esse nome deve ser válido na [Gramática XamlName](xamlname-grammar.md).

Tenha cuidado com as colisões de nome entre esses padrões e outros métodos de um tipo. Se existir um membro que corresponda a um dos padrões, ele poderá ser interpretado como um caminho de uso de membro anexável por um processador XAML, mesmo que isso não seja sua intenção.

#### <a name="the-getpropertyname-accessor"></a>O acessador GetPropertyName

A assinatura para o `GetPropertyName` acessador deve ser:

`public static object GetPropertyName(object target)`

- O objeto `target` pode ser especificado como um tipo mais específico na sua implementação. Você pode usar isso para fazer o escopo do uso do seu membro anexável; os usos fora do escopo pretendido lançarão exceções de conversão inválidas que, em seguida, são apresentadas por um erro de análise XAML. O nome do parâmetro `target` não é um requisito, mas é nomeado `target` por convenção na maioria das implementações.

- O valor retornado pode ser especificado como um tipo mais específico na sua implementação.

Para dar suporte a uma <xref:System.ComponentModel.TypeConverter> sintaxe de texto habilitada para o uso de atributo do membro anexável, aplique <xref:System.ComponentModel.TypeConverterAttribute> ao `GetPropertyName` acessador. Aplicar ao `get` em vez de `set` pode parecer não intuitivo; no entanto, essa convenção pode dar suporte ao conceito de membros anexáveis somente leitura que são serializáveis, o que é útil em cenários de designer.

#### <a name="the-setpropertyname-accessor"></a>O acessador SetPropertyName

A assinatura para o `SetPropertyName` acessador deve ser:

`public static void SetPropertyName(object target, object value)`

- O `target` objeto pode ser especificado como um tipo mais específico na sua implementação, com a mesma lógica e consequências conforme descrito na seção anterior.

- O objeto `value` pode ser especificado como um tipo mais específico na sua implementação.

Lembre-se de que o valor desse método é a entrada proveniente do uso do XAML, normalmente no formato de atributo. No formato de atributo, deve haver suporte a conversor de valor para uma sintaxe de texto e você atributo no `GetPropertyName` acessador s.

### <a name="attachable-member-stores"></a>Repositórios de membros anexáveis

Os métodos de acessadores normalmente não são suficientes para fornecer um meio de colocar valores de membro anexáveis em um grafo de objeto ou para recuperar valores do grafo de objeto e serializá-los corretamente. Para fornecer essa funcionalidade, os `target` objetos nas assinaturas de acessadores anteriores devem ser capazes de armazenar valores. O mecanismo de armazenamento deve ser consistente com o princípio de membro anexável que o membro é anexável a destinos em que o membro anexável não está na lista de membros. Os serviços XAML .NET fornecem uma técnica de implementação para armazenamentos de membros anexáveis por meio das APIs <xref:System.Xaml.IAttachedPropertyStore> e <xref:System.Xaml.AttachablePropertyServices> . <xref:System.Xaml.IAttachedPropertyStore> é usado pelos gravadores XAML para descobrir a implementação da loja e deve ser implementado no tipo que é o `target` dos acessadores. As APIs estáticas <xref:System.Xaml.AttachablePropertyServices> são usadas dentro do corpo dos acessadores e referem-se ao membro anexável por seu <xref:System.Xaml.AttachableMemberIdentifier> .

## <a name="xaml-related-clr-attributes"></a>Atributos CLR relacionados a XAML

A atribuição correta de seus tipos, membros e assemblies é importante para relatar informações do sistema do tipo XAML aos serviços XAML .NET. O tipo de relatório XAML informações do sistema é relevante se qualquer uma das seguintes situações se aplicar:

- Você pretende que seus tipos sejam usados com sistemas XAML que são diretamente baseados em leitores XAML de serviços XAML .NET e gravadores XAML.
- Você define ou usa uma estrutura de uso de XAML com base nesses leitores XAML e gravadores XAML.

Para obter uma lista de cada atributo relacionado a XAML que é relevante para o suporte a XAML de seus tipos personalizados, consulte [atributos CLR relacionados a XAML para tipos e bibliotecas personalizadas](clr-attributes-with-custom-types-and-libraries.md).

## <a name="usage"></a>Uso

O uso de tipos personalizados requer que o autor da marcação deva mapear um prefixo para o assembly e o namespace CLR que contêm o tipo personalizado. Este procedimento não está documentado neste tópico.

## <a name="access-level"></a>Nível de acesso

O XAML fornece um meio para carregar e criar uma instância de tipos que têm um `internal` nível de acesso. Esse recurso é fornecido para que o código do usuário possa definir seus próprios tipos e, em seguida, instanciar essas classes a partir de marcação que também faz parte do mesmo escopo de código de usuário.

Um exemplo do WPF é sempre que o código do usuário define um <xref:System.Windows.Controls.UserControl> que é projetado como uma maneira de refatorar um comportamento de interface do usuário, mas não como parte de qualquer mecanismo de extensão possível que possa ser implícito, declarando a classe de suporte com o `public` nível de acesso. Tal <xref:System.Windows.Controls.UserControl> pode ser declarada com `internal` acesso se o código de backup for compilado no mesmo assembly do qual é referenciado como um tipo XAML.

Para um aplicativo que carrega XAML sob confiança total e usa <xref:System.Xaml.XamlObjectWriter> , o carregamento de classes com `internal` nível de acesso é sempre habilitado.

Para um aplicativo que carrega XAML sob confiança parcial, você pode controlar as características de nível de acesso usando a <xref:System.Xaml.Permissions.XamlAccessLevel> API. Além disso, os mecanismos de adiamento (como o sistema de modelo do WPF) devem ser capazes de propagar qualquer permissão de nível de acesso e preservá-los para as avaliações de tempo de execução eventual; Isso é manipulado internamente pela transmissão das <xref:System.Xaml.Permissions.XamlAccessLevel> informações.

### <a name="wpf-implementation"></a>Implementação do WPF

O XAML do WPF usa um modelo de acesso de confiança parcial em que, se o BAML for carregado sob confiança parcial, o acesso será restrito ao <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> para o assembly que é a origem de BAML. Para o adiamento, o WPF usa <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> como um mecanismo para passar as informações de nível de acesso.

Na terminologia XAML do WPF, um *tipo interno* é um tipo que é definido pelo mesmo assembly que também inclui o XAML de referência. Esse tipo pode ser mapeado por meio de um namespace XAML que omite deliberadamente o assembly = parte de um mapeamento, por exemplo, `xmlns:local="clr-namespace:WPFApplication1"` . Se BAML referencia um tipo interno e esse tipo tem `internal` nível de acesso, isso gera uma `GeneratedInternalTypeHelper` classe para o assembly. Se você quiser evitar `GeneratedInternalTypeHelper` , deverá usar `public` o nível de acesso ou deve fatorar a classe relevante em um assembly separado e tornar esse assembly dependente.

## <a name="see-also"></a>Confira também

- [Atributos CLR relacionados a XAML para tipos personalizados e bibliotecas](clr-attributes-with-custom-types-and-libraries.md)
- [Serviços XAML](../../../api/index.md)
