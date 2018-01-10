---
title: "Usando a Biblioteca de Classes Portátil com Modelo MVVM"
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
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cc12a90025a1862fc6c588fe4425f3f8341da313
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="using-portable-class-library-with-model-view-view-model"></a>Usando a Biblioteca de Classes Portátil com Modelo MVVM
Você pode usar o .NET Framework [biblioteca de classes portátil](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) para implementar o padrão do modo de exibição de modelo modelo MVVM () e compartilhar assemblies em várias plataformas.  
  
 MVVM é um padrão de aplicativo que isola a interface do usuário da lógica de negócios subjacente. Você pode implementar classes de modelo do modelo e o modo de exibição em uma [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]e, em seguida, criar modos de exibição personalizados para diferentes plataformas. Essa abordagem permite que você grave os dados de modelo e lógica de negócios apenas uma vez e usar esse código do .NET Framework, Silverlight, Windows Phone, e [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos, conforme mostrado na ilustração a seguir.  
  
 ![Portátil com diagrama MVVM](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")  
  
 Este tópico fornece informações gerais sobre o padrão MVVM. Ele só fornece informações sobre como usar [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] para implementar MVVM. Para obter mais informações sobre MVVM, consulte o [MVVM Quickstart](https://msdn.microsoft.com/library/gg430869(v=PandP.40).aspx).  
  
## <a name="classes-that-support-mvvm"></a>Classes que oferecem suporte MVVM  
 Quando você seleciona o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight ou Windows Phone 7.5 para seu [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projeto, as classes a seguir estão disponíveis para implementar o padrão MVVM:  
  
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
  
-   Todas as classes de <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace  
  
## <a name="implementing-mvvm"></a>Implementando MVVM  
 Para implementar MVVM, você normalmente cria o modelo e o modelo de exibição em uma [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projeto, porque um [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projeto não pode fazer referência a um projeto não portátil. O modelo e o modelo de exibição podem ser no mesmo projeto ou em projetos separados. Se você usar projetos separados, adicione uma referência do projeto do modelo de exibição para o projeto de modelo.  
  
 Depois de compilar o modelo e exibir projetos de modelo, você pode referenciar os assemblies no aplicativo que contém a exibição. Se o modo de exibição interage somente com o modelo de exibição, você só precisa fazer referência ao assembly que contém o modelo de exibição.  
  
### <a name="model"></a>Modelo  
 O exemplo a seguir mostra uma classe de modelo simplificado que pode residir em um [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projeto.  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 O exemplo a seguir mostra uma maneira simple de popular, recuperar e atualizar os dados em um [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projeto. Em um aplicativo real, você deve recuperar os dados de uma fonte, como um serviço do Windows Communication Foundation (WCF).  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### <a name="view-model"></a>Modelo de exibição  
 Uma classe base para exibir modelos com frequência é adicionada ao implementar o padrão MVVM. O exemplo a seguir mostra uma classe base.  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 Uma implementação de <xref:System.Windows.Input.ICommand> interface é frequentemente usada com o padrão MVVM. O exemplo a seguir mostra uma implementação do <xref:System.Windows.Input.ICommand> interface.  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 O exemplo a seguir mostra um modelo de exibição simplificada.  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>Exibir  
 De um [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aplicativo, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] um aplicativo, com base no Silverlight ou aplicativo do Windows Phone 7.5, você pode referenciar o assembly que contém os projetos de modelo do modelo e o modo de exibição.  Você criar uma exibição que interage com o modelo de exibição. O exemplo a seguir mostra um aplicativo do Windows Presentation Foundation (WPF) simplificado que recupera e atualiza os dados do modelo de exibição. Você pode criar modos de exibição semelhantes no Silverlight, Windows Phone, ou [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>Consulte também  
 [Biblioteca de classes portátil](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
