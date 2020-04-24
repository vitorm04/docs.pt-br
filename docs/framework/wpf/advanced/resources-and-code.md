---
title: Recursos e código
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys [WPF], using objects as
- resources [WPF], accessing from procedural code
- procedural code [WPF], creating resources with
- procedural code [WPF], accessing resources from
- resources [WPF], creating with procedural code
ms.assetid: c1cfcddb-e39c-41c8-a7f3-60984914dfae
ms.openlocfilehash: 8074562ddb865b482cf123743796ac68bb529f85
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646239"
---
# <a name="resources-and-code"></a>Recursos e código
Esta visão geral se concentra em como recursos de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] podem ser acessados ou criados usando o código em vez da sintaxe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Para obter mais informações sobre o uso geral de recursos e sobre os recursos da perspectiva da sintaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consulte [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  

<a name="accessing"></a>
## <a name="accessing-resources-from-code"></a>Acessando recursos do código  
 As chaves que identificam os recursos se eles forem definidos pelo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] também serão usadas para recuperar recursos específicos se você solicitá-los no código. A maneira mais simples de recuperar um recurso <xref:System.Windows.FrameworkElement.FindResource%2A> do <xref:System.Windows.FrameworkElement.TryFindResource%2A> código é chamar o método ou o método de objetos de nível de estrutura em sua aplicação. A diferença comportamental entre esses métodos é o que acontece caso a chave solicitada não seja encontrada. <xref:System.Windows.FrameworkElement.FindResource%2A>levanta uma exceção; <xref:System.Windows.FrameworkElement.TryFindResource%2A> não levantará uma `null`exceção, mas retorna. Cada método usa a chave do recurso como um parâmetro de entrada e retorna um objeto que não é fortemente tipado. Normalmente, uma chave de recurso é uma cadeia de caracteres, mas há usos ocasionais em que esse não é o caso. Consulte a seção [Usando objetos como chaves](#objectaskey) para obter detalhes. Normalmente, você converteria o objeto retornado para o tipo exigido pela propriedade que você está definindo ao solicitar o recurso. A lógica de pesquisa para resolução de recurso do código é a mesma que no caso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] da referência de recurso dinâmico. A pesquisa por recursos é iniciada do elemento de chamada e continua para os elementos pai sucessivos na árvore lógica. A pesquisa segue adiante para os recursos de aplicativo, temas e recursos de sistema, se necessário. Uma solicitação de código para um recurso considerará as alterações em runtime nos dicionários de recursos que podem ter sido feitos após o dicionário de recursos ter sido carregado do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], e também alterações de recursos de sistema em tempo real.  
  
 A seguir, um breve exemplo de código que encontra um recurso por chave <xref:System.Windows.Controls.Primitives.ButtonBase.Click> e usa o valor retornado para definir uma propriedade, implementada como manipuladora de eventos.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Um método alternativo para atribuir <xref:System.Windows.FrameworkElement.SetResourceReference%2A>uma referência de recursos é . Este método utiliza dois parâmetros: a chave do recurso e o identificador de uma determinada propriedade de dependência que está presente na instância do elemento a que o valor do recurso deve ser atribuído. Funcionalmente, esse método é igual e tem a vantagem de não exigir nenhuma conversão de valores retornados.  
  
 Outra forma de acessar recursos de forma programática <xref:System.Windows.FrameworkElement.Resources%2A> é acessar o conteúdo da propriedade como dicionário. Acessando o dicionário contido por esta propriedade, você também pode adicionar novos recursos a coleções existentes, verificar se um nome de chave já existe na coleção e outras operações de dicionário/coleção. Se você estiver [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] escrevendo um aplicativo inteiramente em código, você também pode criar toda a coleção em <xref:System.Windows.FrameworkElement.Resources%2A> código, atribuir chaves a ele e, em seguida, atribuir a coleção finalizada à propriedade de um elemento estabelecido. Isso será descrito na próxima seção.  
  
 Você pode indexar <xref:System.Windows.FrameworkElement.Resources%2A> dentro de qualquer coleção, usando uma chave específica como índice, mas você deve estar ciente de que acessar o recurso dessa forma não segue as regras normais de tempo de execução da resolução de recursos. Você está acessando apenas aquela coleção em particular. A pesquisa de recursos não percorrerá o escopo até a raiz ou o aplicativo se nenhum objeto válido tiver sido encontrado na chave solicitada. No entanto, essa abordagem pode ter vantagens de desempenho em alguns casos, precisamente porque o escopo da pesquisa no caso da chave é mais restrito. Consulte <xref:System.Windows.ResourceDictionary> a classe para obter mais detalhes sobre como trabalhar diretamente com o dicionário de recursos.  
  
<a name="creating"></a>
## <a name="creating-resources-with-code"></a>Criando recursos com código  
 Se quiser criar um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inteiro em código, você também poderá querer criar todos os recursos do aplicativo em código. Para isso, crie <xref:System.Windows.ResourceDictionary> uma nova instância e adicione todos os recursos <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>ao dicionário usando chamadas sucessivas para . Em seguida, <xref:System.Windows.ResourceDictionary> use o assim <xref:System.Windows.FrameworkElement.Resources%2A> criado para definir a propriedade em um <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>elemento que está presente em um escopo de página, ou o . Você também pode <xref:System.Windows.ResourceDictionary> manter o objeto autônomo sem adicioná-lo a um elemento. No entanto, se fizer isso, você precisará acessar os recursos dentro pela chave do item, como se ele fosse um dicionário genérico. Um <xref:System.Windows.ResourceDictionary> que não esteja ligado `Resources` a uma propriedade de elemento não existiria como parte da árvore <xref:System.Windows.FrameworkElement.FindResource%2A> de elementos e não tem escopo em uma seqüência de pesquisas que pode ser usada por métodos relacionados.  
  
<a name="objectaskey"></a>
## <a name="using-objects-as-keys"></a>Usando objetos como chaves  
 A maioria dos usos do recurso definirá a chave de recurso como uma cadeia de caracteres. No entanto, vários recursos de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] deliberadamente não usam um tipo de cadeia de caracteres para especificar chaves, em vez disso, este parâmetro é um objeto. A capacidade de ter recursos cujas chaves são objetos é usada pelo suporte a estilos e temas de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Os estilos em temas que se tornam o estilo padrão para um <xref:System.Type> controle não-estilizado são cada um com chave pelo controle ao qual devem ser aplicados. Ter como chave um tipo fornece um mecanismo de pesquisa confiável que funciona em instâncias padrão de cada tipo de controle, e o tipo pode ser detectado por reflexão e usado para estilizar classes derivadas mesmo que o tipo derivado não tenha nenhum estilo padrão. Você pode <xref:System.Type> especificar uma chave [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para um recurso definido usando a [extensão x:Tipo Marcação](../../../desktop-wpf/xaml-services/xtype-markup-extension.md). Extensões semelhantes existem para outros usos de chave diferentes de cadeias de caracteres que dão suporte a recursos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], como a [Extensão de marcação ComponentResourceKey](componentresourcekey-markup-extension.md).  
  
## <a name="see-also"></a>Confira também

- [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
