---
title: Escrevendo atributos personalizados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET Framework], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0205edba221b833625becbe6a1f2fdda2f9409a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="writing-custom-attributes"></a>Escrevendo atributos personalizados
Para criar seus próprios atributos personalizados, você não precisa dominar muitos novos conceitos. Se você estiver familiarizado com programação orientada a objeto e sabe como criar classes, você já tem a maioria do conhecimento necessário. Atributos personalizados são classes essencialmente tradicionais que derivam direta ou indiretamente <xref:System.Attribute?displayProperty=nameWithType>. Exatamente como classes tradicionais, os atributos personalizados contêm métodos que armazenam e recuperam dados.  
  
 As etapas principais para criar corretamente classes de atributos personalizados são os seguintes:  
  
-   [Aplicando o AttributeUsageAttribute](#cpconapplyingattributeusageattribute)  
  
-   [Declarando a classe de atributo](#cpcondeclaringattributeclass)  
  
-   [Declarando construtores](#cpcondeclaringconstructors)  
  
-   [Declarando propriedades](#cpcondeclaringproperties)  
  
 Esta seção descreve cada uma dessas etapas e termina com um [exemplo de atributo personalizado](#cpconcustomattributeexample).  
  
<a name="cpconapplyingattributeusageattribute"></a>   
## <a name="applying-the-attributeusageattribute"></a>Aplicando o AttributeUsageAttribute  
 Uma declaração de atributo personalizado começa com o **AttributeUsageAttribute**, que define algumas das principais características da sua classe de atributo. Por exemplo, você pode especificar se o atributo pode ser herdada por outras classes ou especificar a quais elementos o atributo pode ser aplicado a. O fragmento de código a seguir demonstra como usar o **AttributeUsageAttribute**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 O <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> tem três membros que são importantes para a criação de atributos personalizados: [AttributeTargets](#cpconwritingcustomattributesanchor1), [herdadas](#cpconwritingcustomattributesanchor2), e [AllowMultiple](#cpconwritingcustomattributesanchor3).  
  
<a name="cpconwritingcustomattributesanchor1"></a>   
### <a name="attributetargets-member"></a>Membro da AttributeTargets  
 No exemplo anterior, **AttributeTargets. All** é especificada, indicando que esse atributo pode ser aplicado a todos os elementos do programa. Como alternativa, você pode especificar **AttributeTargets**, indicando que o atributo pode ser aplicado somente a uma classe, ou **AttributeTargets**, indicando que o atributo pode ser aplicado somente a um método. Todos os elementos do programa podem ser marcados para descrição por um atributo personalizado dessa maneira.  
  
 Você também pode passar várias instâncias do <xref:System.AttributeTargets>. O fragmento de código a seguir especifica que um atributo personalizado pode ser aplicado a qualquer classe ou método.  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
<a name="cpconwritingcustomattributesanchor2"></a>   
### <a name="inherited-property"></a>Propriedade herdada  
 O <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> propriedade indica se o atributo pode ser herdado por classes derivadas de classes para o qual o atributo é aplicado. Essa propriedade aceita um **true** (o padrão) ou **false** sinalizador. Por exemplo, no exemplo a seguir, `MyAttribute` tem um padrão <xref:System.AttributeUsageAttribute.Inherited%2A> valor **true**, enquanto `YourAttribute` tem um <xref:System.AttributeUsageAttribute.Inherited%2A> valor **false**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 Os dois atributos são aplicados a um método na classe base `MyClass`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 Por fim, a classe `YourClass` é herdada da classe base `MyClass`. O método `MyMethod` mostra `MyAttribute`, mas não `YourAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
<a name="cpconwritingcustomattributesanchor3"></a>   
### <a name="allowmultiple-property"></a>Propriedade AllowMultiple  
 O <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> propriedade indica se várias instâncias do seu atributo podem existir em um elemento. Se definido como **true**, são permitidas várias instâncias; se definido como **false** (o padrão), somente uma instância é permitida.  
  
 No exemplo a seguir, `MyAttribute` tem um padrão <xref:System.AttributeUsageAttribute.AllowMultiple%2A> valor **false**, enquanto `YourAttribute` tem um valor de **true**.  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 Quando várias instâncias desses atributos são aplicadas, `MyAttribute` produz um erro do compilador. O exemplo de código a seguir mostra o uso válido de `YourAttribute` e o uso inválido de `MyAttribute`.  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 Se o <xref:System.AttributeUsageAttribute.AllowMultiple%2A> propriedade e o <xref:System.AttributeUsageAttribute.Inherited%2A> propriedade são definidos como **true**, uma classe herdada de outra classe pode herdar de um atributo e ter outra instância do mesmo atributo aplicado na mesma classe filho. Se <xref:System.AttributeUsageAttribute.AllowMultiple%2A> é definido como **false**, os valores de quaisquer atributos na classe pai serão substituídos pelas novas instâncias do mesmo atributo na classe filha.  
  
<a name="cpcondeclaringattributeclass"></a>   
## <a name="declaring-the-attribute-class"></a>Declarando a classe de atributo  
 Depois de aplicar o <xref:System.AttributeUsageAttribute>, você pode começar a definir as especificidades do seu atributo. A declaração de uma classe de atributo é semelhante à declaração de uma classe tradicional, como demonstrado pelo código a seguir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 Esta definição de atributo demonstra os seguintes pontos:  
  
-   Classes de atributo devem ser declarados como classes públicas.  
  
-   Por convenção, o nome da classe de atributo termina com a palavra **atributo**. Embora não seja necessário, esta convenção é recomendada para facilitar a leitura. Quando o atributo é aplicado, a inclusão da palavra atributo é opcional.  
  
-   Todas as classes de atributo devem herdar direta ou indiretamente de **Attribute**.  
  
-   No Microsoft Visual Basic, todas as classes de atributo personalizado devem ter o **AttributeUsageAttribute** atributo.  
  
<a name="cpcondeclaringconstructors"></a>   
## <a name="declaring-constructors"></a>Declarando construtores  
 Atributos são inicializados com construtores da mesma forma como as classes tradicionais. O fragmento de código a seguir ilustra um típico construtor de atributos. Esse construtor público aceita um parâmetro e define seu valor igual a uma variável de membro.  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 Você pode sobrecarregar o construtor para acomodar diferentes combinações de valores. Se você também definir um [propriedade](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) para sua classe de atributo personalizado, você pode usar uma combinação de parâmetros nomeados e posicionais ao inicializar o atributo. Normalmente, você define todos os parâmetros necessários como parâmetros posicionais e todos opcionais, como chamado. Nesse caso, o atributo não pode ser inicializado sem o parâmetro necessário. Todos os outros parâmetros são opcionais. Observe que no Visual Basic, construtores para uma classe de atributo não devem usar um argumento ParamArray.  
  
 O exemplo de código a seguir mostra como um atributo que usa o construtor anterior pode ser aplicado usando parâmetros necessários e opcionais. Ele pressupõe que o atributo tem um valor booleano necessário e uma cadeia de caracteres opcional.  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
<a name="cpcondeclaringproperties"></a>   
## <a name="declaring-properties"></a>Declarando propriedades  
 Se você quiser definir um parâmetro nomeado ou fornecer uma maneira fácil para retornar os valores armazenados pelo seu atributo, declare um [propriedade](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52). Propriedades de atributo devem ser declaradas como entidades públicas com uma descrição do tipo de dados que será retornado. Definir a variável que irá conter o valor de sua propriedade e associá-lo com o **obter** e **definir** métodos. O exemplo de código a seguir demonstra como implementar uma propriedade simples em seu atributo.  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
<a name="cpconcustomattributeexample"></a>   
## <a name="custom-attribute-example"></a>Exemplo de atributo personalizado  
 Esta seção incorpora as informações anteriores e mostra como criar um atributo simples que documenta informações sobre o autor de uma seção de código. O atributo neste exemplo armazena o nome e o nível do programador, e se o código foi revisado. Ele usa três variáveis privadas para armazenar os valores reais para salvar. Cada variável é representado por uma propriedade pública que obtém e define os valores. Finalmente, o construtor é definido com dois parâmetros necessários.  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 Você pode aplicar esse atributo usando o nome completo, `DeveloperAttribute`, ou usando o nome abreviado, `Developer`, em uma das seguintes maneiras.  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 O primeiro exemplo mostra o atributo aplicado com apenas o necessário a parâmetros nomeados, enquanto o segundo exemplo mostra o atributo aplicado com os parâmetros necessários e opcionais.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Attribute?displayProperty=nameWithType>  
 <xref:System.AttributeUsageAttribute>  
 [Atributos](../../../docs/standard/attributes/index.md)
