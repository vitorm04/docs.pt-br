---
title: Usando a Biblioteca de Classes Portátil com Modelo MVVM
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d2f07e471d4f0173f768b0d2a463d756b5be0682
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071007"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a>Usando a Biblioteca de Classes Portátil com Modelo MVVM
Você pode usar o .NET Framework [biblioteca de classes portátil](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) para implementar o padrão Model-View-View modelo (MVVM) e compartilhar assemblies entre várias plataformas.  

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM é um padrão de aplicativo que isola a interface do usuário da lógica de negócios subjacentes. Você pode implementar as classes de modelo do modelo e exibição em um [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]e, em seguida, criar exibições personalizadas para diferentes plataformas. Essa abordagem permite que você grave os dados de modelo e a lógica de negócios apenas uma vez e usá-la de código do .NET Framework, Silverlight, Windows Phone, e [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos, conforme mostrado na ilustração a seguir.  
  
 ![Portátil com o diagrama MVVM](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")  
  
 Este tópico fornece informações gerais sobre o padrão MVVM. Ele só fornece informações sobre como usar [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] para implementar o MVVM. Para obter mais informações sobre o MVVM, consulte o [início rápido do MVVM](https://msdn.microsoft.com/library/gg430869(v=PandP.40).aspx).  
  
## <a name="classes-that-support-mvvm"></a>Classes que dão suporte ao MVVM  
 Quando você seleciona os [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight ou Windows Phone 7.5 para o seu [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projeto, as classes a seguir estão disponíveis para implementar o padrão MVVM:  
  
-   Classe <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>  
  
-   Classe <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>  
  
-   Classe <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType>  
  
-   Classe <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType>  
  
-   Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType>  
  
-   Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType>  
  
-   Classe <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType>  
  
-   Classe <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType>  
  
-   Classe <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType>  
  
-   Classe <xref:System.Windows.Input.ICommand?displayProperty=nameWithType>  
  
-   Todas as classes no <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace  
  
## <a name="implementing-mvvm"></a>Implementação do MVVM  
 Para implementar o MVVM, você normalmente cria o modelo e o modelo de exibição em uma [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projeto, porque um [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projeto não pode fazer referência a um projeto não portátil. O modelo e o modelo de exibição podem ser no mesmo projeto ou em projetos separados. Se você usar projetos separados, adicione uma referência do projeto de modelo de exibição para o projeto de modelo.  
  
 Depois de compilar o modelo e exibir projetos de modelo, você pode referenciar os assemblies no aplicativo que contém a exibição. Se o modo de exibição interage apenas com o modelo de exibição, você só precisará fazer referência ao assembly que contém o modelo de exibição.  
  
### <a name="model"></a>Modelo  
 O exemplo a seguir mostra uma classe de modelo simplificado que pode residir em um [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projeto.  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 O exemplo a seguir mostra uma maneira simples de popular, recuperar e atualizar os dados em um [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projeto. Em um aplicativo real, você recuperaria os dados de uma fonte, como um serviço do Windows Communication Foundation (WCF).  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### <a name="view-model"></a>Modelo de exibição  
 Uma classe base para modelos de exibição com frequência é adicionada ao implementar o padrão MVVM. O exemplo a seguir mostra uma classe base.  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 Uma implementação do <xref:System.Windows.Input.ICommand> interface é frequentemente usada com o padrão MVVM. O exemplo a seguir mostra uma implementação do <xref:System.Windows.Input.ICommand> interface.  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 O exemplo a seguir mostra um modelo de exibição simplificada.  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>Exibir  
 De um [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aplicativo, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo, o aplicativo com base no Silverlight ou o aplicativo de Windows Phone 7.5, você pode referenciar o assembly que contém os projetos de modelo do modelo e exibição.  Você, em seguida, crie uma exibição que interage com o modelo de exibição. O exemplo a seguir mostra um aplicativo Windows Presentation Foundation (WPF) simplificada que recupera e atualiza os dados do modelo de exibição. Você pode criar modos de exibição semelhantes no Silverlight, Windows Phone, ou [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>Consulte também

- [Biblioteca de classes portátil](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
