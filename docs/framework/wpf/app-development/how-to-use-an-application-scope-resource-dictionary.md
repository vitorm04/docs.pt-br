---
title: "Como usar um dicionário de recursos de escopo do aplicativo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ece6a5d2123bb118f11940081e3c1d939815a8ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Como usar um dicionário de recursos de escopo do aplicativo
Este exemplo mostra como definir e usar um dicionário de recursos personalizado de escopo do aplicativo.  
  
## <a name="example"></a>Exemplo  
 <xref:System.Windows.Application>expõe um armazenamento de escopo de aplicativo para recursos compartilhados: <xref:System.Windows.Application.Resources%2A>. Por padrão, o <xref:System.Windows.Application.Resources%2A> propriedade é inicializada com uma instância das <xref:System.Windows.ResourceDictionary> tipo. Usar essa instância quando você obter e definir propriedades de escopo de aplicativo usando <xref:System.Windows.Application.Resources%2A>. Para obter mais informações, consulte [como: obter e definir um recurso de escopo de aplicativo](http://msdn.microsoft.com/en-us/39e0420c-c9fc-47dc-8956-fdd95b214095).
  
 Se você tiver vários recursos que você definir usando <xref:System.Windows.Application.Resources%2A>, em vez disso, você pode usar um dicionário de recursos personalizados para armazenar esses recursos e definir <xref:System.Windows.Application.Resources%2A> com ele em vez disso. O exemplo a seguir mostra como declarar um dicionário de recursos personalizados usando XAML.
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 Troca de dicionários de recursos inteiros usando <xref:System.Windows.Application.Resources%2A> permite que você oferecer suporte a temas de escopo do aplicativo, onde cada tema é encapsulado por um dicionário de recurso único. O exemplo a seguir mostra como definir o <xref:System.Windows.ResourceDictionary>.  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 A seguir mostra como você pode obter recursos de escopo de aplicativo do dicionário de recursos expostos pelo <xref:System.Windows.Application.Resources%2A> em XAML.  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 O exemplo seguinte mostra como é possível também obter os recursos em código.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Há duas considerações a fazer ao usar <xref:System.Windows.Application.Resources%2A>. Primeiro, o dicionário *chave* é um objeto, então você deve usar exatamente a mesma instância de objeto quando estiver definindo e obter um valor de propriedade. (Note que a chave faz distinção entre maiúsculas e minúsculas ao usar uma cadeia de caracteres.) Segundo, o dicionário *valor* é um objeto, então você precisará converter o valor para o tipo desejado ao obter um valor de propriedade.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.ResourceDictionary>  
 <xref:System.Windows.Application.Resources%2A>  
 [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Dicionários de recursos mesclados](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
