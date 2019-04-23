---
title: Definindo tipos personalizados para uso com serviços XAML do .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: be9c0e26574a15279ce89af2c7862abaa8713360
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164431"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>Definindo tipos personalizados para uso com serviços XAML do .NET Framework
Quando você define tipos personalizados que são objetos de negócios ou é tipos que não têm uma dependência em estruturas específicas, há algumas melhores práticas para XAML, você pode seguir. Se você seguir essas práticas, serviços de XAML do .NET Framework e seus leitores XAML e gravadores XAML podem descobrir as características XAML de seu tipo e dê a ele representação apropriada em um fluxo de nó XAML usando o sistema de tipo XAML. Este tópico descreve as práticas recomendadas para definições de tipo, definições de membro e atribuição do CLR de tipos ou membros.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Padrões de construtor e definições de tipo para XAML  
 Para ser instanciado como um elemento de objeto em XAML, uma classe personalizada deve atender aos seguintes requisitos:  
  
-   A classe personalizada deve ser pública e deve expor um construtor de público (sem parâmetros) padrão. (Consulte a seção a seguir para ver as observações sobre estruturas.)  
  
-   A classe personalizada não deve ser uma classe aninhada. O extra "dot" no caminho do nome completo torna a divisão de namespace de classe ambíguo e interfere com outros recursos XAML como propriedades anexadas.  
  
 Se um objeto pode ser instanciado como um elemento de objeto, o objeto criado pode preencher o formulário de elemento de propriedade de todas as propriedades que usam o objeto como seu tipo base.  
  
 Você ainda pode fornecer valores de objeto para tipos que não atendem a esses critérios, se você habilitar um conversor de valor. Para obter mais informações, consulte [conversores de tipo e extensões de marcação para XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Estruturas  
 Estruturas são sempre podem ser construídas em XAML, por definição de CLR. Isso ocorre porque um compilador CLR cria implicitamente um construtor padrão para uma estrutura. Este construtor inicializa todos os valores de propriedade para seus padrões.  
  
 Em alguns casos, o comportamento de construção padrão para uma estrutura não é desejável. Isso pode ocorrer porque a estrutura se destina a preencher valores e a funcionar conceitualmente como uma união. Como uma união, os valores contidos podem ter interpretações mutuamente exclusivas e, portanto, nenhuma de suas propriedades são configuráveis. Um exemplo de uma estrutura como no vocabulário do WPF é <xref:System.Windows.GridLength>. Tais estruturas devem implementar um conversor de tipo para que os valores podem ser expressos na forma de atributo, usando as convenções de cadeia de caracteres que cria a interpretações ou modos diferentes dos valores de estrutura. A estrutura também deve expor um comportamento semelhante para a construção de código por meio de um construtor não padrão.  
  
### <a name="interfaces"></a>Interfaces  
 Interfaces podem ser usadas como tipos subjacentes de membros. O sistema de tipos XAML verifica a lista pode ser atribuída e espera que o objeto que é fornecido como o valor pode ser atribuído à interface. Não há nenhum conceito de como a interface deve ser apresentada como um tipo XAML, desde os requisitos de construção do XAML oferece suporte a um tipo atribuível relevante.  
  
### <a name="factory-methods"></a>Métodos de fábrica  
 Métodos de fábrica são um recurso do XAML 2009. Eles modificam o princípio XAML que objetos devem ter construtores padrão. Métodos de fábrica não são documentados neste tópico. Ver [diretiva X:factorymethod](x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Enumerações  
 Enumerações têm comportamento de conversão de tipo nativo do XAML. Nomes de constantes de enumeração especificados em XAML são resolvidos em relação ao tipo subjacente da enumeração e retornam o valor de enumeração para um gravador de objeto XAML.  
  
 XAML dá suporte ao uso de sinalizadores de estilo para enumerações com <xref:System.FlagsAttribute> aplicado. Para obter mais informações, consulte [sintaxe de XAML em detalhes](../wpf/advanced/xaml-syntax-in-detail.md). ([Sintaxe de XAML em detalhes](../wpf/advanced/xaml-syntax-in-detail.md) é gravada para o público-alvo do WPF, mas a maioria das informações do tópico é relevante para XAML que não é específico para uma determinada estrutura de implementação.)  
  
## <a name="member-definitions"></a>Definições de membro  
 Tipos podem definir membros para o uso do XAML. É possível para os tipos que definem os membros que são utilizáveis de XAML mesmo se esse tipo específico não é utilizável de XAML. Isso é possível devido à herança do CLR. Desde que algum tipo que herda o membro dá suporte ao uso XAML como um tipo e o membro dá suporte ao uso do XAML para seu tipo subjacente ou tem uma sintaxe XAML nativa disponível, esse membro é utilizável de XAML.  
  
### <a name="properties"></a>Propriedades  
 Se você definir propriedades como uma propriedade pública de CLR usando o CLR típico `get` e `set` padrões do acessador e palavras-chave apropriada ao idioma, o sistema de tipos XAML pode relatar a propriedade como um membro com informações apropriadas fornecida para <xref:System.Xaml.XamlMember> propriedades, tais como <xref:System.Xaml.XamlMember.IsReadPublic%2A> e <xref:System.Xaml.XamlMember.IsWritePublic%2A>.  
  
 Propriedades específicas podem habilitar uma sintaxe de texto por meio da aplicação <xref:System.ComponentModel.TypeConverterAttribute>. Para obter mais informações, consulte [conversores de tipo e extensões de marcação para XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
 Na ausência de uma sintaxe de texto ou conversão nativa de XAML e, na ausência de ainda mais indireto, como um uso de extensão de marcação, o tipo de uma propriedade (<xref:System.Xaml.XamlMember.TargetType%2A> no XAML o sistema de tipos) deve ser capaz de retornar uma instância em um gravador de objeto XAML, tratando o t tipo de destino como um tipo CLR.  
  
 Se usar XAML 2009, [extensão de marcação X:Reference](x-reference-markup-extension.md) pode ser usado para fornecer valores se as considerações anteriores não forem atendidas; no entanto, se trata mais de um problema de uso que um problema de definição de tipo.  
  
### <a name="events"></a>Eventos  
 Se você definir eventos como um evento público do CLR, o sistema de tipos XAML pode relatar o evento como um membro com <xref:System.Xaml.XamlMember.IsEvent%2A> como `true`. Conectar os manipuladores de eventos não está dentro do escopo de recursos de serviços de XAML do .NET Framework; Isso é deixado a implementações e estruturas específicas.  
  
### <a name="methods"></a>Métodos  
 O código embutido para métodos não é um recurso XAML padrão. Na maioria dos casos você não faça referência diretamente membros de método de XAML, e a função de métodos em XAML é apenas fornecer suporte para padrões específicos de XAML. [Diretiva X:factorymethod](x-factorymethod-directive.md) é uma exceção.  
  
### <a name="fields"></a>Campos  
 Diretrizes de design do CLR desencorajar os campos não estáticos. Para campos estáticos, você pode acessar valores de campo estático somente por meio [extensão de marcação X:Static](x-static-markup-extension.md); nesse caso, você não fazem nada especial na definição do CLR para expor um campo para [X:Static](x-static-markup-extension.md) usos.  
  
## <a name="attachable-members"></a>Membros anexáveis  
 Os membros anexáveis são expostos ao XAML por meio de um padrão de método do acessador em uma definição de tipo. A definição de tipo em si não precisa ser utilizável de XAML como um objeto. Na verdade, um padrão comum é declarar uma classe de serviço cuja função é possuir o membro anexável e implementar os comportamentos relacionados, mas não servem a nenhuma outra função, como uma representação da interface do usuário. Para as seções a seguir, o espaço reservado *PropertyName* representa o nome de seu membro anexável. Esse nome deve ser válido na [gramática XamlName](xamlname-grammar.md).  
  
 Tenha cuidado de colisões de nome entre esses padrões e outros métodos de um tipo. Se existe um membro que corresponde a um dos padrões, ele pode ser interpretado como um caminho para o membro anexável uso por um processador XAML mesmo se não era sua intenção.  
  
#### <a name="the-getpropertyname-accessor"></a>O acessador GetPropertyName  
 A assinatura para o acessador `Get`*PropertyName* deve ser:  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   O objeto `target` pode ser especificado como um tipo mais específico na sua implementação. Você pode usar isso para definir o escopo o uso de seu membro anexável; usos de fora de seu escopo pretendido gerará exceções de conversão inválida que, em seguida, são apresentadas por um erro de análise XAML. O nome do parâmetro `target` não é um requisito, mas é denominado `target` por convenção, na maioria das implementações.  
  
-   O valor retornado pode ser especificado como um tipo mais específico na sua implementação.  
  
 Para dar suporte a um <xref:System.ComponentModel.TypeConverter> sintaxe de texto habilitada para uso do atributo do membro anexável, aplique <xref:System.ComponentModel.TypeConverterAttribute> para o `Get` *PropertyName* acessador. Aplicação para o `get` em vez do `set` pode parecer (nada óbvio); no entanto, essa convenção pode dar suporte o conceito de somente leitura membros anexáveis que são serializados, que é útil em cenários de designer.  
  
#### <a name="the-setpropertyname-accessor"></a>O acessador SetPropertyName  
 A assinatura para o conjunto*PropertyName* acessador deve ser:  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   O `target` objeto pode ser especificado como um tipo mais específico na sua implementação, com a mesma lógica e consequências, conforme descrito na seção anterior.  
  
-   O objeto `value` pode ser especificado como um tipo mais específico na sua implementação.  
  
 Lembre-se de que o valor para esse método é a entrada proveniente do uso de XAML, normalmente na forma de atributo. No formulário do atributo deve haver suporte de conversor de valor para uma sintaxe de texto e atributo na `Get` *PropertyName* acessador.  
  
### <a name="attachable-member-stores"></a>Repositórios do membro anexável  
 Os métodos acessadores geralmente não são suficientes para fornecer um meio para colocar valores de membro anexável em um gráfico de objeto, ou para recuperar valores fora do grafo de objeto e serializá-los corretamente. Para fornecer essa funcionalidade, o `target` objetos nas assinaturas anteriores acessador devem ser capazes de armazenar valores. O mecanismo de armazenamento deve ser consistente com o princípio de membro anexável que o membro anexável para destinos em que o membro anexável não está na lista de membros. Serviços de XAML do .NET framework fornece uma técnica de implementação para o membro anexável armazena por meio de APIs <xref:System.Xaml.IAttachedPropertyStore> e <xref:System.Xaml.AttachablePropertyServices>. <xref:System.Xaml.IAttachedPropertyStore> é usado pelos gravadores XAML para descobrir a implementação de repositório e deve ser implementado no tipo que é o `target` dos acessadores. Estático <xref:System.Xaml.AttachablePropertyServices> APIs são usadas dentro do corpo dos acessadores e consulte o membro anexável por seu <xref:System.Xaml.AttachableMemberIdentifier>.  
  
## <a name="xaml-related-clr-attributes"></a>Atributos CLR relacionados a XAML  
 Atribuindo corretamente seus tipos, membros e assemblies é importante na ordem para o relatório de informações do sistema de tipo XAML para serviços de XAML do .NET Framework. Isso é relevante se você pretende que seus tipos para uso com sistemas XAML diretamente com base em leitores de XAML de serviços do .NET Framework XAML e gravadores XAML, ou se você definir ou usa uma estrutura utilizando o XAML que se baseia nesses leitores XAML e gravadores XAML.  
  
 Para obter uma lista de cada atributo relacionados a XAML que é relevante para oferecer suporte a XAML seus tipos personalizados, consulte [XAML-Related atributos de CLR para tipos personalizados e bibliotecas](xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Uso  
 Uso de tipos personalizados requer que o autor de marcação deve mapear um prefixo para o assembly e o namespace CLR que contém o tipo personalizado. Esse procedimento não está documentado neste tópico.  
  
## <a name="access-level"></a>Nível de acesso  
 XAML fornece um meio para carregar e criar uma instância de tipos que têm um `internal` nível de acesso. Esse recurso é fornecido para que o código do usuário pode definir seus próprios tipos e, em seguida, crie uma instância dessas classes de marcação que também é parte do mesmo escopo de código do usuário.  
  
 Um exemplo do WPF é sempre que o código de usuário define uma <xref:System.Windows.Controls.UserControl> que destina-se como uma maneira de refatorar um comportamento de interface do usuário, mas não como parte de qualquer mecanismo de extensão possíveis que pode ser implícitas pela declarar a classe de suporte com `public` nível de acesso. Tal uma <xref:System.Windows.Controls.UserControl> pode ser declarado com `internal` acessar se o código é compilado no mesmo assembly do qual ele é referenciado como um tipo XAML.  
  
 Para um aplicativo que carrega XAML em confiança total e usa <xref:System.Xaml.XamlObjectWriter>, carregando classes com `internal` nível de acesso está sempre habilitado.  
  
 Para um aplicativo que carrega a XAML sob confiança parcial, você pode controlar as características de nível de acesso usando o <xref:System.Xaml.Permissions.XamlAccessLevel> API. Além disso, os mecanismos de adiamento (como o sistema de modelo do WPF) devem ser capazes de propagar qualquer permissões de nível de acesso e preservá-las para as avaliações de tempo de execução eventual; Isso é tratado internamente, passando o <xref:System.Xaml.Permissions.XamlAccessLevel> informações.  
  
### <a name="wpf-implementation"></a>Implementação do WPF  
 XAML WPF usa um modelo de acesso de confiança parcial onde se BAML é carregado sob confiança parcial, o acesso é restrito a <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> para o assembly que é a origem BAML. Para o adiamento, o WPF usa <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> como um mecanismo para passar as informações de nível de acesso.  
  
 Na terminologia do WPF XAML, uma *tipo interno* é um tipo definido pelo mesmo assembly que também inclui o XAML de referência. Um tipo pode ser mapeado por meio de um namespace XAML que omite deliberadamente o assembly = parte de um mapeamento, por exemplo, `xmlns:local="clr-namespace:WPFApplication1"`.  Se o BAML faz referência a um tipo interno e que tipo tem `internal` acessar nível, isso gera um `GeneratedInternalTypeHelper` classe para o assembly. Se você quiser evitar `GeneratedInternalTypeHelper`, você deve use `public` nível, de acesso ou deve fatorar a classe relevante em um assembly separado e fazer com que esse assembly dependente.  
  
## <a name="see-also"></a>Consulte também

- [Atributos CLR relacionados a XAML para tipos personalizados e bibliotecas](xaml-related-clr-attributes-for-custom-types-and-libraries.md)
- [Serviços XAML](index.md)
