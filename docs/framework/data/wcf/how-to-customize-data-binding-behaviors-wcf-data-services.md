---
title: "Como: personalizar dados de associação comportamentos (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9aa93e5c0971d1af1f1962bfe4f61a0f56f66b9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Como: personalizar dados de associação comportamentos (WCF Data Services)
Com [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você pode fornecer lógica personalizada que é chamada pelo <xref:System.Data.Services.Client.DataServiceCollection%601> quando um objeto é adicionado ou removido da coleção de associação ou quando for detectada uma alteração de propriedade. Essa lógica personalizada é fornecida como métodos, referenciados como <xref:System.Func%602> delegados, que retornam um valor de `false` quando o comportamento padrão deve ser executado ainda quando o método personalizado é concluído e `true` quando subsequentes de processamento do evento deve ser interrompido.  
  
 Os exemplos neste tópico fornecem métodos personalizados para ambos os `entityChanged` e `entityCollectionChanged` parâmetros de <xref:System.Data.Services.Client.DataServiceCollection%601>. Os exemplos neste tópico usam o serviço de dados de exemplo Northwind e dados de cliente gerado automaticamente classes de serviço. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 A seguinte página de code-behind para o arquivo XAML cria um <xref:System.Data.Services.Client.DataServiceCollection%601> com métodos personalizados que são chamados quando ocorrem alterações nos dados que são associados a coleção de associação. Quando o <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> evento ocorrer, o método fornecido impede que um item que foi removido da coleção de associação seja excluído do serviço de dados. Quando o <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> evento ocorrer, o `ShipDate` valor é validado para garantir que as alterações não são feitas para pedidos que já tenham sido fornecidos.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Exemplo  
 O XAML a seguir define a janela para o exemplo anterior.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Consulte também  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
