---
title: "Covariância e contravariância em genéricos"
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
helpviewer_keywords:
- generics, covariance and contravariance
- generics, variance
- covariance and contravariance in generics
- generic type parameters
ms.assetid: 2678dc63-c7f9-4590-9ddc-0a4df684d42e
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1ae8b6da5917950664e1ab780b8db76cb6500e70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="covariance-and-contravariance-in-generics"></a>Covariância e contravariância em genéricos
<a name="top"></a>Covariância e contravariância são derivados de termos que se referem a possibilidade de usar um valor menor (menos específico) ou tipo (mais específico) mais derivado do originalmente especificado. Os parâmetros de tipo genéricos oferecem suporte a covariância e contravariância para fornecer maior flexibilidade na atribuição e no uso de tipos genéricos. Quando você se refere a um sistema de tipos, a covariância, contravariância e invariância possuem as definições a seguir. Os exemplos assumem uma classe base chamada `Base` e uma classe derivada chamada `Derived`.  
  
-   `Covariance`  
  
     Permite usar um tipo mais derivado que o especificado originalmente.  
  
     Você pode atribuir uma instância de `IEnumerable<Derived>` (`IEnumerable(Of Derived)` no Visual Basic) a uma variável do tipo `IEnumerable<Base>`.  
  
-   `Contravariance`  
  
     Permite a você usar um tipo mais genérico (menos derivado) do que aquele especificado originalmente.  
  
     Você pode atribuir uma instância de `IEnumerable<Base>` (`IEnumerable(Of Base)` no Visual Basic) a uma variável do tipo `IEnumerable<Derived>`.  
  
-   `Invariance`  
  
     Significa que você pode usar apenas o tipo especificado originalmente; assim, um parâmetro de tipo genérico invariante não é covariante nem contravariante.  
  
     Você não pode atribuir uma instância de `IEnumerable<Base>` (`IEnumerable(Of Base)` no Visual Basic) a uma variável do tipo `IEnumerable<Derived>` ou vice-versa.  
  
 Parâmetros de tipo covariant lhe permitem fazer atribuições que se parecem muito parecido com comum [polimorfismo](~/docs/csharp/programming-guide/classes-and-structs/polymorphism.md), conforme mostrado no código a seguir.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 A classe <xref:System.Collections.Generic.List%601> implementa a interface <xref:System.Collections.Generic.IEnumerable%601>. Assim, `List<Derived>` (`List(Of Derived)` no Visual Basic) implementa `IEnumerable<Derived>`. O parâmetro de tipo covariante faz o resto.  
  
 A contravariância, por outro lado, parece não ser intuitiva. O exemplo a seguir cria um delegado do tipo `Action<Base>` (`Action(Of Base)` no Visual Basic) e, em seguida, atribuir o delegado a uma variável do tipo `Action<Derived>`.  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Isso parece ser um retrocesso, mas é esse código de tipo seguro que compila e executa. A expressão lambda corresponde ao delegado ao qual ela é atribuída. Assim, ela define um método que recebe um parâmetro do tipo `Base` e não tem nenhum valor de retorno. O delegado resultante pode ser atribuído a uma variável do tipo `Action<Derived>` porque o parâmetro de tipo `T` do delegado <xref:System.Action%601> é contravariante. O código é de tipo seguro porque `T` especifica um tipo de parâmetro. Quando o delegado do tipo `Action<Base>` é invocado como se fosse um delegado do tipo `Action<Derived>`, seu argumento deve ser do tipo `Derived`. Este argumento sempre pode ser passado ao método subjacente com segurança porque o parâmetro do método é do tipo `Base`.  
  
 Geralmente, um parâmetro de tipo de covariante pode ser usado como o tipo de retorno de um delegado, e os parâmetros de tipo contravariant podem ser usados como tipos de parâmetro. Para uma interface, os parâmetros de tipo covariantes podem ser usados como os tipos de retorno dos métodos da interface, e os parâmetros de tipo contravariantes podem ser usados como os tipos de parâmetro dos métodos da interface.  
  
 A covariância e a contravariância são referidas coletivamente como *variância*. Um parâmetro de tipo genérico que não está marcado como covariant ou contravariant é conhecido como *invariável*. Um breve resumo de fatos sobre variância em Common Language Runtime:  
  
-   No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], os parâmetros de tipo variantes são restringidos à interface genérica e tipos de delegados genéricos.  
  
-   Uma interface genérica ou um tipo delegado genérico podem ter parâmetros de tipo covariantes e contravariantes.  
  
