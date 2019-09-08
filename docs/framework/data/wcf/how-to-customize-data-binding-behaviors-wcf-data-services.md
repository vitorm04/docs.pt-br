---
title: 'Como: Personalizar comportamentos de vinculação de dados (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: c878096cba7d31e0b48727213ee1bb8239b8f690
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790757"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Como: Personalizar comportamentos de vinculação de dados (WCF Data Services)
Com [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] o<xref:System.Data.Services.Client.DataServiceCollection%601> , você pode fornecer uma lógica personalizada que é chamada pelo quando um objeto é adicionado ou removido da coleção de associação ou quando uma alteração de propriedade é detectada. Essa lógica personalizada é fornecida como métodos, referenciados <xref:System.Func%602> como delegados, que retornam um `false` valor de quando o comportamento padrão ainda deve ser executado quando o método personalizado é `true` concluído e quando o processamento subsequente do o evento deve ser interrompido.  
  
 Os exemplos neste tópico fornecem métodos personalizados para os `entityChanged` parâmetros e `entityCollectionChanged` de <xref:System.Data.Services.Client.DataServiceCollection%601>. Os exemplos neste tópico usam o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 A seguinte página code-behind do arquivo XAML cria um <xref:System.Data.Services.Client.DataServiceCollection%601> com métodos personalizados que são chamados quando ocorrem alterações nos dados associados à coleção de associação. Quando o <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> evento ocorre, o método fornecido impede que um item que foi removido da coleção de associação seja excluído do serviço de dados. Quando o <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> evento ocorre, o `ShipDate` valor é validado para garantir que as alterações não sejam feitas em pedidos que já foram enviados.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Exemplo  
 O XAML a seguir define a janela para o exemplo anterior.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
