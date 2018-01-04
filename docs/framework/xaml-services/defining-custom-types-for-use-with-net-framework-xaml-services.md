---
title: "Definindo tipos personalizados para uso com serviços XAML do .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7cce479c7c7a5f6c7112f08f1e15f3bc7e4d366
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>Definindo tipos personalizados para uso com serviços XAML do .NET Framework
Quando você define tipos personalizados que são objetos de negócios ou tipos que não têm uma dependência em estruturas específicas, há algumas melhores práticas para XAML, você pode seguir. Se você seguir essas práticas recomendadas, serviços XAML do .NET Framework e seus leitores XAML e gravadores XAML podem descobrir as características XAML de seu tipo e dê a ele representação apropriada em um fluxo do nó XAML usando o sistema de tipo XAML. Este tópico descreve as práticas recomendadas para definições de tipo, definições de membro e atribuição de CLR de tipos ou membros.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Construtor padrões e definições de tipo para XAML  
 Para ser instanciado como um elemento de objeto em XAML, uma classe personalizada deve atender aos seguintes requisitos:  
  
-   A classe personalizada deve ser pública e deve expor um construtor público (sem parâmetros) do padrão. (Consulte a seção a seguir para ver as observações sobre estruturas.)  
  
-   A classe personalizada não deve ser uma classe aninhada. Adicionais "ponto" no caminho do nome completo torna a divisão do namespace da classe ambígua e interferem com outros recursos XAML, como propriedades anexadas.  
  
 Se um objeto pode ser instanciado como um elemento de objeto, o objeto criado pode preencher o formulário de elemento de propriedade de todas as propriedades que usam o objeto como seu tipo base.  
  
 Você ainda pode fornecer valores de objeto para tipos que não atendem a esses critérios, se você habilitar um conversor de valor. Para obter mais informações, consulte [conversores de tipo e extensões de marcação para XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Estruturas  
 Estruturas sempre são capazes de ser construído em XAML, por definição de CLR. Isso ocorre porque um compilador CLR cria implicitamente um construtor padrão para uma estrutura. Este construtor inicializa todos os valores de propriedade para seus padrões.  
  
 Em alguns casos, o comportamento de construção padrão para uma estrutura não é desejável. Isso pode ser porque a estrutura é destinada para preencher valores e função conceitualmente como uma união. Como uma união, os valores contidos podem ter interpretações mutuamente exclusivas e, portanto, nenhuma de suas propriedades são configuráveis. Um exemplo de tal uma estrutura de vocabulário do WPF é <xref:System.Windows.GridLength>. Essas estruturas devem implementar um conversor de tipo para que os valores podem ser expressos na forma de atributo usando convenções de cadeia de caracteres que cria a interpretações diferentes ou modos dos valores de estrutura. A estrutura também deve expor um comportamento semelhante para a construção de código por meio de um construtor não padrão.  
  
### <a name="interfaces"></a>Interfaces  
 Interfaces podem ser usadas como tipos base de membros. O sistema de tipo XAML verifica a lista pode ser atribuída e espera que o objeto que é fornecido como o valor pode ser atribuído à interface. Não há nenhum conceito de como a interface deve ser apresentada como um tipo XAML, como um tipo atribuível relevante suporte os requisitos de construção de XAML.  
  
### <a name="factory-methods"></a>Métodos de fábrica  
 Métodos de fábrica são um recurso de XAML 2009. Eles modificar o princípio XAML que objetos devem ter construtores padrão. Métodos de fábrica não são documentados neste tópico. Consulte [diretiva X:factorymethod](../../../docs/framework/xaml-services/x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Enumerações  
 Enumerações tem comportamento de conversão de tipo nativo do XAML. Nomes de constantes de enumeração especificados em XAML são resolvidos em relação ao tipo de enumeração subjacente e retornam o valor de enumeração para o gravador de objeto XAML.  
  
 XAML dá suporte ao uso de um estilo de sinalizadores para enumerações com <xref:System.FlagsAttribute> aplicado. Para obter mais informações, consulte [XAML sintaxe em detalhes](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md). ([XAML sintaxe em detalhes](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md) é gravado para o público do WPF, mas a maioria das informações do tópico é relevante para XAML que não é específico para uma estrutura específica de implementação.)  
  
## <a name="member-definitions"></a>Definições de membro  
 Tipos podem definir membros para uso em XAML. É possível para os tipos que definem os membros que são utilizáveis de XAML, mesmo se esse tipo específico não é utilizável de XAML. Isso é possível devido a herança de CLR. Desde que algum tipo que herda o membro oferece suporte ao uso XAML, como um tipo e o membro oferece suporte ao uso do XAML para seu tipo subjacente ou possui uma sintaxe XAML nativo disponível, esse membro é XAML utilizável.  
  
### <a name="properties"></a>Propriedades  
 Se você definir propriedades como uma propriedade pública de CLR usando o CLR típico `get` e `set` padrões de acessador e palavras-chave apropriada ao idioma, o sistema de tipo XAML pode relatar a propriedade como um membro com informações apropriadas fornecida para <xref:System.Xaml.XamlMember> propriedades, como <xref:System.Xaml.XamlMember.IsReadPublic%2A> e <xref:System.Xaml.XamlMember.IsWritePublic%2A>.  
  
 Propriedades específicas podem habilitar uma sintaxe de texto aplicando <xref:System.ComponentModel.TypeConverterAttribute>. Para obter mais informações, consulte [conversores de tipo e extensões de marcação para XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 Na ausência de uma sintaxe de texto ou de conversão de XAML nativo e na ausência de indireção adicional, como um uso de extensão de marcação, o tipo de uma propriedade (<xref:System.Xaml.XamlMember.TargetType%2A> no XAML sistema de tipos) deve ser capaz de retornar uma instância de um gravador de objeto XAML tratando o t tipo de destino como um tipo CLR.  
  
 Se usando XAML 2009, [extensão de marcação X:Reference](../../../docs/framework/xaml-services/x-reference-markup-extension.md) pode ser usado para fornecer valores se as considerações anteriores não forem atendidas; no entanto, que é mais um problema de uso de um problema de definição de tipo.  
  
### <a name="events"></a>Eventos  
 Se você definir eventos como um evento público do CLR, o sistema de tipo XAML pode relatar o evento como um membro com <xref:System.Xaml.XamlMember.IsEvent%2A> como `true`. Os manipuladores de eventos de circuito não está dentro do escopo de recursos de serviços XAML do .NET Framework; Isso é da esquerda para implementações e estruturas específicas.  
  
### <a name="methods"></a>Métodos  
 O código embutido para métodos não é um recurso XAML padrão. Na maioria dos casos você não faça referência diretamente membros de método do XAML, e a função dos métodos em XAML é apenas fornecer suporte para padrões específicos de XAML. [Diretiva X:factorymethod](../../../docs/framework/xaml-services/x-factorymethod-directive.md) é uma exceção.  
  
### <a name="fields"></a>Campos  
 Diretrizes de design do CLR evitar campos não estáticos. Para campos estáticos, você pode acessar os valores de campo estático somente com [extensão de marcação X:Static](../../../docs/framework/xaml-services/x-static-markup-extension.md); nesse caso você não fazem nada especial na definição do CLR para expor um campo para [X:Static](../../../docs/framework/xaml-services/x-static-markup-extension.md) usos.  
  
## <a name="attachable-members"></a>Membros anexáveis  
 Membros anexáveis são expostos para XAML por meio de um padrão de método de acessador em uma definição de tipo. A definição de tipo em si não precisa ser XAML usado como um objeto. Na verdade, um padrão comum é declarar uma classe de serviço cuja função é possuir o membro anexável e implementar os comportamentos relacionados, mas não servem nenhuma outra função, como uma representação da interface do usuário. Para as seções a seguir, o espaço reservado *PropertyName* representa o nome de seu membro anexável. Esse nome deve ser válido no [gramática XamlName](../../../docs/framework/xaml-services/xamlname-grammar.md).  
  
 Tenha cuidado de conflitos de nome entre esses padrões e outros métodos de um tipo. Se existe um membro que corresponda a um dos padrões, ele pode ser interpretado como um caminho de uso anexável por um processador XAML mesmo que não era a intenção.  
  
#### <a name="the-getpropertyname-accessor"></a>O acessador de GetPropertyName  
 A assinatura para o acessador `Get`*PropertyName* deve ser:  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   O objeto `target` pode ser especificado como um tipo mais específico na sua implementação. Você pode usar isso para definir o escopo de uso de anexável; usos de fora de seu escopo pretendido lançarão exceções de conversão inválida que, em seguida, são apresentadas por um erro de análise XAML. O nome do parâmetro `target` não é um requisito, mas é denominado `target` por convenção, na maioria das implementações.  
  
-   O valor retornado pode ser especificado como um tipo mais específico na sua implementação.  
  
 Para dar suporte a um <xref:System.ComponentModel.TypeConverter> sintaxe de texto habilitado para uso do atributo do membro anexável, aplicar <xref:System.ComponentModel.TypeConverterAttribute> para o `Get` *PropertyName* acessador. Aplicação para o `get` em vez do `set` pode parecer (nada óbvio); no entanto, essa convenção pode dar suporte o conceito de somente leitura anexáveis membros serializáveis, que é útil em cenários de designer.  
  
#### <a name="the-setpropertyname-accessor"></a>O acessador de SetPropertyName  
 A assinatura para o conjunto de*PropertyName* acessador deve ser:  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   O `target` objeto pode ser especificado como um tipo mais específico na sua implementação, com a mesma lógica e consequências, conforme descrito na seção anterior.  
  
-   O objeto `value` pode ser especificado como um tipo mais específico na sua implementação.  
  
 Lembre-se de que o valor para este método é a entrada proveniente do uso de XAML, normalmente na forma de atributo. De forma de atributo deve haver suporte de conversor de valor para uma sintaxe de texto e atributo no `Get` *PropertyName* acessador.  
  
### <a name="attachable-member-stores"></a>Repositórios de membro anexável  
 Os métodos acessadores normalmente não são suficientes para fornecer um meio para inserir os valores de membro anexável em um gráfico de objeto, ou para recuperar valores fora do gráfico do objeto e serializá-los corretamente. Para fornecer essa funcionalidade, o `target` objetos nas assinaturas acessador anterior devem ser capazes de armazenar valores. O mecanismo de armazenamento deve ser consistente com o princípio de anexável que o membro anexável para destinos de onde o membro anexável não está na lista de membros. Serviços XAML do .NET framework fornece uma técnica de implementação para o membro anexável armazena através das APIs <xref:System.Xaml.IAttachedPropertyStore> e <xref:System.Xaml.AttachablePropertyServices>. <xref:System.Xaml.IAttachedPropertyStore>é usado pelos autores XAML para descobrir a implementação de armazenamento e deve ser implementado no tipo que é o `target` de acessadores. Estático <xref:System.Xaml.AttachablePropertyServices> APIs são usados dentro do corpo de acessadores e consulte o membro anexável por seu <xref:System.Xaml.AttachableMemberIdentifier>.  
  
## <a name="xaml-related-clr-attributes"></a>Atributos CLR relacionados a XAML  
 Atribuição corretamente os tipos, membros e assemblies é importante na ordem para o relatório de informações do sistema de tipo XAML para serviços XAML do .NET Framework. Isso é relevante se você pretende seus tipos para uso com os sistemas XAML diretamente com base em leitores de XAML de serviços XAML do .NET Framework e gravadores XAML, ou se você define ou usa uma estrutura utilizando XAML com base nesses leitores XAML e gravadores XAML.  
  
 Para obter uma lista de cada atributo relacionados a XAML que é relevante para suporte XAML de seus tipos personalizados, consulte [XAML-Related CLR atributos para tipos personalizados e bibliotecas](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Uso  
 Uso de tipos personalizados requer que o autor de marcação deve mapear um prefixo para o assembly e o namespace CLR que contém o tipo personalizado. Esse procedimento não está documentado neste tópico.  
  
## <a name="access-level"></a>Nível de acesso  
 XAML fornece um meio para carregar e instanciar tipos que têm um `internal` nível de acesso. Essa funcionalidade é fornecida para que o código do usuário pode definir seus próprios tipos e, em seguida, criar uma instância dessas classes de marcação que também faz parte do mesmo escopo de código do usuário.  
  
 Um exemplo do WPF é sempre que o código de usuário define uma <xref:System.Windows.Controls.UserControl> que destina-se como uma maneira para refatorar um comportamento de interface do usuário, mas não como parte de qualquer mecanismo de extensão possíveis que pode ser implícitas declarando a classe de suporte com `public` nível de acesso. Tal uma <xref:System.Windows.Controls.UserControl> pode ser declarado com `internal` acesso se o código é compilado para o mesmo assembly do qual ele é referenciado como um tipo XAML.  
  
 Para um aplicativo que carrega o XAML em confiança total e usa <xref:System.Xaml.XamlObjectWriter>, carregando classes com `internal` nível de acesso está sempre habilitado.  
  
 Para um aplicativo que carrega o XAML em confiança parcial, você pode controlar as características de nível de acesso usando o <xref:System.Xaml.Permissions.XamlAccessLevel> API. Além disso, mecanismos de adiamento (como o sistema de modelo do WPF) devem ser capazes de propagar quaisquer permissões de nível de acesso e preservá-los para as avaliações de tempo de execução eventual; Isso é manipulado internamente, passando o <xref:System.Xaml.Permissions.XamlAccessLevel> informações.  
  
### <a name="wpf-implementation"></a>Implementação do WPF  
 WPF XAML usa um modelo de acesso de confiança parcial onde se BAML é carregado sob confiança parcial, o acesso é restrito a <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> para o assembly que é a origem BAML. Para o adiamento, WPF usa <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> como um mecanismo para passar as informações de nível de acesso.  
  
 Na terminologia do WPF XAML, uma *tipo interno* é um tipo definido pelo mesmo assembly que também inclui o XAML de referência. Desse tipo pode ser mapeado por meio de um namespace XAML que deliberadamente omite o assembly = parte de um mapeamento, por exemplo, `xmlns:local="clr-namespace:WPFApplication1"`.  Se BAML faz referência a um tipo interno e que tenha tipo `internal` acessar nível, isso gera um `GeneratedInternalTypeHelper` classe para o assembly. Se você quiser evitar `GeneratedInternalTypeHelper`, você deve use `public` nível, de acesso ou deve influenciar a classe relevante um assembly separado e tornar esse assembly dependente.  
  
## <a name="see-also"></a>Consulte também  
 [Atributos CLR relacionados a XAML para tipos personalizados e bibliotecas](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)  
 [Serviços XAML](../../../docs/framework/xaml-services/index.md)