-   A variância aplica-se apenas para referenciar tipos; se você especificar um tipo de valor para um parâmetro de tipo variante, esse parâmetro de tipo será invariante para o tipo construído resultante.  
  
-   A variância não se aplica à combinação de delegado. Ou seja, considerando dois delegados de tipos `Action<Derived>` e `Action<Base>` (`Action(Of Derived)` e `Action(Of Base)` no Visual Basic), você não pode combinar o segundo delegado com o primeiro, ainda que o resultado seja de tipo seguro. A variância permite que o segundo delegado seja atribuído a uma variável do tipo `Action<Derived>`, mas os delegados podem ser combinados somente quando seus tipos são exatamente iguais.  
  
 As subseções a seguir descrevem parâmetros de tipo covariantes e contravariantes em detalhes:  
  
-   [Interfaces genéricas com parâmetros de tipo Covariant](#InterfaceCovariantTypeParameters)  
  
-   [Interfaces genéricas com parâmetros de tipo genérico Contravariant](#InterfaceCovariantTypeParameters)  
  
-   [Delegados genéricos com variante parâmetros de tipo](#DelegateVariantTypeParameters)  
  
-   [Definição de Interfaces genéricas variáveis e delegados](#DefiningVariantTypeParameters)  
  
-   [Lista de variante Interface genérica e tipos delegados](#VariantList)  
  
<a name="InterfaceCovariantTypeParameters"></a>   
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Interfaces genéricas com parâmetros de tipo covariantes  
 Começando com o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], várias interfaces genéricas tem parâmetros de tipo covariant; por exemplo: <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Linq.IQueryable%601>, e <xref:System.Linq.IGrouping%602>. Todos os parâmetros de tipo dessas interfaces são covariantes, de forma que os parâmetros de tipo são usados apenas para os tipos de retorno dos membros.  
  
 O exemplo a seguir ilustra parâmetros de tipo covariantes. O exemplo define dois tipos: `Base` tem um método estático chamado `PrintBases` que usa um `IEnumerable<Base>` (`IEnumerable(Of Base)` no Visual Basic) e imprime os elementos. `Derived` herda de `Base`. O exemplo cria um `List<Derived>` vazio (`List(Of Derived)` no Visual Basic) e demonstra que esse tipo pode ser passado a `PrintBases` e atribuído a uma variável do tipo `IEnumerable<Base>` sem converter. <xref:System.Collections.Generic.List%601> implementa <xref:System.Collections.Generic.IEnumerable%601>, o qual tem um único parâmetro de tipo covariante. O parâmetro de tipo covariante é a razão pela qual uma instância de `IEnumerable<Derived>` pode ser usada em vez de `IEnumerable<Base>`.  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
 [Voltar ao início](#top)  
  
<a name="InterfaceContravariantTypeParameters"></a>   
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Interfaces genéricas com parâmetros de tipo genéricos contravariantes  
 Começando com o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], várias interfaces genéricas tem parâmetros de tipo contravariant; por exemplo: <xref:System.Collections.Generic.IComparer%601>, <xref:System.IComparable%601>, e <xref:System.Collections.Generic.IEqualityComparer%601>. Essas interfaces possuem apenas parâmetros de tipo contravariantes. Assim, os parâmetros de tipo são usados apenas como parâmetros de tipo nos membros das interfaces.  
  
 O exemplo a seguir ilustra parâmetros de tipo contravariantes. O exemplo define uma classe abstrata (`MustInherit` no Visual Basic) `Shape` com uma propriedade `Area`. O exemplo também define uma classe `ShapeAreaComparer` que implementa `IComparer<Shape>` (`IComparer(Of Shape)` no Visual Basic). A implementação do método <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> baseia-se no valor da propriedade `Area`, portanto `ShapeAreaComparer` pode ser usado para classificar objetos `Shape` por área.  
  
 A classe `Circle` herda `Shape` e substitui `Area`. O exemplo cria um <xref:System.Collections.Generic.SortedSet%601> de objetos `Circle` usando um construtor que usa `IComparer<Circle>` (`IComparer(Of Circle)` no Visual Basic). Porém, em vez de passar um `IComparer<Circle>`, o exemplo passa um objeto `ShapeAreaComparer` que implementa `IComparer<Shape>`. O exemplo pode passar um comparador de um tipo derivado (`Shape`) quando um código chama um comparador de um tipo mais derivado (`Circle`) porque o parâmetro de tipo da interface genérica <xref:System.Collections.Generic.IComparer%601> é contravariante.  
  
 Quando um novo objeto `Circle` é adicionado a `SortedSet<Circle>`, o método `IComparer<Shape>.Compare` (método `IComparer(Of Shape).Compare` no Visual Basic) do objeto `ShapeAreaComparer` é chamado sempre que um novo elemento é comparado a um elemento existente. O tipo de parâmetro do método (`Shape`) é menos derivado que o tipo que está sendo passado (`Circle`). Assim, a chamada é de tipo seguro. A contravariância permite que `ShapeAreaComparer` classifique uma coleção de um único tipo, bem como uma coleção mista de tipos, que deriva de `Shape`.  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  
  
 [Voltar ao início](#top)  
  
<a name="DelegateVariantTypeParameters"></a>   
## <a name="generic-delegates-with-variant-type-parameters"></a>Delegados genéricos com parâmetros de tipo variantes  
 No [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], o `Func` delega genérico, como <xref:System.Func%602>, têm tipos de retorno covariante e tipos de parâmetro contravariant. Os delegados genéricos `Action`, como <xref:System.Action%602>, possuem tipos de parâmetros contravariantes. Isso significa que os delegados podem ser atribuídos a variáveis que possuem tipos de parâmetro mais derivados e (no caso dos delegados genéricos `Func`) menos tipos de retorno derivados.  
  
> [!NOTE]
>  O último parâmetro de tipo genérico dos delegados genéricos `Func` especifica o tipo do valor de retorno na assinatura do delegado. É covariante (palavra-chave `out`), enquanto os outros parâmetros de tipo genéricos são contravariantes (palavra-chave `in`).  
  
 O código a seguir ilustra isso. O primeiro trecho de código define uma classe chamada `Base`, uma classe chamada `Derived` que herda `Base` e outra classe com um método `static` (`Shared` no Visual Basic) chamado `MyMethod`. O método usa uma instância de `Base` e retorna uma instância de `Derived`. (Se o argumento é uma instância de `Derived`, `MyMethod` o retorna; se o argumento é uma instância de `Base`, `MyMethod` retorna uma nova instância de `Derived`.) Em `Main()`, o exemplo cria uma instância de `Func<Base, Derived>` (`Func(Of Base, Derived)` no Visual Basic) que representa `MyMethod` e a armazena na variável `f1`.  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 O segundo trecho de código a seguir mostra que o delegado pode ser atribuído a uma variável do tipo `Func<Base, Base>` (`Func(Of Base, Base)` no Visual Basic) porque o tipo de retorno é covariante.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 O terceiro trecho de código a seguir mostra que o delegado pode ser atribuído a uma variável do tipo `Func<Derived, Derived>` (`Func(Of Derived, Derived)` no Visual Basic) porque o tipo de parâmetro é contravariante.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 O trecho final de código mostra que o delegado pode ser atribuído a uma variável de tipo `Func<Derived, Base>` (`Func(Of Derived, Base)` no Visual Basic), combinando os efeitos do tipo de parâmetro contravariante e do tipo de retorno covariante.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Variação em delegados genéricos e não genéricos  
 No código anterior, a assinatura de `MyMethod` corresponde exatamente à assinatura do delegado genérico construído: `Func<Base, Derived>` (`Func(Of Base, Derived)` no Visual Basic). O exemplo mostra que esse delegado genérico pode ser armazenado em variáveis ou parâmetros do método que têm tipos de parâmetro mais derivados e tipos de retorno menos derivados, desde que todos os tipos de delegados sejam construídos do tipo de delegado genérico <xref:System.Func%602>.  
  
 Este é um aspecto importante. Os efeitos de covariância e contravariância em parâmetros de tipo de delegados genéricos são semelhantes aos efeitos de covariância e contravariância delegado comum de associação (consulte [variação em delegações](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)). No entanto, a variância na associação de delegados funciona com todos os tipos de delegados, e não apenas com tipos de delegados genéricos com parâmetros de tipo variantes. Além disso, a variância na associação de delegados possibilita a um método a ser associado a qualquer delegado que tenha os tipos de parâmetro mais restritivos e um tipo de retorno menos restritivo, enquanto que a atribuição de delegados genéricos só funciona quando ambos os tipos de delegados são construídos da mesma definição de tipo genérico.  
  
 O exemplo a seguir mostra os efeitos combinados da variância na associação de delegados e a variância em parâmetros de tipo genéricos. O exemplo define uma hierarquia de tipo que inclui três tipos, do menos derivado (`Type1`) para o mais derivado (`Type3`). A variância na associação comum de delegados é usada para associar um método a um tipo de parâmetro `Type1` e um tipo de retorno `Type3` a um representante genérico com um tipo de parâmetro `Type2` e um tipo de retorno `Type2`. O delegado genérico resultante é então atribuído a outra variável cujo tipo de delegado genérico possui um parâmetro de tipo `Type3` e tipo de retorno `Type1`, usando a covariância e a contravariância de parâmetros de tipo genéricos. A segunda atribuição requer que o tipo de variável e o tipo de delegado sejam construídos a partir da mesma definição de tipo genérico, nesse caso, <xref:System.Func%602>.  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  
  
 [Voltar ao início](#top)  
  
<a name="DefiningVariantTypeParameters"></a>   
## <a name="defining-variant-generic-interfaces-and-delegates"></a>Definindo interfaces e delegados genéricos variantes  
 A partir do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], o Visual Basic e o C# possuem palavras-chave que permitem marcar os parâmetros de tipo genéricos de interfaces e delegados como covariantes ou contravariantes.  
  
> [!NOTE]
>  A partir do .NET Framework 2.0, o Common Language Runtime oferece suporte a anotações de variância em parâmetros de tipo genéricos. Antes do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], a única maneira de definir uma classe genérica que tenha essas anotações é usar o Microsoft intermediate language (MSIL), ao compilar a classe com [Ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) ou pelo emissor-lo em um dinâmico assembly.  
  
 Um parâmetro de tipo covariant é marcado com o `out` palavra-chave (`Out` palavra-chave no Visual Basic, `+` para o [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Você pode usar um parâmetro de tipo covariante como o valor de retorno de um método que pertence a uma interface ou como o tipo de retorno de um delegado. Você não pode usar um parâmetro de tipo covariante como uma restrição de tipo genérico para métodos de interface.  
  
> [!NOTE]
>  Se um método de uma interface tem um parâmetro que é um tipo de delegado genérico, um parâmetro de tipo covariante do tipo da interface pode ser usado para especificar um parâmetro de tipo contravariante do tipo delegado.  
  
 Um parâmetro de tipo contravariant está marcado com o `in` palavra-chave (`In` palavra-chave no Visual Basic, `-` para o [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Você pode usar um parâmetro de tipo contravariante como o tipo de um parâmetro de um método que pertence a uma interface ou como o tipo de um parâmetro de um delegado. Você pode usar um parâmetro de tipo contravariante como uma restrição de tipo genérico para um método de interface.  
  
 Somente tipos de interfaces e tipos de delegados podem ter parâmetros de tipo variantes. Um tipo de delegado ou interface pode ter parâmetros de tipo covariantes e contravariantes.  
  
 O Visual Basic e o C# e não permitem que você viole as regras de uso de parâmetros de tipo covariantes e contravariantes nem adicionar anotações de covariância e de contravariância aos parâmetros de tipo de tipos que não sejam interfaces e delegados. O [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md) não executar essas verificações, mas um <xref:System.TypeLoadException> é gerada se você tentar carregar um tipo que viola as regras.  
  
 Para obter informações e exemplo de código, consulte [variação em Interfaces genéricas](http://msdn.microsoft.com/library/e14322da-1db3-42f2-9a67-397daddd6b6a).  
  
 [Voltar ao início](#top)  
  
<a name="VariantList"></a>   
## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Lista de tipos de interfaces e delegados genéricos variantes  
 No [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], os seguintes tipos de interface e delegados possuem parâmetros de tipo covariantes e/ou contravariantes.  
  
|Tipo|Parâmetros de tipo covariantes|Parâmetros de tipo contravariantes|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%601>Para<xref:System.Action%6016>||Sim|  
|<xref:System.Comparison%601>||Sim|  
|<xref:System.Converter%602>|Sim|Sim|  
|<xref:System.Func%601>|Sim||  
|<xref:System.Func%602>Para<xref:System.Func%6017>|Sim|Sim|  
|<xref:System.IComparable%601>||Sim|  
|<xref:System.Predicate%601>||Sim|  
|<xref:System.Collections.Generic.IComparer%601>||Sim|  
|<xref:System.Collections.Generic.IEnumerable%601>|Sim||  
|<xref:System.Collections.Generic.IEnumerator%601>|Sim||  
|<xref:System.Collections.Generic.IEqualityComparer%601>||Sim|  
|<xref:System.Linq.IGrouping%602>|Sim||  
|<xref:System.Linq.IOrderedEnumerable%601>|Sim||  
|<xref:System.Linq.IOrderedQueryable%601>|Sim||  
|<xref:System.Linq.IQueryable%601>|Sim||  
  
## <a name="see-also"></a>Consulte também  
 [Covariância e contravariância (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)  
 [Covariância e contravariância (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)    
 [Variação em Delegações](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)
