---
title: Reflexão no .NET Framework para aplicativos da Windows Store
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection, Windows Store apps
- .NET for Windows Store apps, TypeInfo class
ms.assetid: 0d07090c-9b47-4ecc-81d1-29d539603c9b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9aaec282fda0a038d14f3a0cd57e1a8a2855f2ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448138"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Reflexão no .NET Framework para aplicativos da Windows Store

Starting with the .NET Framework 4.5, the .NET Framework includes a set of reflection types and members for use in Windows 8.x Store apps. These types and members are available in the full .NET Framework as well as in the .NET for Windows Store apps. Este documento explica as principais diferenças entre eles e seus equivalentes no .NET Framework 4 e em versões anteriores.  
  
 If you are creating a Windows 8.x Store app, you must use the reflection types and members in the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Esses membros e tipos também estão disponíveis, mas não são obrigatórios, para uso em aplicativos da área de trabalho, portanto você pode usar o mesmo código para os dois tipos de aplicativos.  
  
## <a name="typeinfo-and-assembly-loading"></a>TypeInfo e Carregamento do Assembly  
 No [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], a classe <xref:System.Reflection.TypeInfo> contém algumas das funcionalidades da classe <xref:System.Type> do .NET Framework 4. Um objeto <xref:System.Type> representa uma referência a uma definição de tipo, enquanto um objeto <xref:System.Reflection.TypeInfo> representa a definição de tipo em si. Isso permite que você manipule objetos <xref:System.Type> sem necessariamente exigir que o runtime carregue o assembly que eles referenciam. Obter o objeto <xref:System.Reflection.TypeInfo> associado força o assembly a ser carregado.  
  
 <xref:System.Reflection.TypeInfo> contém muitos dos membros disponíveis em <xref:System.Type> e muitas das propriedades de reflexão no [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] retornam coleções de objetos <xref:System.Reflection.TypeInfo>. Para obter um objeto <xref:System.Reflection.TypeInfo> de um objeto <xref:System.Type>, use o método <xref:System.Reflection.IReflectableType.GetTypeInfo%2A>.  
  
## <a name="query-methods"></a>Métodos de consulta  
 No [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], use as propriedades de reflexão que retornam coleções <xref:System.Collections.Generic.IEnumerable%601> em vez de métodos que retornam matrizes. Os contextos de reflexão podem implementar passagens lentas dessas coleções para grandes tipos ou assemblies.  
  
 As propriedades de reflexão retornam apenas os métodos declarados em um objeto específico em vez de percorrer a árvore de herança. Além disso, elas não usam parâmetros <xref:System.Reflection.BindingFlags> para filtragem. Em vez disso, a filtragem ocorre no código do usuário, usando consultas LINQ nas coleções retornadas. Para objetos de reflexão que se originam com o runtime (por exemplo, como resultado de `typeof(Object)`), a passagem pela árvore de herança é melhor realizada usando os métodos auxiliares da classe <xref:System.Reflection.RuntimeReflectionExtensions>. Os consumidores de objetos de contextos de reflexão personalizados não podem usar esses métodos e devem percorrer a árvore de herança sozinhos.  
  
## <a name="restrictions"></a>Restrições  
 In a Windows 8.x Store app, access to some .NET Framework types and members is restricted. Por exemplo, você não pode chamar os métodos do .NET Framework que não estão incluídos no [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], usando um objeto <xref:System.Reflection.MethodInfo>. In addition, certain types and members that are not considered safe within the context of a Windows 8.x Store app are blocked, as are <xref:System.Runtime.InteropServices.Marshal> and <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> members. Essa restrição afeta apenas os tipos e membros do .NET Framework. Você pode chamar seu código ou o código de terceiros como faria normalmente.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa os tipos e membros de reflexão no [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] para recuperar os métodos e propriedades do tipo <xref:System.Globalization.Calendar>, incluindo os métodos e propriedades herdados. To run this code, paste it into the code file for a Windows 8.x Store page that contains a <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> control named `textblock1` in a project named Reflection. Se você colar esse código dentro de um projeto com um nome diferente, certifique-se de alterar o nome do namespace para corresponder ao seu projeto.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Reflexão](reflection.md)
