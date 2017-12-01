---
title: "Recuperando informações armazenadas em atributos"
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
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d3fd9a5a49d65b37d2cdb5107e9c516a6df5847
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-information-stored-in-attributes"></a>Recuperando informações armazenadas em atributos
Recuperar um atributo personalizado é um processo simple. Primeiro, declare uma instância do atributo que você deseja recuperar. Em seguida, use o <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> método para inicializar o novo atributo para o valor do atributo que você deseja recuperar. Depois que o novo atributo é inicializado, você simplesmente usar suas propriedades para obter os valores.  
  
> [!IMPORTANT]
>  Este tópico descreve como recuperar os atributos de código carregados no contexto de execução. Para recuperar os atributos de código carregados no contexto exclusivo de reflexão, você deve usar o <xref:System.Reflection.CustomAttributeData> classe, conforme mostrado no [como: carregar Assemblies no contexto de only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
 Esta seção descreve as seguintes maneiras de recuperar os atributos:  
  
-   [Recuperando uma única instância de um atributo](#cpconretrievingsingleinstanceofattribute)  
  
-   [Recuperando várias instâncias de um atributo aplicadas ao mesmo escopo](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [Recuperando várias instâncias de um atributo aplicadas a diferentes escopos](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a>Recuperando uma única instância de um atributo  
 No exemplo a seguir, o `DeveloperAttribute` (descrito na seção anterior) é aplicado para o `MainApp` classe no nível de classe. O `GetAttribute` método usa **GetCustomAttribute** para recuperar os valores armazenados em `DeveloperAttribute` no nível de classe antes de exibi-los no console.  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 Este programa exibe o texto a seguir quando executado.  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 Se o atributo não for encontrado, o **GetCustomAttribute** método inicializa `MyAttribute` com um valor nulo. Este exemplo verifica `MyAttribute` para uma instância e notifica o usuário se nenhum atributo for encontrado. Se o `DeveloperAttribute` não foi encontrado no escopo de classe, a seguinte mensagem será exibida no console.  
  
```  
The attribute was not found.   
```  
  
 Este exemplo supõe que a definição de atributo está no namespace atual. Lembre-se de importar o namespace no qual a definição do atributo reside se ele não está no namespace atual.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>Recuperando várias instâncias de um atributo aplicadas ao mesmo escopo  
 No exemplo anterior, a classe para inspecionar e o atributo específico para localizar são passados para <xref:System.Attribute.GetCustomAttribute%2A>. Esse código funciona bem se apenas uma instância de um atributo é aplicada no nível de classe. No entanto, se várias instâncias de um atributo forem aplicadas no mesmo nível de classe, o **GetCustomAttribute** método não recupera todas as informações. Em casos onde várias instâncias do mesmo atributo são aplicadas ao mesmo escopo, você pode usar <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> para colocar todas as instâncias de um atributo em uma matriz. Por exemplo, se duas instâncias do `DeveloperAttribute` são aplicadas no nível de classe da mesma classe, o `GetAttribute` método pode ser modificado para exibir as informações encontradas em ambos os atributos. Lembre-se de que, para aplicar vários atributos no mesmo nível, o atributo deve ser definido com o **AllowMultiple** propriedade definida como **true** no <xref:System.AttributeUsageAttribute>.  
  
 O exemplo de código a seguir mostra como usar o **GetCustomAttributes** método para criar uma matriz que faz referência a todas as instâncias de `DeveloperAttribute` em qualquer determinada classe. Os valores de todos os atributos são exibidos no console.  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 Se nenhum atributo for localizado, esse código alerta o usuário. Caso contrário, as informações contidas em ambas as instâncias de `DeveloperAttribute` é exibido.  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>Recuperando várias instâncias de um atributo aplicadas a diferentes escopos  
 O <xref:System.Attribute.GetCustomAttributes%2A> e <xref:System.Attribute.GetCustomAttribute%2A> métodos não pesquisam uma classe inteira e retornam todas as instâncias de um atributo na classe. Em vez disso, eles pesquisam somente um método especificado ou membro por vez. Se você tiver uma classe com o mesmo atributo aplicado a cada membro e você deseja recuperar os valores em todos os atributos aplicados a esses membros, você deve fornecer cada método ou membro individualmente para **GetCustomAttributes** e  **GetCustomAttribute**.  
  
 O exemplo de código a seguir usa uma classe como um parâmetro e procura o `DeveloperAttribute` (definida anteriormente) no nível de classe e em cada método individual de classe.  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 Se nenhuma instância do `DeveloperAttribute` são encontradas no nível de método ou nível de classe, o `GetAttribute` método notifica o usuário que nenhum atributo foi encontrado e exibe o nome do método ou classe que contém o atributo. Se um atributo for encontrado, o `Name`, `Level`, e `Reviewed` campos são exibidos no console.  
  
 Você pode usar os membros de <xref:System.Type> classe para obter os métodos e membros individuais na classe passada. Este exemplo primeiro consulta o **tipo** objeto para obter informações de atributo para o nível de classe. Em seguida, ele usa <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> para colocar instâncias de todos os métodos em uma matriz de <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objetos para recuperar informações de atributo para o nível de método. Você também pode usar o <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> método para verificar os atributos no nível de propriedade ou <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> para verificar os atributos no nível do construtor.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [Atributos](../../../docs/standard/attributes/index.md)
