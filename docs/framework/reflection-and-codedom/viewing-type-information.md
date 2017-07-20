---
title: "Exibindo informações de tipo | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- types, viewing type information
- Type object
- viewing type information
- reflection, viewing type information
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5bc5ed1dd10f04a2d5ef5b00127b6d858102e933
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="viewing-type-information"></a>Exibindo informações de tipo
A classe <xref:System.Type?displayProperty=fullName> é fundamental para reflexão. O Common Language Runtime cria o **Type** para um tipo carregado quando a reflexão solicitá-lo. Você pode usar os métodos, campos, propriedades e classes aninhadas de um objeto **Tipo** para descobrir tudo sobre o tipo do objeto.  
  
 Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName> ou <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> para obter objetos **Tipo** de assemblies que não foram carregados, passando o nome do tipo ou tipos que você deseja. Use <xref:System.Type.GetType%2A?displayProperty=fullName> para obter objetos **Tipo** de um assembly que já foi carregado. Use <xref:System.Reflection.Module.GetType%2A?displayProperty=fullName> e <xref:System.Reflection.Module.GetTypes%2A?displayProperty=fullName> para obter objetos **Type** do módulo.  
  
> [!NOTE]
>  Se você quiser examinar e manipular tipos genéricos e métodos, consulte as informações adicionais fornecidas na [Reflexão e tipos genéricos](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md) e [Como examinar e instanciar tipos genéricos com reflexão](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 O exemplo a seguir mostra a sintaxe necessária obter o objeto <xref:System.Reflection.Assembly> e o módulo para um assembly.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)] [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)] [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 O exemplo a seguir demonstra como obter objetos de **Tipo** de um assembly carregado.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)] [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)] [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 Depois de obter um **Tipo**, há várias maneiras de descobrir informações sobre os membros desse tipo. Por exemplo, você pode descobrir sobre todos os membros do tipo chamando o método <xref:System.Type.GetMembers%2A?displayProperty=fullName>, que obtém uma matriz de objetos <xref:System.Reflection.MemberInfo> que descrevem cada um dos membros do tipo atual.  
  
 Você também pode usar métodos na classe **Tipo** para recuperar informações sobre um ou mais construtores, métodos, eventos, campos ou propriedades que você especifica por nome. Por exemplo, <xref:System.Type.GetConstructor%2A?displayProperty=fullName> encapsula um construtor específico da classe atual.  
  
 Se você tiver um **Tipo**, poderá usar a propriedade <xref:System.Type.Module%2A?displayProperty=fullName> para obter um objeto que encapsula o módulo que contém esse tipo. Use a propriedade <xref:System.Reflection.Module.Assembly%2A?displayProperty=fullName> para localizar um objeto que encapsula o assembly que contém o módulo. Você pode obter o assembly que encapsula o tipo diretamente usando a propriedade <xref:System.Type.Assembly%2A?displayProperty=fullName>.  
  
## <a name="systemtype-and-constructorinfo"></a>System.Type e ConstructorInfo  
 O exemplo a seguir mostra como listar os construtores de uma classe, nesse caso, a classe <xref:System.String>.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)] [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)] [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a>MemberInfo, MethodInfo, FieldInfo e PropertyInfo  
 Obtenha informações sobre métodos, propriedades, eventos e campos do tipo usando os objetos <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo> ou <xref:System.Reflection.PropertyInfo>.  
  
 O exemplo a seguir usa **MemberInfo** para listar o número de membros na classe **System.IO.File** e usa a propriedade <xref:System.Type.IsPublic%2A> para determinar a visibilidade da classe.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)] [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)] [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 O exemplo a seguir examina o tipo do membro especificado. Ele executa reflexão em um membro da classe **MemberInfo** e lista seu tipo.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)] [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)] [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 O exemplo a seguir usa todas as classes Reflection **\*Info** junto com <xref:System.Reflection.BindingFlags> para listar todos os membros (construtores, campos, propriedades, eventos e métodos) da classe especificada, dividindo os membros em categorias de instância e estáticos.  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)] [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)] [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.BindingFlags>   
 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName>   
 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName>   
 <xref:System.Type.GetType%2A?displayProperty=fullName>   
 <xref:System.Type.GetMembers%2A?displayProperty=fullName>   
 <xref:System.Type.GetFields%2A?displayProperty=fullName>   
 <xref:System.Reflection.Module.GetType%2A?displayProperty=fullName>   
 <xref:System.Reflection.Module.GetTypes%2A?displayProperty=fullName>   
 <xref:System.Reflection.MemberInfo>   
 <xref:System.Reflection.ConstructorInfo>   
 <xref:System.Reflection.MethodInfo>   
 <xref:System.Reflection.FieldInfo>   
 <xref:System.Reflection.EventInfo>   
 <xref:System.Reflection.ParameterInfo>   
 [Reflexão e tipos genéricos](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
