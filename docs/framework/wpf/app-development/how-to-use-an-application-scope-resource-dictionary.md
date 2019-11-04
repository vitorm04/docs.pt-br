---
title: Como usar um dicionário de recursos de escopo do aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 5bfb3ed0304598a5acf4b7682bf4a4169c5153d1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459803"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Como usar um dicionário de recursos de escopo do aplicativo
Este exemplo mostra como definir e usar um dicionário de recursos personalizado de escopo do aplicativo.  
  
## <a name="example"></a>Exemplo  
 o <xref:System.Windows.Application> expõe um repositório de escopo de aplicativo para recursos compartilhados: <xref:System.Windows.Application.Resources%2A>. Por padrão, a propriedade <xref:System.Windows.Application.Resources%2A> é inicializada com uma instância do tipo <xref:System.Windows.ResourceDictionary>. Você usa essa instância quando Obtém e define as propriedades de escopo do aplicativo usando <xref:System.Windows.Application.Resources%2A>. Para obter mais informações, consulte [como: obter e definir um recurso de escopo de aplicativo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).
  
 Se você tiver vários recursos que você definiu usando <xref:System.Windows.Application.Resources%2A>, poderá usar um dicionário de recursos personalizados para armazenar esses recursos e definir <xref:System.Windows.Application.Resources%2A> com ele. O seguinte mostra como você declara um dicionário de recursos personalizados usando XAML.
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 A troca de dicionários de recursos inteiros usando o <xref:System.Windows.Application.Resources%2A> permite que você ofereça suporte a temas de escopo de aplicativo, onde cada tema é encapsulado por um único dicionário de recursos. O exemplo a seguir mostra como definir o <xref:System.Windows.ResourceDictionary>.  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 O seguinte mostra como você pode obter recursos de escopo de aplicativo do dicionário de recursos exposto por <xref:System.Windows.Application.Resources%2A> em XAML.  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 O exemplo seguinte mostra como é possível também obter os recursos em código.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Há duas considerações a serem feitas ao usar <xref:System.Windows.Application.Resources%2A>. Primeiro, a *chave* de dicionário é um objeto, portanto, você deve usar exatamente a mesma instância de objeto quando ambas estiverem Configurando e obtendo um valor de propriedade. (Observe que a chave diferencia maiúsculas de minúsculas ao usar uma cadeia de caracteres.) Em segundo lugar, o *valor* Dictionary é um objeto, portanto, você precisará converter o valor para o tipo desejado ao obter um valor de propriedade.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Dicionários de recursos mesclados](../advanced/merged-resource-dictionaries.md)
