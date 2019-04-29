---
title: 'Como: Personalizar dados de associação de comportamentos (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: f55c9790b8300a1a3f26e031a17a0982638b562b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765512"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Como: Personalizar dados de associação de comportamentos (WCF Data Services)
Com o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você pode fornecer lógica personalizada que é chamada pelo <xref:System.Data.Services.Client.DataServiceCollection%601> quando um objeto é adicionado ou removido da coleção de associação ou quando for detectada uma alteração de propriedade. Essa lógica personalizada é fornecida como métodos, referenciados como <xref:System.Func%602> delegados, que retornam um valor de `false` quando o comportamento padrão deve ainda ser executado quando o método personalizado é concluído e `true` quando subsequentes de processamento da evento deve ser interrompido.  
  
 Os exemplos neste tópico fornecem métodos personalizados para ambos os `entityChanged` e `entityCollectionChanged` parâmetros de <xref:System.Data.Services.Client.DataServiceCollection%601>. Os exemplos neste tópico usam o serviço de dados de exemplo Northwind e dados de cliente gerado automaticamente classes de serviço. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [início rápido do WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 A seguinte página code-behind para o arquivo XAML cria um <xref:System.Data.Services.Client.DataServiceCollection%601> com métodos personalizados que são chamados quando ocorrem alterações nos dados que estão associados à coleção de associação. Quando o <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> evento ocorrer, o método fornecido impede que um item que foi removido da coleção de associação que está sendo excluído do serviço de dados. Quando o <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> evento ocorrer, o `ShipDate` valor é validado para garantir que não são feitas alterações em pedidos que já foram enviados.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Exemplo  
 O XAML a seguir define a janela para o exemplo anterior.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
